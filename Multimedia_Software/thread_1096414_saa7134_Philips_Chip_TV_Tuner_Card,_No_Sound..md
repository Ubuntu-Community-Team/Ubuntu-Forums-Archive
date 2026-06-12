---
title: "saa7134 Philips Chip TV Tuner Card, No Sound."
date: 2009-03-14
forum: Multimedia Software
---

### Post by wbee on 2009-03-14
Hello,

After much discussion,cussin,and percussion,I got tvtime to read the card,for video.

(MSI TV Anywhere Plus Card,saa7134 Philips chip,card number 82,tuner number 54)

Now,how do I get audio?

-------------

Thank you.

---

### Post by steefjeqv on 2009-03-15
Hi,

Install the alsamixergui package, open TVtime and select a channel.
Now open alsamixergui and just increase the volume (or switch off mute) of all the available sliders (one by one).

Sorry for this elaborate way of solving your issue but I can't remember which input needs to be activated.

One other thing, sometimes you need to set the correct TV standard (PAL-B or I etc...) before Tvtime works properly.

Greetings,
Steven

---

### Post by wbee on 2009-03-16
steefjeqv,

I tried that and it did not work.

There were two available sliders. The one marked "master" worked. That is I could mute or un mute it. I could get the sliders to work.

The one marked "capture" did not work at all.

May I infer from that,logically enough,that the sound is not "captured"?

---------------

Thank you though Steven,
Woody

---

### Post by wbee on 2009-03-16
Hello Again,

I found this site:

[URL="http://www.techsupportteam.org/forum/linux-alternative-os/5417-saa7134-pci-tv-tuner-cards-linux.html"[/URL]

---------------------

Here is a relevant part from it:

Audio

Starting from 2.6.17 kernel, Linux provides audio device DMA driver:

modprobe saa7134-alsa

The sound must be directed from card's audio device to the main audio device:

sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp -w -r 32000 /dev/dsp &

***********Setting it up in Debian

Add a file /etc/modprobe.d/saa7134 with the following contents:

options saa7134 card=65 tuner=54
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

Reload the modules for the card and tuner id to take effect:

rmmod tuner saa7134-alsa saa7134
modprobe saa7134

Unload the module by doing modprobe -r saa7134 or rmmod saa7134 and the load module by doing modprobe -v saa7134. You should see it is using the options you added in the modules.conf or modprobe.conf.

gksu gedit /etc/modules /etc/modprobe.d/options /etc/modprobe.d/aliases

update-modules

Use the following script to start tvtime and audio forwarding at the same time:

#!/bin/sh
sox -q -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp -w -r 32000 /dev/dsp &
soxpid=$!
sleep 0.5
tvtime
kill $soxpid

---------------

--I know to put my card and tuner number in correctly.

--May I leave the sleep line out of the last entry?

--rmmod tuner saa7134-alsa saa7134
modprobe saa7134  (Is that two commands or one command?)

--
gksu gedit /etc/modules /etc/modprobe.d/options /etc/modprobe.d/aliases  (Is this what I should see or is a separate command?))


--Being a rookie at this,if this does not work,am I liable to do any damage I can't undo?

--I'm posting from work,on my lunch break,so I'll try this later.

-----------

Thank you,
Woody

---

### Post by steefjeqv on 2009-03-18
Hi,

Sorry for the late reply.

Before you try out the link you've mentioned, just try the following command in terminal :

sudo modprobe saa7134-dvb

or 

sudo modprobe saa7134-alsa


--May I leave the sleep line out of the last entry? - I really don't know.

--rmmod tuner saa7134-alsa saa7134
modprobe saa7134 (Is that two commands or one command?)
These are two commands. rmmod removes installed drivers and modprobe activates the drivers.

gksu gedit /etc/modules /etc/modprobe.d/options /etc/modprobe.d/aliases (Is this what I should see or is a separate command?))
With this command you're going to start up gedit (text editor) in order to edit the files mentioned.

However, all of this shouldn't be necessary because all of these drivers should be loaded correctly at boot.

You can check if these drivers are actually used by typing this command (terminal) :

sudo lsmod

One other thing, does your TV card have an internal audio connector ?

Greetings,
Steven

---

### Post by wbee on 2009-03-20
Steven,

Thank you.

I'll keep searching.

Yes,it has an audio out that I can connect to the sound card.

The audio chip has a function where,(in Windows XP) whereby you can play the video,and select between an analog audio from the tv tuner card,or the sound card itself. In the later instance,you can,for example,watch a sporting event and listen to a compact disk or a streamed fm station at the same time.

I'm sure there is a way to do this,but I have not figured it out yet.  I'm reading tutorials as time permits.

----------------

Thank you
Woody

---

### Post by seiyachan on 2009-05-02
I am able to get the sound with the following command:

mplayer tv://$channel -tv driver=v4l2:device=/dev/video0:chanlist=australia:channel=10:channels=2-ABC,7-Seven,9-Nine,10-Ten,28-SBS:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=PAL:tdevice=/dev/vbi0:tformat=1:tpage=801

---

### Post by longi on 2010-03-05
> **seiyachan said:**
> I am able to get the sound with the following command:

mplayer tv://$channel -tv driver=v4l2:device=/dev/video0:chanlist=australia:channel=10:channels=2-ABC,7-Seven,9-Nine,10-Ten,28-SBS:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=PAL:tdevice=/dev/vbi0:tformat=1:tpage=801


I solved the audio problem by simply purchasing an audio jack with rca inputs and a stereo output at the back.  Plug the audio from the composite into the audio jack rca red and plug your speaker into the stereo output at the back of the jack.  Then plug the audio jack into the mic in of the laptop.  The last is necessary for recording.  I record tv with gtkrecordmy desktop and it records perfectly:P

---

### Post by dealcorn on 2010-03-24
I can not use the command
```
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp -w -r 32000 /dev/dsp &
```
because "-w" is an invalid option.  What is "-w"?  I do not see it listed in the manual page.

---

### Post by Chronos6 on 2010-07-04
Amazing that it is still not fixed..

This works for me:
sox -c 2 -s -2 -r 32000 -t ossdsp /dev/dsp1 -t ossds

---

### Post by Chronos6 on 2010-07-04
This should work: sox -c 2 -s -2 -r 32000 -t ossdsp /dev/dsp1 -t ossds

---

