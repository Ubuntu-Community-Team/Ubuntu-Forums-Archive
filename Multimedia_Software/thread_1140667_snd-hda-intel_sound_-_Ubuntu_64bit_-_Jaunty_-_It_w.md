---
title: "snd-hda-intel sound - Ubuntu 64bit - Jaunty - It worked!"
date: 2009-04-27
forum: Multimedia Software
---

### Post by davidfdr on 2009-04-27
Hello,

I found a lot of guys with same problem. 

After reading some threads here, I did the following things to make my sound works OK:

Laptop Model:
Gateway P-6831FX
Core2duo Xtreme 3ghz
4gb RAM
8800mGTS
Sound: IDT 92DT71B8X 
lspci -v:

```

...

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 0690
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

```

1 - put following lines on /etc/modprobe.d/alsa-base.conf
```

options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1

```

Note that my notebook is an Gateway, BUT i'm using model hd-m4 (HP DV laptops) because apears to have the same chipset (IDT 92DT71B8X)

The list of the supported models you can find on following place:
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

```

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP dv laptops

```

I've tried with some Gateway listed models, but none of them worked, so, i'll continue to use the hp-m4 model.

A strange thing happend after all configurations. I needed to put/remove the headphone jacket to turn on the laptop speakers. I think that is maybe because the model hp-m4 isn't complete compatible.

So, I hope it help.

best regards.

David

---

### Post by SeanBlader on 2009-04-28
I had begun to think that it wasn't going to ever get sound. I'd go through threads and think that I didn't want to try stuff because I didn't think it would work. Then I saw this one, and I just knew somewhere that the right line to the alsa-base.conf file would fix it, and in that list was the answer for my Adamo:

options snd-hda-intel model=dell-eq

Now to fix some of the actual sounds themselves since I actually have audio. Thanks for the link David.

---

### Post by quickyfant on 2009-04-28
Hi!

I had already thrown in the towel! I had tried every new tip, nothing! Thank you so much David, IT WORKED! Thanks!!

---

### Post by The Mad Mule on 2009-04-28
So it works, but we have to plug something into the headphone port, and pull it out to have the speakers start working?

---

### Post by babin on 2009-04-28
Hi
I gauss I have a same problem.
I have a Gateway T-6161 and I have Ubuntu 9.4 64bit on it.
You know, its speakers work well but I don't hear sound in headphone. I edit alsa-base like your said, but it still doesn't work. I test other model but it still doesn't work.

here is my Playback list

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by davidfdr on 2009-04-28
> **The Mad Mule said:**
> So it works, but we have to plug something into the headphone port, and pull it out to have the speakers start working?
Yes. It was a little strange, but after putting the righ line on alsa-config, and do the reboot, I had to do that.

---

### Post by davidfdr on 2009-04-28
> **babin said:**
> Hi
I gauss I have a same problem.
I have a Gateway T-6161 and I have Ubuntu 9.4 64bit on it.
You know, its speakers work well but I don't hear sound in headphone. I edit alsa-base like your said, but it still doesn't work. I test other model but it still doesn't work.

here is my Playback list

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Other thing that I hear the could work is pull the kernel option "irqpoll" on grub.

You may try that.

Go to /boot/grub/menu.lst
Fine the line kopt..
Put irqpoll on the end of the line.

I´ve found a thread on launchpad saying that.

---

### Post by mrbubblesort on 2009-04-30
Just for the record, this worked on my gateway 6860-fx. The mic always get re-muted when I close the volume control box, but it's useable.  Thank you very much!

---

### Post by arturhoo on 2009-05-01
Insert the following in /etc/modprobe.d/alsa-base.conf:
```

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
```

made the trick. 

I have an 6860FX laptop. Running 32bit jaunty on it.
Don't use the mic, so I can't really tell much about it.

Thanks to
mourngrym1969
from:
[http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway](http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway)

---

### Post by tantos on 2009-05-01
it works!
lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3607
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	Memory at dc500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

thank you very very much:popcorn:

---

### Post by babin on 2009-05-30
I still have this problem... I put different models in alsa-base.conf but it doesn't work for me... my headphone output doesn't work :(

---

### Post by gwyndyn on 2009-06-14
> **arturhoo said:**
> Insert the following in /etc/modprobe.d/alsa-base.conf:
```

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
```

made the trick. 

I have an 6860FX laptop. Running 32bit jaunty on it.
Don't use the mic, so I can't really tell much about it.

Thanks to
mourngrym1969
from:
[http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway](http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway)

Glory Hallelujah. My speakers work again. Thanks!

---

### Post by petedes5 on 2010-03-02
I give up.....


How do I know what sound model to put in? I have a gateway 6836 and i have no idea if i should change the model in the lines or not.

I put the lines in and it still does not work.:confused:

---

### Post by Trinity33 on 2010-03-02
anyone who got problem with sound and karmic or lucid fallow this tuto:

 [http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

when u update everything and your card still wouldn't work then:

[http://forums.opensuse.org/hardware/laptop/422949-acl1200-ich9-82801i-4-1-surround-sound-problem-2.html](http://forums.opensuse.org/hardware/laptop/422949-acl1200-ich9-82801i-4-1-surround-sound-problem-2.html)

and your card will work.

im new to ubuntu. was looking for solution to my acl 1200 and ati hdmi for long time couldnt make it work. this two websites helped me a lot. 

tested on acer aspire 5735
and msi gt725

---

### Post by petedes5 on 2010-03-02
what about alsa update on jaunty?

---

