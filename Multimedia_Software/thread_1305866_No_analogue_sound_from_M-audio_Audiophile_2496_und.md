---
title: "No analogue sound from M-audio Audiophile 2496 under Karmic Koala"
date: 2009-10-30
forum: Multimedia Software
---

### Post by silvera on 2009-10-30
Hi,  I installed Ubuntu 9.10 and have no longer analogue sound.   In Sound Preferences under the Hardware tab I can choose from nine different profiles for my device. Eight of them are digital and one is Off.  Since I have no digital amplifier I must have analogue sound output.  Thanks in advance for any help.

---

### Post by Paulo Wageck on 2009-10-30
same issue here.

no analog sound with my m-audio delta 44 (koala 64). 

how do we fix it? 

pulseaudio problem maybe?

sound in linux is still a problematic issue...


thanks!

---

### Post by kronikabis on 2009-10-30
same thing here too! PLEASE HELP! :)

---

### Post by Paulo Wageck on 2009-10-30
"aplay -l" results:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Interestingly this onboard VIA card is disabled on BIOS but all generations of ubuntu still recognize it even thou!

---

### Post by Paulo Wageck on 2009-10-30
"aplay -L" results shows the card.

BUT

pulse audio is not recognizing analog and digital audio...

i wonder if it is a pulse audio config problem or a pulseaudio binary problem....

---

### Post by bluemind on 2009-10-30
Hi!

I have the same problem and the sound started working after removing pulseaudio with "sudo apt-get purge pulseaudio".

Also in the 'system->preferences->multimedia systems selector' I set the output to autodetect ('right click systems --> edit menus', if that doesn't show up).

My only worry is that that it removed the ubuntu-desktop package, which probably will affect some update stuff. Maybe it can be reinstalled when pulseaudio is updated and works?

Cheers
Risto

---

### Post by Paulo Wageck on 2009-10-30
the purge pulseaudio didn't work for me... alsa still have problems with the card....

take a look at: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/)

tried that too... worked for some ppl... not for me....

this is a VERY annoying bug....

---

### Post by silvera on 2009-10-30
'system->preferences->multimedia systems selector' is not available in my menu.  I'm using 32-bit desktop Ubuntu.

---

### Post by Paulo Wageck on 2009-10-30
> **silvera said:**
> 'system->preferences->multimedia systems selector' is not available in my menu.  I'm using 32-bit desktop Ubuntu.

do what the previous post says: 

"Also in the 'system->preferences->multimedia systems selector' I set the output to autodetect (_'right click systems --> edit menus', if that doesn't show up)_ "

---

### Post by kronikabis on 2009-10-30
Got mine working as in the link:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/)

> I added this to /etc/pulse/default.pa and it works for me (I didn't
comment out any lines like the original workaround said).

# Workaround for MAudio Audiophile
# [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7)
load-module module-alsa-sink sink_name=M2496_out device=hw:M2496
format=s32le channels=10
channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
load-module module-alsa-source source_name=M2496_in device=hw:M2496
format=s32le channels=12
channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9

---

### Post by bishopblaize on 2009-11-06
Just to confirm that adding the above line to etc/pulse/default.pa solved the problem for me. I didn't do anything else. it was a clean install tho not an upgrade.

thanks for the help.

---

### Post by airtac on 2009-11-06
I am having sound problem too, after loading 9.10.  I tryed reinstalling drivers and everything I can find online.

Help

aplay -l
aplay: device_list:223: no soundcards found...

lshw -C multimedia
[sudo] password for ******: 
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fdff4000-fdff7fff

---

### Post by SineCosine31413 on 2010-01-22
My Audiophile 2496 works with Karmic!  Rythmbox, MoviePlayer, YouTube, Audacity; they all work!

I spent a solid 2 week trying to get my  Audiophile 2496 to work with Karmic.  Seriously, I tried everything to get this to work.  I built drivers from source, I rebuild pulseaudio and I tried OSS instead of ALSA or pulseaudio.  In the end, I screwed it up even worse than it was originally!
 
 In hind site, The Ubuntu Sound Troubleshooting guide helped me a lot:
 [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
 
 So, here is what I did to get my Audiophile 2496 to work with Karmic:
 
 1.  I “restored” my audio core by following the directions in the Troubleshooting Guide (see above link).  Look under “Manual Installation”.  Then, page down a bit and look at “Refreshing/Reinstalling the drivers”.  I followed the directions in the 2 paragraphs listed there.  I rebootoed.
 
 After the restore, Karmic recognized my 2496 but I had no sound.  (This was an improvement, BTW, because previous to the restore, I had no driver at all).
 
 2.  I added the 2 lines to my /etc/pulse/default.pa as described in: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7).   
 
 Specifically, this is what I added:
 
 load-module module-alsa-sink sink_name=M2496_out device=hw:M2496 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
 load-module module-alsa-source source_name=M2496_in device=hw:M2496 format=s32le channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
 
 One other thing I did was to make sure all of the mixer levels were up in alsamixer.  I did this before I added the lines to /etc/pulse/default.pa so I do not know if this has an effect on anything or not.  I had read in many other posts in various places that alsa mutes the mixer channels by default.
 
Hope this helps...

---

### Post by streamsanddragonflies on 2010-02-28
Hi! Having no sound in Ubuntu Studio 64 karmic, I searched related bugs and followed instructions from comments in launchpad.  I was trying to get the maudio card to work properly all day but still no luck.  I did get ALSA to work now with the added lines in etc/pulse/default.pa and most applications have sound exept movie player and pulse audio- which at least worked before with volume meters moving and no sound-now fails to start. I am stumped; I even followed the  pulse audio thread in the forums but when I try to start pulse audio I get :


 "~$  pulseaudio & pavucontrol
[1] 8147
E: module-alsa-sink.c: Failed to parse module arguments
E: module.c: Failed to load  module "module-alsa-sink" (argument: "sink_name=M2496_out device=hw:M2496 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,au x5,aux6,aux7"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio"


I read and it seems that channels and sink are not set right or there was another setting to change but my mind is a blur now!  And it needs to be set specific to the card again...

I will add a bug to pulse audio as well-cause I need to have sound set right if I want to learn how to use the multimedia productions apps!

If anyone can help me I would really appreciate it!

---

### Post by HippieDave on 2010-12-29
> **kronikabis said:**
> Got mine working as in the link:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/)

I did too. I entered the change exactly as set forth and it worked...sort of.  Initially I had sound, but only out of one stereo track.  Then I went into alsamixer and fiddled around.  when I turned the HW and HW1 channels to PCM Out, I got both channels working.  So now it seems fixed, I have both playback and record on both channels...HOWEVER, I cannot access the Sound Preferences through System --for example- if I wanted to mute everything temporarily ...

Any thoughts on how to keep sound and get the volume/preferences controls back?:confused:

---

