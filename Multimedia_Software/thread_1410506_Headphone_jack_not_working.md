---
title: "Headphone jack not working"
date: 2010-02-18
forum: Multimedia Software
---

### Post by llueveYescampa on 2010-02-18
I just realize that when I plug in my headphones in my laptop, the sound in the laptop's speakers continues to play and I have no sound on the headphones.

Doing some research I learned that some people have had this or similar problems before, but I found no answer.

This is the output of the 'sudo lshw -C sound' on my system:

  *-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3000000-d3003fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:db100000-db103fff

Any help will be highly appreciated.

---

### Post by byStanderone on 2010-02-18
...sounds like a phone-jack problem to me,or perhaps the earphone plug does not fit right, try using another earphone with a plug that fits well.

---

### Post by llueveYescampa on 2010-02-18
No, it is not a phone-jack problem. In Windows everything runs as expected....

---

### Post by llueveYescampa on 2010-02-19
Partial Improvement...

The headpjone jack is working. I had to add  following lines to my /etc/modprobe.d/alsa-base.conf

The solution is not perfect, tough. When I plug in my headphones, the laptop speakers don't stop playing. At least I have the headphones working.


options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

---

### Post by mattaphore on 2010-02-19
I'm having the same issue on my HP tx2110us... I get sound playing out of both the laptop speakers and my headphones.

Pretty much defeats the purpose of using headphones :(

I'm pretty new to Ubuntu, so any help would be greatly appreciated :)

---

### Post by mattaphore on 2010-02-19
I found this in another thread, and I'll give it a shot:

> **willix said:**
> Ok I'm done, I finally have my sound working on my HP pavilion dv7 2150ez with Ubuntu 9.10 Karmic Koala; Both speakers are working and they switch off when I plug my headphones.

YEEEEEESSSSSSSSSS :popcorn:

So for the record here is what I did:

I updated my BIOS; that did not do the trick

I updated my alsa to version 1.0.21; that did not do the trick

I edited my alsa-base.conf and added the enable_msi=1 option: that did not do the trick

So I finally installed the alsa-driver-snapshot.tar.gz as described here 
[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

and edited the alsa-base.conf file and added
options snd_hda_intel model=hp-dv5

(and not options=hp_dv5 as I read in a few threads)

and that did it. 

The bottom line is; when everything else fails, read the doc!

It was right there under my eyes but read the section about dv7 ignoring the one about dvxx. When I tried the section about dvxx (dv7 is, afterall, a dvxx), everything fitted.

Next step: getting HDMI working...

I'll let you know if it works.

---

### Post by byStanderone on 2010-02-20
...simple things are getting complicated each day, had to catchup anyway.lol

---

### Post by jlh68 on 2010-05-09
My laptop headphone output quit working.  I have the "switch" clicked on for the head phones.  I checked the alsamixer and I cannot get the headphone slide to work, it stays at 00.  When I uncheck the headphone switch the alsamixer changes the headphone state.  I cannot figure out why the headphone will not output.

Realtek ALC883 Intel HDA

---

