---
title: "Only one sound source at a time?"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by mark2741 on 2006-06-09
I'm using a external USB SoundBlaster Extigy sound unit for sound with Dapper. I  just noticed that only one sound source can play at a time. In other words, if I'm playing Rhythmbox and at the same time I go to a webpage with sound, or I play a video clip or something, the sound won't come through. I have to first stop and close rhythmbox (or whatever app first started playing sound) in order for something else to play.

I don't remember ever noticing this in the few days I was using Breezy (I switched to Ubuntu a few days before the Dapper release, so I'm a newbie for sure). I also don't remember it being a problem when, until last week, I was using an internal PCI sound card. The sound from that was fine but something was up with that card because it seemed to lockup my computer once in a while - windows and ubuntu, so I ditched it for this USB Extigy I had laying around. I'll post another thread about not being able to get the controls on the Extigy to work : (

mark

---

### Post by jazzmuzik on 2006-06-09
Try using the alsa sound architecture.

---

### Post by mark2741 on 2006-06-09
[QUOTE=jazzmuzik]Try using the alsa sound architecture.[/QUOTE]
I *think* I'm using that already? When I right-click on the little speaker icon in the top-right of Gnome and select preferences, it says "SoundBlaster Extigy (Alsa Mixer).

---

### Post by jazzmuzik on 2006-06-10
Hmm. I'm using alsa and I can hear multiple sources...

---

### Post by mhs on 2006-06-13
[QUOTE=mark2741]I'm using a external USB SoundBlaster Extigy sound unit for sound with Dapper. I  just noticed that only one sound source can play at a time. 
mark[/QUOTE]

i have the same problem ! :( 
plz help!

---

### Post by Nuld on 2006-06-19
Unfortunately, I have the same annoying problem. I have an Acer Travelmate 8003 laptop. Any advices are appreciated :)

---

### Post by mrf76 on 2007-11-02
Thanks. After setting my audacious crossfade plugin to use alsa output (and others progs too) I'm able to play multiple sounds at a time (kaffeine, audaciuos... gaim) without problem. Gutsy on Thinkpad Z60m.

---

### Post by pkkid on 2008-05-31
I have the same problem, still looking for a solution.

EDIT: A little more research and I found a solution that works for me here:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

> **Firefox/Flash and PulseAudio**

Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio.  *Update: libflashsupport is available in Hardy as a package via the synaptic package manager.*

Go to logicalnetworking.net to download the libflashsupport .deb and install it:
>> wget [http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb](http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb)
>> sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb

Restart Firefox to enable simultaneous audio output from flash and other sources (rhythmbox, totem, etc). 

---

