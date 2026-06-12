---
title: "Redirecting sound output?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Mariane on 2010-01-21
Hi, 

Is there a simple way to redirect sound output? I watched a movie yesterday with vlc and I had to listen to the sound out of the laptop speakers. This is never loud enough so I missed half the dialog. I had tried pluging in headphones but it just said "jack server not found" or simply ignored them. 

I tried fiddling with the drivers

Re-install:
```

sudo apt-get --purge remove linux-sound-base
sudo apt-get install linux-sound-base
sudo apt-get install alsa-base
sudo apt-get install alsa-utils

```

Re-build:
```

sudo apt-get install module-assistant
sudo module-assistant a-i alsa-source

```

Make sure it's taken into account:
```

sudo dpkg-reconfigure kdm-kde4

```

And reboot. 

It didn't help. 

I am also sometimes using a headphone with an integrated sound card which plugs into a usb port and this is a real nuisance to get to work as I have to modify some file in a directory with the sweet name of modprobe.d and reboot each time. 

I would like a program which would allow me to say "send the sound to the jack port" or "send the sound to the usb port number 3" or "send the sound to the laptop speakers" or "don't send out any sound at all" without rebooting. And without trying to detect the device because the detection may fail, just trust me that the device is there. 

Does such a program exist, please? 

Mariane

---

### Post by VertexPusher on 2010-01-21
> **Mariane said:**
> I had tried pluging in headphones but it just said "jack server not found" or simply ignored them.
What is "it"?

Headphone jacks can be enabled/disabled using alsamixer.

---

### Post by Mariane on 2010-01-21
"It" is the computer terminal from which I had launched vlc. 

alsamixer is not working, it (still the terminal) says:
alsamixer: function snd_ctl_open failed for default: No such device

```

say tee

```

duplicates the sound and it comes out as "teetee"


Mariane

---

### Post by Mariane on 2010-01-28
bump

---

### Post by sports.car.guy on 2010-01-28
> **Mariane said:**
> "It" is the computer terminal from which I had launched vlc. 

alsamixer is not working, it (still the terminal) says:
alsamixer: function snd_ctl_open failed for default: No such device

```

say tee

```duplicates the sound and it comes out as "teetee"


Mariane

That can be because it is trying to access a device that is not primary. Does this computer have an HDMI port on it? If so, it's sound device could be taking preference over the actual sound card.

---

### Post by Mariane on 2010-06-07
I don't know. According to this:
[http://en.wikipedia.org/wiki/HDMI](http://en.wikipedia.org/wiki/HDMI)
an hdmi looks just like a usb port. 
How can I tell the diference? 

Mariane

---

