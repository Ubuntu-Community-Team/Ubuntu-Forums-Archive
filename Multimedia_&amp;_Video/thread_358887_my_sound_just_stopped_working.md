---
title: "my sound just stopped working"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by klep on 2007-02-11
hello, 

today my sound stopped working. When i open amarok it says "xine was unable to initialise any audio drivers". alsamixer doesnt work presumably for the same reason. 

When i boot up the PC it still plays the little bongo sounds. The only thing i've changed since it was all working is I did this:

apt-get install ssh

thats it. I dont see how that could have affected my sound. I've had a quick search through the forums but could only find one relevant post that had no replies. I'm at a bit of a loss as to where to start trying to solve this to be honest (sound has always "just worked" with no intervention from me).


Cheers

edit: i've been through a bit of the comprehensive sound problems guide. With aplay -l i get :

aplay: device_list:221: no soundcard found...

but i can see it with lspci -v

sudo modprobe snd-emu10k returns nothing and changes nothing.


now im stuck

---

### Post by klep on 2007-02-12
bumping this as the problem remains...

does anyone have any suggestions?

---

### Post by klep on 2007-02-12
hello, 

i've been through the comprehesive sound guide now. this is my results:


With aplay -l i get :

aplay: device_list:221: no soundcard found...

but i can see it with lspci -v:

05:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 1001
        Flags: bus master, medium devsel, latency 32, IRQ 7
        I/O ports at 9c00 [size=64]
        Capabilities: <access denied>



sudo modprobe snd-emu10k
this command used to do seemingly nothing at all. now that ive been through the whole guide it hangs. 


I went through "Getting the ALSA drivers from a *fresh* kernel" part of the guide. it did not help and it did remove gdm and ubuntu-desktop as warned.


I went through compiling drivers Using alsa-source and this did not work.


i really have no idea where to begin now.

anyone with any suggestions?

---

### Post by tripmix on 2007-12-29
This just happend to me too, it worked perfectly till I rebooted tooday. Now there is no sound and no way of loading it. I'm starting to think it's broken or something but I just got this mobo. I don't get any errors or anything running alsaconf, seems to work fine. But alsamixer or any mixer has no slideres or anything like they used to. And there is no sound working anywhere.

Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2) (hda-intel)

---

