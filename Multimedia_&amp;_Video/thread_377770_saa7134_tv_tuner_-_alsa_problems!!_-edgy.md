---
title: "saa7134 tv tuner - alsa problems!! -edgy"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by stumpy on 2007-03-06
Hey all, having trouble getting the audio working on my SAA7134 TV tuner card.  Got the picture working well with tvtime, but no sound at all

I think the card should be showing as a second sound card, however is not showing up with aplay -l

dmesg gives:

[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[17179971.484000] saa7134_alsa: Unknown symbol snd_ctl_add
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_new
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_card_register
[17179971.484000] saa7134_alsa: Unknown symbol snd_card_register
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_card_free
[17179971.484000] saa7134_alsa: Unknown symbol snd_card_free
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_stop
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[17179971.484000] saa7134_alsa: Unknown symbol snd_ctl_new1
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_card_new
[17179971.484000] saa7134_alsa: Unknown symbol snd_card_new
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[17179971.484000] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[17179971.484000] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed

I reckon this is the problem, any pointers on how to fix??

I have installed latest alsa driver already

thanks in advance!

---

### Post by josesanders on 2007-03-06
The saa7134 tuner cards have a lot of problems with getting the sound off the card, which is why they have an audio output that you are supposed to connect to your sound card.  It is possible to get sound off the card, but chances are it will be out of sync with the video.

Is your tuner card recognized automatically, or do you have to set the tuner number manually?  In trying to get my card to work, it was not recognized on bootup so I had to set the tuner number manually.  I found that if I set the wrong number, sometimes I would get video but no audio in TVTime.

Hope this helps.  Those saa7134 cards are really difficult to get to work in Linux.

---

### Post by stumpy on 2007-03-11
Hi, thanks for your response - I had to set the card and tuner numbers for the saa7134, however none of the tuner numbers that produce sound give me a picture.

The only thing I can think of to try is reinstalling the saa7134 and saa7134_alsa drivers....any ideas anyone?

---

### Post by david_2001 on 2007-03-11
> **stumpy said:**
> Hey all, having trouble getting the audio working on my SAA7134 TV tuner card.  Got the picture working well with tvtime, but no sound at all

I think the card should be showing as a second sound card, however is not showing up with aplay -l

dmesg gives:

[Cut]

I reckon this is the problem, any pointers on how to fix??

I have installed latest alsa driver already

thanks in advance!

When you say "installed latest alsa driver", how did you install the alsa driver?  Those errors are possibly being caused by version mismatches between parts of alsa that have been compiled from source and parts that were installed from Ubuntu packages.

Secondly, what's the make/model of your TV card and is it being recognised correctly by the LinuxTV drivers ("dmesg | grep card=")?

---

### Post by stumpy on 2007-03-24
I installed the driver according to the comprehensive sound problems guide, to try and get audio from the card

I got an unbranded card unfortunately (cheapo ebay job), its just being picked up as SAA7134 in LinuxTV

---

### Post by Jose Catre-Vandis on 2007-03-24
As josesanders says, you may need to connect your TV card audio output to your line/CD input to get sound running - I had to as it just wasn't making its way through the PCI interface. This should be one of those CDrom to sound card connectors, but there are also two types, 4 wire and three wire. I needed a three wire one to get both channels working.

Are any other sound devices showing up in Mixer Settings/Devices. (SAA7134 - Alsa Mixer  is what I have). If so check if the slider levels and On/Offs are set correctly and try different combinations of the switches. You may also need to do some work to get "multiple sound cards " running at the same time?

Run some commands to give you info about your card:

```
sudo lshw
```
```
lspci -v
```
```
lsmod
```
```
dmesg
``` (after boot)

In dmesg you should see how well you card is loading, and get some info about card and tuner. Try just choosing a card type as very often the system will auto select the tuner type.

---

### Post by Goodson1974 on 2007-03-25
Hi guys

Sorry to barge in, but i'm rather new to Ubuntu and have failed miserably to get my saa7134 tv card to show video let alone sound!

Is there any idiot proof guides as to the set up of these cards?

---

### Post by Dubstar_04 on 2007-03-25
Hey guys,

 I'm using a compro saa7134 hybrid tv card and i have managed to get both analog and dvb to work really well.

Follow this guide to install the drivers needed:

```
http://www.linuxtv.org/wiki/index.php/How_to_install_DVB#Solution_for_new_kernels_.282.6.29
```

 you  will need to do a complete shut down and boot before the modules and drivers begin to work. 

You may need to do insert the modules manually as follows:

```
 sudo modprobe saa7134-dvb
```

or if just analog

```
 sudo modprobe saa7134
```

if you need to manually insert the modules after every boot, add the module to the modules list as follows;

```
 sudo gedit /etc/modules
```

and add the saa7134-dvb or saa7134 under the lp entry.

If you continue to experinece problems with your cards sound you may need to specify which order the modules are loaded for each sound enabled device.

This is done as follows:

in terminal type lsmod and look to see what modules are used for each device.

Mine are as follows  

1. intel8x0              (on board sound)
2. saa7134-alsa      (Tuner card)

 run 

```
 sudo gedit -w /etc/modprobe.d/alsa-base
```

Edit the alsa config by adding the sound devices AT THE BOTTOM and leave the rest intact. My added section looked like this: 

options snd-intel8x0 index=-1
options saa7134_alsa index=-2

This makes the motherboard sound have priority over the tv card sound and made everythig work in mythtv!!

I do believe this has been causing me problems with the system freezing at boot and if the same happens to use please let me know.

I hope this helps relieve your frustration!

Dubstar

EDIT: I changed my HDD today because it started to get really noisy, and the freezing problem seems to be cured!!  Therefore the above guide should work perfectly for you!!

---

