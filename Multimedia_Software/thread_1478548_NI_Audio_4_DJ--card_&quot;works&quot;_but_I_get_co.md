---
title: "NI Audio 4 DJ--card &quot;works&quot; but I get constant hissing and clicking noises"
date: 2010-05-09
forum: Multimedia Software
---

### Post by dumdidum on 2010-05-09
I use a Native Instruments Audio 4 DJ as my main sound card. It's an external USB audio interface. The problem described below occurs on Ubuntu 10.04 x86-64 (installed via standard desktop CD). If this post misses any relevant info, please kindly point it out (I'm new to Ubuntu).

The installer detected the card just fine. I selected the Audio 4 DJ in Preferences ---> Sound as my default card for sound output (the installer had set my internal audio as the default card).

Now, the card plays sounds as well as music. However, there are really loud hissing sounds and clicking noises which basically render the card unusable in practice. These "kkrrck" sounds stop about a second or two after I terminate playback. LEDs on the card light up correctly as they would under Windoze.

Any thoughts?

EDIT: and btw, I am x-posting this here after getting no help on the NI forums ([this]("http://www.native-instruments.com/forum/showthread.php?t=109201") is the thread).

---

### Post by cchhrriiss121212 on 2010-05-10
I have heard pulse causes this kind of unwanted noise, but if you are using lucid you cannot remove it without taking away ubuntu-desktop. You could try: disabling your onboard sound from bios; removing any other devices using the same usb port; or upgrading alsa.

---

### Post by dumdidum on 2010-05-10
> **cchhrriiss121212 said:**
> I have heard pulse causes this kind of unwanted noise, but if you are using lucid you cannot remove it without taking away ubuntu-desktop.

Thanks for your suggestions!

> 
You could try:

> 
disabling your onboard sound from bios

Disabling on-board sound makes no difference.
> 
removing any other devices using the same usb port

No other device is using the same USB port.
> 
or upgrading alsa

OK, will look into that.

Does anyone have other suggestions?

Any users of the NI Audio 2 DJ/Audio 4 DJ/Audio 8 DJ here that got their audio interface to work properly in Lucid?

---

### Post by dumdidum on 2010-05-12
bump

---

### Post by snapback77 on 2010-11-05
I am having a similar problem with my hrt music streamer II USB Dac especially when I move large files from my external HDD to my computer AMD 64 like yours. No noise when I use the internal sound card. It has to be related to USB interface, nes't pas?  Another thing, the volume of the noise stays the same if I lower the volume of music.  I like the suggestion of going to the bios and shutting down any computer sounds which this sounds like to me.  I will let you know if I discover the answer to this annoying problem.

---

### Post by snapback77 on 2010-11-11
I do not get the hissing sound.  Loud white noise strikes like lighting.  Very annoying if you are digging music.  Not happening with rhythm box.  It happens with Potamus (a very good player that does 24/96 files perfectly. Simple drag and drop listening.  But, that pop! Random.  It does not happen with my internal card which is inferior to my usb dac.

---

### Post by AndrewBorg on 2010-11-29
Hi,

I had this problem lately, But today while I was downloading some software for my beloved Ubuntu Maverick I noticed this constant distortion.

What I did was removing the Ethernet Cable and browse the Internet via Wi - Fi

Hope it Helps

Good Luck
Andrew :D

---

### Post by snapback77 on 2010-11-29
The clicking is mostly random.  I can force it to occur by opening screen saver and previewing one of the them.  Weird.  It occurs more often when playing 96/24 music files now in GNOME MPlayer thanks to Ubuntufreak Comprehensive Sound thread.  I really sounds better.  I just cannot use a screen saver. weird.  I hope I don't blow a tweeter.  Thanks for help.

---

### Post by detrate on 2010-12-19
I'm having the same problem.  Things were working great out of the box initially... but after my system crashed due to a power outage, it's started hissing.  It seems to be affected by the ethernet cable as Andrew had noticed was effecting the crackle.

If I unplug the ethernet, I have no interference what-so-ever.  However, this is a desktop machine... and I'd prefer to have it connected via a wire.

I've been going through my configs to try and get to the bottom of this but no luck yet..  I can't think of anything else that changed to cause this.

---

### Post by cchhrriiss121212 on 2010-12-19
You could try changing the port you have it connected to, a different USB controller might not suffer from the interference and most computers have more than one.

---

### Post by detrate on 2010-12-20
> **cchhrriiss121212 said:**
> You could try changing the port you have it connected to, a different USB controller might not suffer from the interference and most computers have more than one.

I have tried all the ports, same issue.

I've tested the soundcard on a windows computer, no issue.

I've ripped out pulseaudio, issue persists.

I reinstalled pulseaudio, issue persists.

I reinstalled the "ubuntu-desktop" package, issue persists.

My onboard sound works without problems.


any other ideas?

---

### Post by snapback77 on 2010-12-23
In my opinion this is a problem with 10.04.  I went back to 9.10: problem gone and I am delighted with my sound.

---

### Post by Timjh on 2011-02-26
I'm running into the same problem with my new HRT music streamer II USB Dac and Ubuntu 9.10. Has anybody found a workable solution?

---

### Post by snapback77 on 2011-03-02
Apparently not.  I have the MS II also and I have found if I deactivate the Nvidia Nuforce 6150 video card's driver the problem goes away for the most part. However, I am limted to 800x600 resolution.  It also helps to turn off the screen saver. Are you using MPD? It sound much better to me, more resolution, less noise, just more realistic.  
Hope we find the answer.


HP AMD 6400 desktop. MPD+Sonata. HRT MS II.  Dell W4200HD. NAD 744 AVR.  Paradigm Studio 40.

---

### Post by d0m1nation on 2011-08-28
I'm experiencing the same issues on 11.04 natty

Really wish there was an solution to this, i don't want to buy a new soundcard..

---

### Post by nfo on 2011-10-06
i had the same issues with ubuntu natty 11.04
following workaround works for me:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get-update
sudo apt-get install linux-alsa-driver-modules-2.6.38-11-generic
reboot
```

---

