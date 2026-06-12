---
title: "alsa sound driver"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by croquagei on 2007-09-06
Hey guys

i was following the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+blaster](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+blaster)

I got to the point where i used the command ```
sudo modprobe snd-
``` and pressed tab to view all the available modules.  Unfortunately I couldn't find the one needed for my **Sound Blaster Audigy Value**

I had obviously already checked the website to see if my card was supported to learn the name of the chipset module needed.  On this page: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) it lists my sound card as being supported and CA0106 as is it's chipset.  Only with the above code and instructions from that thread it doesn't list that chipset module

So what do i do?

---

### Post by deadgobby on 2007-09-06
Oh, that is a good guide, but it is out dated and can be miss leading.  I have a sound blaster live and reads as ca0106 if I type in the terminal 
aplay -l

 If I type in 
lspci -v 

 I get this

00:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
 It can be a bit confusing.  And thus the problem lies. So how to get that pesky sound problem solved. Simple really. Go into Synaptic and install 
alsamixergui

 Once installed. Open up the program that can be found in Apps> Sound&Vid> alsamixergui. Pop In a Audio CD. Any CD that is Audio CD. Let Ubie read it and the default player will open up and start playing. Look for the Analog Front and turn up the volume by clicking on the right mouse to the volume level you want. All so a other trick is to double click on the speaker icon. Go to switches tab and click on and off the IEC 958 box. If you get sound... Rejoice and kill the minstrels.

Gobby

---

### Post by croquagei on 2007-09-06
The ALSA mixer has detected my onboard sound card instead of my sound blaster.  How do i rectify this?
EDIT: Fixed this by turning the onboard sound off in bios.

I just used the command ```
lspci -v
```
And i get this:
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

Why would i be denied access to my own sound card?

---

