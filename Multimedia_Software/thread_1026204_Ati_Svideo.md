---
title: "Ati Svideo"
date: 2008-12-30
forum: Multimedia Software
---

### Post by Labmonkey on 2008-12-30
Hello, I have a Dell Inspiron 5000 laptop. I am turning it into an arcade machine, and that involves hooking it up to a tv. It has an Svideo output, but just shows a blue screen on my tv. I googled around, and it seems like there are a bunch of threads about this, but none of them have solutions. If there is a solution, thats great, but if there isn't please also tell me. I just want to know so I can get on to doing other things.

graphics card: ATI Range Mobility
computer: Dell Inspiron 5000

---

### Post by Ng Oon-Ee on 2008-12-30
Suggest looking into ATI's website for instructions, especially on how to configure xorg.conf for your specific case.

I know nvidia has a wiki for their linux drivers, but I'm not sure about ATI, being a staunch NVidia user for years now.

---

### Post by Melcar on 2008-12-30
Well what drivers are you using?  If you installed the drivers from the "restricted modules" then you got fglrx, which is easily configured with the CCC (or check out the [wiki]("http://wiki.cchtml.com/index.php/Main_Page")).  If you're just using radeon (the default driver that Ubuntu loads up from the beginning) then check the radeon wiki (or simply enter "man radeon" on a terminal to look at the manual for the driver):

[http://www.x.org/wiki/radeon]("http://www.x.org/wiki/radeon")

---

### Post by Labmonkey on 2008-12-31
I looked around some more following the link you gave me, and it seems that atitvout [http://0pointer.de/lennart/projects/atitvout/](http://0pointer.de/lennart/projects/atitvout/) will solve my problem. I installed the package, but when trying to run it I get the error message:
open /dev/mem: Permission denied
Could not initialise LRMI.

Is there any way i can fix this. I am not sure what lrmi is, and have failed at googling it.

If you need more info (i have no idea what you might need to know to solve this, im a linux noob) here is the output of lspci.

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)

---

