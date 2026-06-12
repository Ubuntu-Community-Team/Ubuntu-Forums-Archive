---
title: "GWC External USB SoundCard = no sound"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by victorgreen on 2007-09-25
I got a shiny new 5.1 usb sound card today made by GWC. Several of the reviews on Newegg indicated that it worked fairly well with Ubuntu. See the info about the device here: 
[http://www.newegg.com/Product/Product.asp?Item=N82E16829126101](http://www.newegg.com/Product/Product.asp?Item=N82E16829126101)

I plug it in and its big read power light comes on... and nothing else happens. I plugged my speakers into it and they popped a bit as the plugs went it, generally a good sign. 

Ubuntu recognizes only my laptop intel sound card, and indeed, system - pref- sounds now only shows analog devices AD1984 (OSS Mixer) instead of my HDA sound intel device. 

The command: aplay -l   gives me this with no difference whether or not the external sound card is plugged in or not: 
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1592:(snd_config_load1) :58:1:Unexpected }
ALSA lib conf.c:2849:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (0): Invalid argument

My sound card doesnt even seem to be being detected. As a side note, it seems my /etc/asound.conf file is messed up too. How would I fix that?

Thanks

---

### Post by victorgreen on 2007-09-25
those smileys were not meant to be htere, it auto interpeted the : ( as a smiley i guess

---

### Post by victorgreen on 2007-09-25
I have recompiled my alsa to 1.0.14 with no difference whatsoever in anything.

---

### Post by victorgreen on 2007-09-25
I fixed the detection of my intel sound card and thereby fixed audio quality issues by deleting my /etc/asound.conf file. 

How do I get the module snd-usb-audio to load?

---

### Post by victorgreen on 2007-10-05
I just had a VERY weird experience with sound. 

I went to the alsa website, downloaded and compiled the lasted release candidate of alsa (1.0.15rc3). My usb soundcard was recognized!! Sound came out, it was amazing. I unplugged it to make sure the onboard still worked, and it did. I was happy. Then I noticed that although my volume up down buttons still displayed the little volume bar rising/falling on the screen, but the volume didnt actually change. Only the gnome applet actually controlled sound. 

I then replugged the usb sound card and set prefs-sound to use it. No sound, no joy. All the sound came out of the onboard speakers. 

I restarted. Now prefs- sound doesnt show the usb sound card as an option and 
:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8220000 irq 19

shows only my onboard when before it showed the USB as well. 

The volume controls work now too. 

Im really confused.

---

