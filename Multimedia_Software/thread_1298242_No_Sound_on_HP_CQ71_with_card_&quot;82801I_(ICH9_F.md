---
title: "No Sound on HP CQ71 with card &quot;82801I (ICH9 Family) HD Audio Controller&quot;"
date: 2009-10-22
forum: Multimedia Software
---

### Post by bigmasterdenis on 2009-10-22
Hi Folks,

I'm trying now for days to get sound working on my laptop (HP CQ71-205SG / Ubuntu 9.04). Sound from headphones works but not from speakers. I have already installed the newest ALSA.

**lshw** says:
```

...
*-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

...

```and 
**aplay -l **says:
```

Karte 0: Intel [HDA Intel], Gerät 0: STAC92xx Analog [STAC92xx Analog]
Sub-Geräte: 0/1
Sub-Gerät #0: subdevice #0

```So the sound card seems to be recognized correctly.

The codec is IDT 92HD75B2X5.

I've tried editing /etc/modprobe.d/alsa-base.conf as suggested in many other forums... But still NO SOUND.

Hhm... what else can I do???
Thanks for help!

---

### Post by pgar23 on 2009-10-22
Having the same problem with Toshiba Satellite M305-s4848 with product: 82801I (ICH9 Family) HD Audio Controller. The sound suddenly quit working.

---

### Post by Ulysses361 on 2009-10-23
@Bigmasterdenis: please try this solution:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/81520](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/81520)

---

### Post by Ael Loro on 2009-11-21
Hello, [bigmasterdenis]("http://ubuntuforums.org/member.php?u=935295").

I've the same laptop and had the same trouble )
I spent few days for editing alsa-base.conf but it's not enough. And about hour ago i've found the solution! Yeah, it's work! (So, i'm realy happy now)

First: You should download the latest alsa snapshot from here: [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

Second: Extract downloaded "tar.gz" file.

Third: Open extracted folder in console.

Last: ```

#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo nano /etc/modprobe.d/alsa-base.conf
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]

```
After Last:  reboot. ;) 

Enjoy (=

So, this solution from here: [http://forum.ubuntu-nl.org/hardware-en-drivers/geen-speakergeluid-op-compaq-presario-cq71/?action=printpage](http://forum.ubuntu-nl.org/hardware-en-drivers/geen-speakergeluid-op-compaq-presario-cq71/?action=printpage)

---

