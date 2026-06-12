---
title: "How to setup and use TV and FM Tuner cards?"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Agent24 on 2008-10-26
I'm using Ubuntu 8.04 and have a GemTek PCI Radio card and an Askey CPH05X/06X BT878 TV Tuner

What software do I need to install to be able to watch TV stations and use the radio?

Thanks in advance

---

### Post by cariboo on 2008-10-26
In a Applications-->Accessories-->Terminal type:

```
sudo lshw -C multimedia
```

To see if the drivers have been loaded for you TV card, it should be atomagically detected and the driver loaded. If the driver has been inserted, try a program like tvtime. Tvtime is available in the repositories, you can install it using Add/Remove Programs, Synaptic Package Manage and of course the command line.

Jim

---

### Post by Agent24 on 2008-10-26
I imagine this means the drivers are loaded?

```
  *-multimedia:0          
       description: Multimedia audio controller
       product: PCI Radio
       vendor: GemTek Technology Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: driver=gemtek_pci latency=64 module=radio_gemtek_pci
  *-multimedia:1
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=bttv latency=64 maxlatency=40 mingnt=16 module=bttv
  *-multimedia:2 UNCLAIMED
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: f.1
       bus info: pci@0000:00:0f.1
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64 maxlatency=255 mingnt=4
  *-multimedia:3
       description: Multimedia audio controller
       product: ES1968 Maestro 2
       vendor: ESS Technology
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ES1968 (ESS Maestro) latency=64 maxlatency=24 mingnt=2 module=snd_es1968
```


EDIT: I just installed TVTime, but when I run it, it just flashes briefly on the screen and then disappears.

---

### Post by Agent24 on 2008-11-16
I have fixed the problem with TV Time (issues with video card) and it now runs properly.

I can connect my camera to the Composite input and it will show up in TV Time fine.

BUT I cannot seem to use the tuner. How can I get the tuner working??

---

### Post by Agent24 on 2008-11-16
I have searched some more and found this:

[http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/](http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/)

However I get problems when I get here:

> This line “options bttv card=37 tuner=30 radio=1 pll=1 adc_crush=0“, as I told you before that I’m using Pixelview PlayTV Pro, according to the CARDLIST, it has number 37.

I checked the cardlist ([http://mandrivausers.org/index.php?showtopic=43596](http://mandrivausers.org/index.php?showtopic=43596)) but I'm not too sure what I need to choose.

Card itself just has a sticker on back with "CPH051" so the only thing that makes sense to fit is card 24, which is CPH05x. 

As for tuner, nothing seems to match. Sticker on the Tuner says:

"3139 147 13371L
FM1216/PH hm
SV23 0004"

FM1216 comes up in the tuner list for cards 3 & 38 (FM1216MF & FM1216ME MK3) respectively but PH appears nowhere and 'hm' doesn't seem to fit anywhere either...

---

### Post by Agent24 on 2008-11-16
Finally got it working - Using card 24 and Tuner 5 !!!

Turns out my reception wasn't perfect enough for TVTime to pickup the channels properly so it was discarding the whole lot and showing just a blue screen

Once I turned off signal detection I was able to get everything as good as my bad antenna could allow

FM Radio in the card also works (haven't tried the gemtek yet)

HOWEVER.. Line-in on my soundcard appears to not work!! so I can only get sound I plug the speakers directly into the tuner card.... :(

---

