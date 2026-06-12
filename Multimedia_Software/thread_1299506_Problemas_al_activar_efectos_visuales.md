---
title: "Problemas al activar efectos visuales"
date: 2009-10-24
forum: Multimedia Software
---

### Post by jecymx on 2009-10-24
Antes que nada quiero felicitarles por este sitio, en donde gracias a todos ustedes, como  expertos, nosotros los que apenas empezamos podremos aprender cosas nuevas.... 8)

Instalé Ubuntu 9.04 - Jaunty Jackalope GNOME en mi PC  - Dell Dimension 2400 - Intel Pentium 4 a 2.66Ghz -Ram 2Gb.

Al parecer todo va bien, pero a la hora de querer instalar los efectos visuales "EXTRA", pero me aparece un mensaje que dice "No se han podido activar los efectos de escritorio". He realizado las siguientes pruebas:

$ glxinfo | grep direct

get fences failed: -1
param: 6, val: 0
direct rendering: Yes
----------------------------------------
glxgears (Si me aparece la figura con tre engranes girando)
get fences failed: -1
param: 6, val: 0
1659 frames in 5.0 seconds = 331.663 FPS
2030 frames in 5.0 seconds = 405.887 FPS
2032 frames in 5.0 seconds = 406.365 FPS
1759 frames in 5.0 seconds = 351.722 FPS.........

-----------------------------------------
$ sudo gedit /etc/X11/xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

------------------------------------------------
$ sudo gedit /usr/bin/compiz

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

------------------------------------------------
lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

-------------------------------------------------------------
lshw

pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
---------------------------------------------------------------

Amigos, es todo lo que logre sacar como configuración de mi PC, ojala sea suficiente y me puedan ayudar para poder, darle vida a mi escritorio con el magnifico CUBO.

Gracias:razz:

---

### Post by cotcot on 2009-10-24
Mi español es bastante para entender su problema pero no bastante a contestar. Conseguí una cierta ayuda de un traductor en línea.

La respuesta está en el acoplamiento de la salida que usted da. Su viruta gráficos (ATIRS480) es negro enumerado porque el conductor del ati no es bastante estable para el compiz.

3 soluciones :

- Compre una tarjeta conveniente de los gráficos y póngala en su computadora.

- No utilice el compiz

- Intente el compiz saltando la prueba negra de la lista ```
SKIP_CHECKS=yes compiz-manager
```

---

### Post by jecymx on 2009-10-25
> **cotcot said:**
> Mi español es bastante para entender su problema pero no bastante a contestar. Conseguí una cierta ayuda de un traductor en línea.

La respuesta está en el acoplamiento de la salida que usted da. Su viruta gráficos (ATIRS480) es negro enumerado porque el conductor del ati no es bastante estable para el compiz.

3 soluciones :

- Compre una tarjeta conveniente de los gráficos y póngala en su computadora.

- No utilice el compiz

- Intente el compiz saltando la prueba negra de la lista ```
SKIP_CHECKS=yes compiz-manager
```
CotCot,
Thank you for your answer. So, where do I need to change the code that you sent me, Do I need run this from the terminal window? or I need add this line in some place?

---

### Post by cotcot on 2009-10-25
From terminal. The code is coming from the link in your first post.

---

