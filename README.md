# programa-MEN-RESTAURANTE---SISTEMA-DE-PEDIDOS
Nebu de restaurante que toma pedido , aplica descuentos con ciertas condiciones y al final genera una factura mostrando todos los productos seleccionados y el valor total a pagar.
# programa-MEN-RESTAURANTE---SISTEMA-DE-PEDIDOS
Menu de restaurante que toma pedido , aplica descuentos con ciertas condiciones y al final genera una factura mostrando todos los productos seleccionados y el valor total a pagar.
#Nombre Estudiante :Juan sebastian muñoz lopez
#Grupo :FUNDAMENTOS DE PROGRAMACIÓN - (213022A_2201)
# Sistema de venta comidas restaurante con promociones
#codigo fuente :Autoria propia
# =========================================
# MENÚ RESTAURANTE - SISTEMA DE PEDIDOS
# =========================================

# Matriz:
# [Nombre del producto, Categoría, Precio Base]

menu = [
    ["Churrasco 250 gramos", "Carnes", 45000],
    ["Bandeja Paisa", "Plato Tipico", 28000],
    ["Ajiaco Santafereño", "Sopas", 30000],
    ["Empanaditas", "Plato Tipico", 7000],
    ["Tamales tolimense", "Plato Tipico", 23000],
    ["Chocolate con Queso", "Bebidas", 12000]
]

# =========================================
# FUNCIÓN PARA CALCULAR DESCUENTO
# =========================================

def calcular_precio_final(categoria, precio_base):

    categoria_objetivo = "Plato Tipico"
    umbral = 20000

    # Aplicar descuento
    if categoria == categoria_objetivo and precio_base > umbral:

        descuento = precio_base * 0.15
        precio_final = precio_base - descuento

    else:
        precio_final = precio_base

    return precio_final


# =========================================
# VARIABLES
# =========================================

total_pagar = 0
pedido = []

continuar = "si"

# =========================================
# CICLO DE PEDIDOS
# =========================================

while True:
    print("\n========== MENÚ DEL RESTAURANTE ==========")

    for i in range(len(menu)):
        print(f"{i+1}. {menu[i][0]} - ${menu[i][2]}")

    # Selección
    opcion = int(input("\nSeleccione el número del producto que desea pedir: "))

    # Validar opción
    if opcion >= 1 and opcion <= len(menu):
        producto = menu[opcion - 1]

        nombre = producto[0]
        categoria = producto[1]
        precio_base = producto[2]

        # Calcular precio final
        precio_final = calcular_precio_final(categoria, precio_base)

        # Guardar pedido
        pedido.append([nombre, precio_final])

        # Acumular total
        total_pagar += precio_final

        print("\n Producto agregado al pedido")
        print("Producto:", nombre)
        print("Precio : $", precio_base)

        # Mostrar si tuvo descuento
        if precio_final < precio_base:
            print(" Se aplicó promoción del 15%")
            print("Precio Final: $", precio_final)
        else:
            print(" No aplica promoción")
    else:
        print(" Opción inválida")

    # Preguntar si desea continuar
    while True:
        continuar = input("\n¿Desea agregar otro producto? (si/no): ").lower()
        if continuar == "si" or continuar == "no":
            break
        print(" Opción no válida. Escriba solamente 'si' o 'no'.")

    if continuar == "no":
        break

# =========================================
# FACTURA FINAL
# =========================================

print("\n=========== FACTURA FINAL ===========")

for producto in pedido:
    print(f"{producto[0]} ---> ${producto[1]}")

print("\nTOTAL A PAGAR: $", total_pagar)

print("\n Gracias por su compra ")

# =========================================
# FIN DEL PROGRAMA
# =========================================
#Gracias por revisar mi código, cualquier sugerencia es bienvenida para mejorar mi aprendizaje.
