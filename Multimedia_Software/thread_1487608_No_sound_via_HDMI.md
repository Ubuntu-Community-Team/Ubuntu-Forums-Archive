---
title: "No sound via HDMI"
date: 2010-05-19
forum: Multimedia Software
---

### Post by AntiBarbie on 2010-05-19
Hey

I can't get any sound via HDMI. 

I have my computer hooked up to my TV with a HDMI cable. Video works fine, but the sound comes from the laptop's speakers and not the TV speakers.

In my **aplay -l **there is nothing about HDMI at all... :confused: My graphics card is NVIDIA GeForce 9300M GS


Liz@MediaPC:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

I just have no idea what to do, and would appreciate some help!! :KS

Thanks a bunch /// [COLOR=Magenta]~~Liz[/COLOR]

[I]PS: 
Before you say anything, yeah I have searched for solutions and I've  tried following instructions, for example this:  [http://ubuntuforums.org/showthread.php?t=1332261&highlight=sound+HDMI](http://ubuntuforums.org/showthread.php?t=1332261&highlight=sound+HDMI)  ...and this:  [http://ubuntuforums.org/showthread.php?t=1476915&highlight=sound+HDMI](http://ubuntuforums.org/showthread.php?t=1476915&highlight=sound+HDMI) ...but no luck so far![/I]

---

### Post by Pope89 on 2010-05-31
i wanted to say, that i have exacty the same problem

i got an asus g60vx laptop with an 
gtx260m 

aplay -l lists:
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC663 Analog [ALC663 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC663 Digital [ALC663 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

and lspci -vv | grep -i audio shows:

/usr/src/modules/alsa-driver$ lspci -vv|grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

so i dont know how to get my hdmi device to show up the only thing i found including hdmi is in /proc/asound/card0/codec#*
Codec: Realtek ALC663
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0663
Subsystem Id: 0x104319a3
Revision Id: 0x100001
No Modem Function Group found
:
:
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x18561120: [Jack] Digital Out at Int **_HDMI_**
    Conn = Digital, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10

so if anyone knows anything about it pls let me know
im googling since 2 weeks and do not find anything except something with inclusding patch_hdmi.c but i don't no how to do this and cant find an description(i'm quite new to ubuntu)

---

### Post by puntua on 2010-06-01
gt240 here
not sound either hdmi or analog, i give up after 2 weeks trying everything

---

### Post by Pope89 on 2010-06-11
so now i write another reply :)
cause i tried now for more then 2 weeks i think and nothing has changed--- even haven't got any sound over hdmi
i would be really thankful if someone who knows something about it could help me, 
or at least tell me that it wont work atm so i can stop searching

thanks a lot
Pope

---

### Post by hvc123 on 2010-06-11
try my post i did this morning 
[http://ubuntuforums.org/showthread.php?t=1507056](http://ubuntuforums.org/showthread.php?t=1507056)


works for samsung tvs dunno about others

---

### Post by hvc123 on 2010-06-11
i think the digital part of your sound card is for optical out. but if you like me and cant be bothered with that use a 3.5 mmmm audio jack from the GREEN output to your HDMI/DVI analogue input

---

