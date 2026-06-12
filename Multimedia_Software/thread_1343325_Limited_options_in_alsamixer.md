---
title: "Limited options in alsamixer"
date: 2009-12-01
forum: Multimedia Software
---

### Post by rdd37 on 2009-12-01
Hello,

In troubleshooting another issue ([here]("http://ubuntuforums.org/showthread.php?t=1340308&highlight=xvidcap")), I found that I needed to enabled the 'mix' option for my soundcard in alsamixer. However, as shown in the screencap below, alsamixer does not include a 'mix' option on this system -- as a matter of fact, it only has two options total.
[IMG]http://storage.bertd37.fastmail.fm/files/alsamixer.png[/IMG]

Is it possible that my soundcard is not sufficiently new/powerful enough to have this option? 

The soundcard details are:

(from aplay -l)
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help greatly appreciated.

---

### Post by spiderbatdad on 2009-12-01
not really sure but a couple of options might be:
check the file alsa.conf in /usr/share or /usr/share/alsa and remove the line /usr/share/alsa/pulseaudio.conf
the other suggestion would be download and install alsa-firmware-1.0.20
install it with
./configure --with-cards=all
make
sudo make install

---

### Post by rdd37 on 2009-12-02
> **spiderbatdad said:**
> 
check the file alsa.conf in /usr/share or /usr/share/alsa and remove the line /usr/share/alsa/pulseaudio.conf

the other suggestion would be download and install alsa-firmware-1.0.20
install it

**spiderbatdad** - thank you for the suggestions. 
- unfortunately there are no occurrences of 'pulseaudio' in the /usr/share/alsa/alsa.conf file on this system:
~$ sudo grep -i pulseaudio* /usr/share/alsa/alsa.conf 
~$

- I will definitely consider installing the updated alsa firmware, but probably as a later resort.


I've taken a few more screencaps, in case they help. First, alsamixer view on another system that works well:
[IMG]http://storage.bertd37.fastmail.fm/files/alsamixer-II.png[/IMG]
One thing that stands out right away is that the 'Card' value lines up with the output of 'aplay -l' (as opposed to the problem system, where it reads simply 'PulseAudio').


The gnome-alsamixer view on the problem system:
[IMG]http://storage.bertd37.fastmail.fm/files/gnome-alsamixer.png[/IMG]
(note no 'mix' checkbox available)

And the gnome-alsamixer view on the working system:
[IMG]http://storage.bertd37.fastmail.fm/files/gnome-alsamixer-II[/IMG]
(note the 'mix' checkbox available)



Again, any help greatly appreciated.

---

### Post by rdd37 on 2009-12-02
^ bumping 
(because I'm starting to think/hope that I've made a stupid mistake somewhere, which would explain why the problem system lists card as 'PulseAudio', and doesn't have many options available)

---

