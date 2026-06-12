---
title: "es1371 no sound"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by cosine on 2005-10-14
I can't get sound from my soundblaster sound card.  I've already tried checking the other posts on this forum but none of them seem to have the problem I'm facing.

The device shows up on lspci:

0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)

lsmod gives me:

snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

There's a red x at the volume control, but when I double click on it, I get "No volume control elements and/or devices found."  I can't open Preferences.

When I use the Multimediea Systems Selector, I get "Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'" no matter which I choose.  Replace the ESD bit with whatever option it is.

Totem cannot play any music file.  I get the message "There were no decoders found to handle the stream, you might need to install the corresponding plugins"

Synaptic shows that gstreamer plugins are installed.

I'm using ubuntu 5.10 and I'm a linux newbie so please go slowly.  Thanks a lot.

---

### Post by cosine on 2005-10-15
Does anyone have any ideas? If more information is needed just ask and I'll provide it.

---

### Post by humps_buatbu on 2005-10-17
I'm having the exact same problem with my sound card (same card).  It worked beautifully on Hoary, but for some reason on Breezy it doesn't.....

---

### Post by shaggy3zx on 2005-10-17
I am having this problem with an older ensoniq ISA card.

It shows in device manager as 

PNP DEVICE (ENS1010)
PNP DEVICE (ENS2020)

any help?  I am so lost on this one. :confused:

---

### Post by sjeapes on 2005-10-18
Hi,

I'm having the same problem too. With the same card :sad:

---

### Post by tooms on 2005-10-20
I had the same problem, added my user (the one I'm running gnome with) to the 'audio' group, everything worked fine after that.  I had no problems with my ES1371 until I started messing with the groups my user was in, also took away all my root access from gnome.  Glad there's google to help me get my system all fixed and working great again!

---

### Post by cosine on 2005-10-23
My user is allowed to use audio devices.  Same problem.

---

### Post by sjeapes on 2005-10-23
Yup, me too. All the users are in the audio group but I still get no sound.

It appears that /dev/dsp does not exist on my breezy system
Also the only file that shows up in /dev/snd is 'timer'

In Hoary (where my sound works) /dev/dsp exists and I get controlC0, midiC0D0c, pcmC0D0p, pcmC0D1p and timer files.

Does that help at all. Why are these files not being created?

---

### Post by Rumpty on 2005-10-26
Due to something I did, I lost sound, hence came to this thread. I'm using the same sound card.
What I did was to cut short hotplug during the booting process, using Ctrl-C, because I didn't want to wait 30 seconds for it to do whatever it was doing. As a result, my soundcard stuff did not appear in lsmod, and the alsamixer wasn't there either.  So, hotplug does more than I realise - is it looking at pci cards as well as USB etc?

Sorry that this is not directly helping with the above problems that you are having, but it is partly relevant. 

Still using Hoary here.

---

### Post by Mark Rose on 2005-11-13
[QUOTE=humps_buatbu]I'm having the exact same problem with my sound card (same card).  It worked beautifully on Hoary, but for some reason on Breezy it doesn't.....[/QUOTE]

I had exactly the same issue here, too. An upgrade from Hoary didn't work. A fresh install of Breezy doesn't work. It's most annoying.

---

### Post by served on 2005-11-16
Do you all have a ISA card?? 
I had the same problem with my SB16 with 4.10 it worked but not with 5.10.

So i used 5.10 and i wanted to buy a pci card, but i changed some settings in the BIOS : Plug and Play OS- set disable and Parallel port disable. I got that information from "foorum.hinnavaatlus.ee" but i think u cant understand that language ;) so i think the problem is in the boot loader and kernel and bios.
This new kernel blocks free ports ,dunno why, and thats why it doesn't work.

---

### Post by sjeapes on 2005-11-20
My sound card is  a PCI sound card.

I have a USB soundcard that I plugged in and it gets detected and works with no messing around in Breezy, the pci one still isn't detected with or without the usb sound card in. I can't really use the USB one as it only has optical outs so I'm still stuck.
I guess that proves that it should work and it's just having problems with that specific card :(

---

### Post by chrstoph on 2006-02-15
Had the same problem with es1371, all i did was use the oss module:

modprobe snd-ens1371
(if this works, you can add it to /etc/modules.conf)

then you might need to add group permissions on the audio device:
to keep the original group permissions just type: groups yourname
and then add the groups into the following command eg:

usermod -G user,admin,audio yourusername

then log off and log back in, you should be able to start the esd server through system-> preferences-> sound.

hope this helps. :)

chris

---

### Post by stupid_idiot on 2006-11-14
Once 'modprobe foo' gets you working sound, add the soundcard module to "/etc/modules" and reboot. I just had this problem. All the appropriate devices already belonged to group 'audio' but mplayer kept giving alsa-lib errors about not finding 'card 0' or something.
Prolly when root modprobes the card successfully the long aliases in /etc/modules.conf aren't being used, so the alsa software think there's no card. Probably, letting udev load the modules at startup fixed the problem, since that would use the alias bindings in modules.conf

---

### Post by sjeapes on 2006-11-14
Using mod-probe didn't appear to work, and the permissions weren't the problem

I solved this by adding
[FONT="Courier New"]**acpi=ht**[/FONT] to the boot options
This can then be added to the grub config file to apply this permanently

This thread might help
[http://ubuntuforums.org/showthread.php?t=140604](http://ubuntuforums.org/showthread.php?t=140604)

---

