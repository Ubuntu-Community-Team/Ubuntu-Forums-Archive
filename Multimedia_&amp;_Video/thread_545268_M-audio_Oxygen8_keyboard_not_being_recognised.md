---
title: "M-audio Oxygen8 keyboard not being recognised"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by chrome101 on 2007-09-07
Hi peeps, I got a m-audio oxygen8 keyboard and i'm trying to get it to work with muse with not much luck. Jack is not recognising it, but all lights come on (on keyboard) and nothing happens. Does anyone know how to get it working or am I going to have to use another OS?

:confused:

---

### Post by schneertz on 2007-11-10
The instructions in this forum worked for me:
[http://www.kvraudio.com/forum/viewtopic.php?t=190021&view=previous](http://www.kvraudio.com/forum/viewtopic.php?t=190021&view=previous)

Note two things:

Before you start you need to install fxload

sudo apt-get install fxload

"sudo cd" doesn't work, just use "cd"

The location of usbmidi has changed. You can find it here:
[http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html](http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html)

Hope this works for you.

---

### Post by chrome101 on 2007-11-11
Thanks will try and let you know if it works.

---

### Post by chrome101 on 2007-11-16
tried both links and no joy. The first link started throwing up errors half way through. I have made sure all libs are installed, etc etc... 

I have tried 64Studio and everything works except wine and vsti instruments and there are a few buggy things... I have a friend who has debien and everything works with no problems... 

Might have to switch to that, cause there is no way I'm going out to buy another keyboard. Or failing that I'll just have to create a partition for window (which I really dont want to do) or totally switch to Mac (I have two machines). 

I dont see why I have to practically build a kernel just so I can write music... Not impressed!!!

---

### Post by Yellow Pasque on 2007-11-17
You could try completely removing ALSA and installing OSS. They claim that their drivers don't support MIDI, but yet it's listed as a supported device. I kind of doubt it works, but at least it's something easy to try before completely abandoning the Ubuntu ship. See my sig for OSS details.

---

### Post by chrome101 on 2007-11-17
I have tried practically everything and I just end up loading all sorts of drivers and clogging up the machine... I havent given up yet and I will give the Howto a go, although there are other things on the require ALSA, thanks anyway

---

### Post by drPJ on 2008-01-22
Hi,

 I followed the instructions here 

[https://bugs.launchpad.net/ubuntu/+source/midisport-firmware/+bug/88923](https://bugs.launchpad.net/ubuntu/+source/midisport-firmware/+bug/88923)


 My oxygen 8 now works fine.

---

