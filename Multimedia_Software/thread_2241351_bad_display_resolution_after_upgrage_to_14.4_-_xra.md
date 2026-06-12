---
title: "bad display resolution after upgrage to 14.4 - xrandr fails"
date: 2014-08-25
forum: Multimedia Software
---

### Post by Leto_Fregar on 2014-08-25
Hello!
I am using Kubuntu for some years now, but I just crashed into a problem that I neither can fix myself nor did I find a solution via the existing posts in this forum or google. I hope someone can help me:

Situation: I am using a Toshiba Satellite L350D as Laptop. Including yesterday, everything was fine. The laptop is seldom in use, but during a vaction trip it came back to live. Today I had a little time and upgraded to Kubuntu 14.4. The upgrade went smoothly, but for some reason I cannot understand my screen resolution is now set to a strange 1152x864 (the physical resolution 1440x900).

I had similar problems (independent of the (k)ubuntu version with other computers already, so I tried to fix it with xrandr. However this time it does not work. After some reading and remembering old cases I tried the following:

```
~$ xrandr --newmode "1440x900_76.00"  138.50  1440 1536 1688 1936  900 903 909 943 -hsync +vsync     
xrandr: Failed to get size of gamma for output default
~$ xrandr --addmode default "1440x900_76.00"
~$ xrandr --addmode default "1440x900_76.00"     
xrandr: Failed to get size of gamma for output default
~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1152 x 864, current 1152 x 864, maximum 1440 x 900
default connected primary 1152x864+0+0 0mm x 0mm
   1152x864       76.0* 
   1440x900_76.00   75.9  
:~$ xrandr --output default --mode 1440x900_76.00 --pos 0x0 --rotate normal   
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```

I tried some additional options but at the end I always get the result 
```
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```

Some further things I tried to find a hint:
```
~$ sudo lshw -C video
PCI (sysfs)  
  *-display UNGEFORDERT   
       Beschreibung: VGA compatible controller
       Produkt: RS780MC [Mobility Radeon HD 3100]
       Hersteller: Advanced Micro Devices, Inc. [AMD/ATI]
       Physische ID: 5
       Bus-Informationen: pci@0000:01:05.0
       Version: 00
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi vga_controller bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:e0000000-efffffff ioport:6000(Größe=256) memory:f6200000-f620ffff memory:f6100000-f61fffff
```
As far as I can see there is no driver mentioned in this output, so this might be the problem? Where can I get the right one? Or is there a wayI can set the gamma value manually? Without knowing what I really have to do I tried
```
~$ xrandr --output default --mode 1440x900_76.00 --gamma 255:255:255
xrandr: Gamma size is 0.
```
Probably the value was nonsense, but no matter what I tried it was either invalid or "xrandr: Gamma size is 0."

Can anyone please help? Do you need aditional information?

Best regards,

Leto

---

### Post by Leto_Fregar on 2014-08-25
Forgot one thing: this page gives some technical details about the laptop:
[http://www.toshiba.de/discontinued-products/satellite-l350d-11k/](http://www.toshiba.de/discontinued-products/satellite-l350d-11k/)

---

### Post by arakelov on 2014-11-07
Hello, I would like to know if you could solve the problem. I'm experiencing the same thing with Lubuntu 14.04.

Kind regards.

---

### Post by Leto_Fregar on 2015-04-01
Hello arakelov,

I could never really solve the problem, but we could narrow it down: there seems to be some communication issue between the driver and the graphics card, but we could never fix it. 

However: today I updated to Kubuntu 14.10, and now it works again. Seems this problem only exists in 14.04.
So maybe this is a solution for you as well?

Best regards,

Leto

---

### Post by arakelov on 2015-04-01
Thanks for your response, Leto. I'll also try to upgrade and see if it's solved.
Regards.

---

