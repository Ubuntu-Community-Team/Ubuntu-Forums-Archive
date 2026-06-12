---
title: "[SOLVED] ASUS m51 laptop sound"
date: 2008-09-27
forum: Multimedia Software
---

### Post by L4S7 on 2008-09-27
I am a total noob at getting code to work.

I installed ubuntu on my ASUS m51 laptop. i am trying to get the sound working and cant seem to figure it out. 

i have looked at [this ]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusM51Sn")but i typed all that code in and didnt get anything back.

I think i got alsa installed but i am not to sure.

also i dualbooted with Vista and want to loose vista and i couldnt figure out how to do it in the boot up process any help there?

---

### Post by pyth3n on 2008-10-06
If you have a solution, I'd be interested in hearing it. I'm having the same problem.

---

### Post by neorg on 2008-10-24
Yesterday I installed the Intrepid Beta 64AMD version on my ASUS laptop M51 (V-serie M51V). As far as I can see now everything is working fine. Sound, Video, WiFi, LAN etc. ME HAPPY :)



FlapFlop:~$ lspci  | egrep -i 'audio|vga|network|ethernet|firewire' 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

---

