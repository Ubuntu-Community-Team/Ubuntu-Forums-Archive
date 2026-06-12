---
title: "RME Multiface on UbuntuStudio"
date: 2008-04-19
forum: Multimedia Production
---

### Post by tigabeatz on 2008-04-19
hi there, 

I installed my first ubuntu last weekend.I am a real linux noob so I really need your help. I got through the installation with no problems. but my soundcard does not work. I use a laptop with RME Multiface via PCMCIA. it seems that the multiface gets recognized but does not work. please see details below.    

my questions:

1: how do I get the multiface to work properly?

2: and afterwards use it in Ardour / Jack with all 18 channels?

Details:
-RME Multiface & pcmcia Card
-Toshiba Satellite
-ubuntustudio 7.10 gutsy gibbon
-hdsp alsa pakages are installed 
-alsa packages are in version 1.0.14, but there are newer ones on the ALSA Project site (v 1.0.16) if it is nescecary to install the new ones, I need someone to tell me how to do this... *looking ashamed

-I cant switch off the onboard soundchip in BIOS

audiomobil@audiomobil:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with unknown codec at irq 11
 1 [DSP            ]: H-DSP - Hammerfall DSP
                      RME Hammerfall DSP at 0x58000000, irq 10



audiomobil@audiomobil:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : Intel 82801DB-ICH4 with unknown codec at irq 11
Card 1 : RME Hammerfall DSP at 0x58000000, irq 10
Upload firmware for card hw:1
Unable to open file '/usr/share/alsa/firmware/hdsploader/multiface_firmware_rev11.bin' for reading
audiomobil@audiomobil:~$ 

I would be very happy if you can help me!

do you need any further information?

many thanks, 
tiga

btw. 
i can not find that missing 
/usr/share/alsa/firmware/hdsploader/multiface_firmware_rev11.bin
anywhere. shouldnt it have been installed with the hdsp packages?

---

### Post by thorgal on 2008-04-19
it is most likely sitting in /lib/firmware

---

### Post by tigabeatz on 2008-04-20
oh yeah, many thanks thorgal. that helped. ;-) 

for some strange reason i am not able to search my harddisk (get a error message when i try to) but with your post i found that *.bin file. 

via terminal i was able to copy the file to the hdsploader folder and at least could ctest it via the system seeting. jack seem salso to recognice it properly. 

new testing ardour with it. 

audiomobil@audiomobil:~$ sudo cp /lib/firmware/hdsploader/multiface_firmware_rev11.bin /usr/share/alsa/firmware/hdsploader
audiomobil@audiomobil:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : Intel 82801DB-ICH4 with unknown codec at irq 11
Card 1 : RME Hammerfall DSP at 0x58000000, irq 10
Upload firmware for card hw:1
Firmware uploaded for card hw:1
audiomobil@audiomobil:~$

---

### Post by thorgal on 2008-04-20
great!
I own a Multiface II, and I use it daily for my music production. It runs perfect!

Well, actually, there's only ONE annoying thing : if you put your PC to sleep and wake it up, it screws up something so the multiface becomes unusable. The only thing to do then is to shutdown the computer AND power it off (remove the power cable). It seems to reset everything and a new boot restores everything correctly. Apart from that, it is an excellent piece of hardware!

---

