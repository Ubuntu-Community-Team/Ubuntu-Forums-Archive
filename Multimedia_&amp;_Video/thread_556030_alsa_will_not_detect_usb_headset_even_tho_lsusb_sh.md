---
title: "alsa will not detect usb headset even tho lsusb shows it"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by mjkelly on 2007-09-20
laptop:~$ lsusb
Bus 002 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 047f:0ca1 Plantronics, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

laptop:~$ asoundconf list
Names of available sound cards:
Intel
Sometimes it works. Sometimes it doesnt. I cant figure out why. USB is finding it and identifying it correctly but alsa is not picking it up. Why not?

Also i have i the usb line set to index 0 in the right file im not gonna go looking for it, but its set to 0.


On a side note,  i have a USB mouse that works perfectly fine but now how do i disable the keyboard on my laptop.  I constantly accidently touch it and its driving me nuts.

---

### Post by Mobus on 2007-09-26
I am having this exact same problem but with the Gigaware USB headphones.  lsusb is detecting it perfectly, however none of my programs are using it.

---

### Post by Mobus on 2007-10-01
Any takers?  I'd really like to be able to use my headphones, as it helps when I'm watching Star Trek

---

### Post by Mobus on 2007-10-11
bump

---

### Post by mjkelly on 2007-10-18
bump

---

### Post by khughitt on 2007-10-19
Have you upgraded to gusty? Gusty includes a newer version of ALSA.. Perhaps if you are lucky it will start to detect your headset. I have a plantronics headset, but it is detected when I look for it, although it usually is listed as an address without any informative naming (e.g. U0x47f0xc001).

> Names of available sound cards:
ICH5
U0x47f0xc001


---

### Post by nzadLithium on 2007-10-19
is it possible it has detected it but not as a sound card? I havent actually got any usb headsets so i don't know. But when you plug it in does the sound stop from speakers?

---

### Post by elj4176 on 2007-11-06
i have this headset as well and am on gusty on my hp dv9074 laptop. It shows up in the sound prefs and I can select it but I get no sound in the headphones. the mic works tho.

really strane problem. it didnt work in feisty either.

any ideas?

---

### Post by erisianmonkey on 2007-11-07
I'm having a similar problem with a logitech USB headset. ALSA shows it, but I cannot use it.

---

### Post by ridetheteapot on 2007-11-07
i don't have usb headphones either but i use a usb soundcard.
i don't know how your configuration goes, but i know for mine i always ahve to do it manuelly

first i cat /proc/asound/cards

and take note of the name, not the number of the device looks like this: 
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xa800, irq 21
 1 [MP3            ]: USB-Audio - Sound Blaster MP3+
                      Creative Labs Sound Blaster MP3+ at usb-0000:00:1d.0-2, full speed
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

the key with my usb soundcard is to use the device name instead of the number, cause that can change from boot to boot on a usb device.

then in your /etc/asound.conf or your ~/asoundrc replace the pcm "hw:#,#" to pcm "hw:NAME"
and i guess do the same for the card options for the mixer.
then use alsa like normal

maybe that is the problem?

incidently my gutsy install didn't have an asound.conf to start out with, which i though was really odd, because i thought that was the default now

---

### Post by theovercoat on 2007-11-08
hey man, set your usb index line to 1 instead of 0

*sudo gedit /etc/modprobe.d/alsa-base*

then make sure this line looks like...

*options snd-usb-audio index=-1*

save and reboot please!

truth be told, that has been my usb audio miracle for sound playback in everything in both fiesty and gutsy.

---

### Post by skizzabadoo on 2008-04-22
Still no luck.  

lsusb returns: 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0b0e:620c GN Netcom 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

When I changed the value from 0 to 1 I still had no response. Any other ideas out there?

---

### Post by grashdur on 2008-04-30
I've had this problem with a GigaWare USB headset for a year and a half. Now with Hardy Heron, I just did System: Preferences: Sound: Devices [tab]: set the desired output to &#8220;USB audio&#8221; and it works fine, though not with every program (VLC Media Player can't use it). I hope this option is also available in Gutsy Gibbon, because I'm just about to downgrade back (because so many programs like Skype and Amarok won't install, and I have many many problems with sound & video).

---

