---
title: "No LCD Backlight on 2.6.38-7-generic update"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gunbladeiv on 2011-03-22
I finish updating Natty to latest update using main server.  After finish dist-upgrade process, i restarted my laptop and bammppp~! 

The screen was there but it was dim until nothing seem to be visible. and i notice my LCD backlight didn't working. I was pretty sure that it is a kernel problem because when i revert to kernel 2.6.38-6-generic the screen was working fine. So is there any fix that i could possibly apply on this latest updated kernel to make it working on my acer 4736Z? any one with the same laptop having similar problem like me?

IMHO this is a critical bug cause the brightness button didn't working since 10.04 and now the LCD light is gone. If there is anyone could help me please guide through this process.  I have a bit knowledge on using terminal and following instructions. :p

Thanks in advanced.

---

### Post by VMC on 2011-03-22
I'm guessing your running Unity. Have a look at Backlight Mode. More than likely its turn on, but can't hurt to check anyway.

---

### Post by lucazade on 2011-03-22
> **VMC said:**
> I'm guessing your running Unity. Have a look at Backlight Mode. More than likely its turn on, but can't hurt to check anyway.

He is speaking about lcd panel brightness, not about Unity tiles background!
Look at /var/log/dmesg if there are differences between two kernels.

what is the output of (with both kernels):
ls /proc/acpi/video/*/LCD/brightness

try also to add "acpi_backlight=vendor" to grub (kernel parameters)

---

### Post by glococo on 2011-03-22
Hi,

Nightmare!
I have the same issue, cant boot with 2.6.38-020638-generic nor can make a dmesg

Tried different options in grub2:
acpi_osi=Linux, acpi_backlight=vendor and legacy, acpi=off
and none work out.

notebook: emachines E725
VGA: Intel Mobile 4 series IGP rev 09

dmesg in 2.6.35:
ACPI:Video Device OVGA Multi-head: yes rom:no post:no

Any guide ?

UPDATE: Cant access "Recovery option" menu nor shell. Complete backlight disabled.

UPDATE2: NOW -> CAN CONTROL brightness via: "sudo setpci -s 00:02.0 F4.B=7F" in 2.6.35 (cant try in 2.6.38 since cannot see anything.)

---

### Post by gunbladeiv on 2011-03-23
My problem solve when i append acpi_osi=linux acpi_backlight=vendor to grub line. Even though the fn+increase light function awkwardly(by awkward i mean it functioning in reverse mode. Increase light turn out to be decreasing the light :) ) but still i can see my screen right now. and for the first time my short key to control backlight working after 9.04 distribution. 

Right now, what was crashing is compiz. It doesnt load on boot and no windows decorator for my unity and no unity-panel on top and left screen.  Sad. i need to figure this one.  Some said that it is incomplete upgrade. it's my fault BTW.

---

### Post by lucazade on 2011-03-23
> **gunbladeiv said:**
> My problem solve when i append acpi_osi=linux acpi_backlight=vendor to grub line. Even though the fn+increase light function awkwardly(by awkward i mean it functioning in reverse mode. Increase light turn out to be decreasing the light :) ) but still i can see my screen right now. and for the first time my short key to control backlight working after 9.04 distribution. 

Right now, what was crashing is compiz. It doesnt load on boot and no windows decorator for my unity and no unity-panel on top and left screen.  Sad. i need to figure this one.  Some said that it is incomplete upgrade. it's my fault BTW.

I'm glad acpi_backlight=vendor helped you!

---

### Post by neiltwist on 2011-04-12
> **glococo said:**
> Hi,

Nightmare!
I have the same issue, cant boot with 2.6.38-020638-generic nor can make a dmesg

Tried different options in grub2:
acpi_osi=Linux, acpi_backlight=vendor and legacy, acpi=off
and none work out.

notebook: emachines E725
VGA: Intel Mobile 4 series IGP rev 09

dmesg in 2.6.35:
ACPI:Video Device OVGA Multi-head: yes rom:no post:no

Any guide ?

UPDATE: Cant access "Recovery option" menu nor shell. Complete backlight disabled.

UPDATE2: NOW -> CAN CONTROL brightness via: "sudo setpci -s 00:02.0 F4.B=7F" in 2.6.35 (cant try in 2.6.38 since cannot see anything.)

Very interesting, I have the same issue, with the only thing that works for me being the last command:

> sudo setpci -s 00:02.0 F4.B=7F

I am able to test this on 2.6.38 by using an external monitor, and it does indeed adjust the brightness to make the screen visible.

So, is there something that is setting the brightness to 0 on boot? Or is it the fact that the brightest setting is achieved by setting it to "0"? Could it be related to the fact that the brightness controls are reversed? (ps, they don't work on my machine at all)

Any help is appreciated, as I currently have to manually run this command on login, or after the screen has gone to sleep (meaning I must log in or unlock the screen without the backlight...)

---

### Post by travmon69 on 2011-04-16
I just add acpi_osi=Linux to the end of kernel line in grub. works on my my acer with intel gma 4500m

---

