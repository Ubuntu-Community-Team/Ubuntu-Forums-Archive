---
title: "NO sound on  Via VT8233/A/8235/8237 AC97 Audio Controller"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by kakashi on 2005-10-14
i just installed breezy and i can't get any sound 
i did not have sound with hoaray either 
please help 

my computer is 
Amd sempron 2400
MSI KM3M-V
onboard sound and video and lan 

this is what lspci says 
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


i have provided any info i could think off 
if any thing else is needed do tell me 
i really want sound 

also when i run multemedia system selector 
i cannot run Alsa becase when i press check it say failed to construct pipline
and when i try OSS or ESD all i hear i a strange clicking sound through my head phones

---

### Post by tecantonio on 2005-10-14
hi!, well, i dont now so much english, but im goin to try.....

you now, im a newbie too, and i have the same problem, and i do this:

open the window "volumen control", i mean, two click on the icon sound, its at the left of the time icon on the taskbar
clik on the menu file, then select on the change disp. the via 8237 (alsa) option

after that, clik on the menu edit, then preferences, select all the options in that window, an then close, you are gona note that there's anothers options in de volumen control window, well, then clik on the "conmutadores" tab (im sorry, i dont now how to say that in english)its the third one from de left to the right, then uncheq evert option that is there, in special the "iec958 capture monitor" option, then put all the volumens loud (to the top) and thats it, well it works for me, an i hope that they work for you......

-to&#241;o-

---

### Post by kakashi on 2005-10-14
thanks for your answer 
i dont know what did this but now when i log into gnome i hear a sound for 1 sec 
then it it turns into a crackling sound. i have tried the solution [here]("https://wiki.ubuntu.com/SoundProblemsHoary") but it does not work please help

---

### Post by kakashi on 2005-10-15
please somebody help me 
i know the topic says NO sound but still i don't want to start a new thread
for the same problem

---

### Post by jarrett.wold on 2005-10-15
Open up a terminal

```

~$ alsamixer


```

In alsamixer, make sure that neither Master or PCM are muted.  You can tell if they're muted if they have the letters MM below the vertical bar.  You can mute/unmute by arrowing (left/right) over to either Master or PCM and pressing: 'm' without quotes.  You can increase or decrease the volume on each by arrowing up or down, while each is highlighted.

---

### Post by kakashi on 2006-02-17
my bad. i had plugged the headphones in the wrong slot.

---

