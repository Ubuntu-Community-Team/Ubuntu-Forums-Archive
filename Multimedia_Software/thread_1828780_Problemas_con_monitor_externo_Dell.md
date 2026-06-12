---
title: "Problemas con monitor externo Dell"
date: 2011-08-19
forum: Multimedia Software
---

### Post by dcrosio on 2011-08-19
Buenas, soy nuevo en el foro y nuevo con Linux si bien trabaje durante muchos años con Unix.
Tengo el siguiente problema a ver si alguien me ayuda.
Tengo una Notebook Dell Inspiron N4030 i3 4 Gb de Ram nueva hace 1 mes, en cuanto la recibi de lo primero que me deshice fue de nuestro amigo Mocosoft, saque el Ventana7 con que venia y le instale Ubuntu 11.04 (Naty). Todo funciona a las mil maravillas, la maquina es rapidisima, no hay "pantallas azules" ni esas cosas que suelen suceder son otros SO.
Hace unos dias se me ocurrio conectar a la salida VGA un monitor Dell SP2208WFP. Funcionar funciona, lo detecto como monitor Dell de 20", hasta ahi todo bien, el problema es que es imposible de usar porque la imagen vibra, no se bien como explicarlo, es como si hubiese una fuente externa que inyectara ruido y se mueve la imagen (en Windows funciona perfecto).
Estuve googleando y no encuentro nada, no se que hacer, salvo, no usar el monitor
Les copio algunas salidas de comando que vi que lo piden, por si sirve de algo:

*-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:fac00000-faffffff memory:c0000000-cfffffff ioport:f080(size=8)


Screen 0: minimum 320 x 200, current 3046 x 1050, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1680x1050+1366+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

Desde ya muchas gracias

---

### Post by BicyclerBoy on 2011-08-19
You could have two problems.
video driver & VGA cable connection.

Try DVI cable & see if the problem resolves itself.
Then post your /var/log/Xorg.0.log file (as attachment .txt file)

To get the best performance out of the integrated intel GPU you likely need the xorg-edgers launchpad ppa (later intel driver)

---

### Post by dcrosio on 2011-08-23
Hi,

Thx for your answer. Well change cable and same problem.

The Xorg.0.log is too big for upload in only one file, I am sendig in 4 files

Regards

Daniel

---

### Post by BicyclerBoy on 2011-08-23
Your Xorg.0.log just says VGA1 disconnected.
No indication of anything about DVI.

I have no helpful suggestions other than trying xorg-edgers ppa or messing about with xrandr to force the DVI DFP on.

---

