---
title: "Mic not working fujitsu amilo 1718 ubuntu 10.04"
date: 2010-07-25
forum: Multimedia Software
---

### Post by koco on 2010-07-25
Hi there, i'm here again with sound problem. I can't make internal mic to capture any sound (specially in use with skype :/ ) 
i did some change to 
/etc/modprobe.d/alsa-base.conf and i add this at the end 
options snd-hda-intel index=0
options snd-hda-intel model=auto

where i ws changing 'auto' to acer, lenovo.. etc. as i read somewhere on forum that for 
[B]cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC861-VD
Codec: Motorola Si3054

[/B]card you have to try to change model in order to make thing's work, but this solution doesn't work for me.

i checked alsamixer settings and boost mic but nothing   :)
i really need to have this done as it's for someone else. 
I'm not good in linux at all so i might be missing something but what i do is i'm just setting up laptops for friends to ubuntu as windows give you window but linux give you whole house :)

thank's in advance koco

---

### Post by lidex on 2010-07-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by koco on 2010-07-29
So after spending some time to fix dual boot with win xp i got ubuntu back so here are think's you asked me to check. I'm getting confuse as this laptop Fujitsu siemens li1718 might not have internal mic as i cant find any small hole as you can see on 99%of laptops and i spoke with owner and he sad that he had to buy   headset with mic (in win xp mic does not work ether) So it doesn't have internal mic but have jack instead o use as mic input interface.
I dont have any headset here so i wont be able to test this and i HATE to return pc/laptop without any testing and NOT FINISHED !!!!!!!!!!!!

So the question now is will it work from external device mic/headset ????????????


I have no idea why all laptops/pc i was setting with ubuntu in past 2 years had common problem wifi/sound/hdmi.......  
As i sad i'm not using ubuntu myself as i'm running on mac and freebsd in vmware but i do have simple file server running opensuse and didnot had problem to set it on 12 years box and i'm using it for watching online movies as well (recently powrsupply burn out after 5 months nonstop on :(  )
I Just wanted to help friends and guys who suffer from using winshit but more and more is dificult to setup simple thinks. I'm  sad as i like to do this for folks out there  :( 

Sorry forget to mention that output jack for speakers is working correctly.

Linux bejk-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

*** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


i  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA


==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC861-VD

---

### Post by lidex on 2010-07-30
This is a pretty stripped-down laptop. As you mention there is no internal mic. The input is shared stereo line/mono mic so you want to make sure to lower the level on one side - right I believe - in pavucontrol when using the mic. With no mic to test with (did I read that correctly?) simply check to see if you can get the line input to work. At this point I can't be certain there is a problem so...

---

### Post by koco on 2010-07-30
I'm sorry for my english but im not native speaker :)  anyway i'll test that laptop as soon as i get chance and post here how it goes hope that mic will work and hope that everything will work.

thank's for help lidex

---

