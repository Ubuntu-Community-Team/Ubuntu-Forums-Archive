---
title: "Sound stopped working from laptop speakers"
date: 2011-11-12
forum: Multimedia Software
---

### Post by NewReformist on 2011-11-12
So, I have no idea what actually happened because just a couple of days ago everything worked just fine.

Suddenly my sound from my laptop speakers are not working at all, but the sound from the headphones jacks still works just fine.

I did have some problem with Spotify (run in Wine) which crashed a couple of times, but somehow I don't see the connection.

The problem might also have been some update, because I did run the updates at some time.

I have Ubuntu 11.04 (I run it in classic environment). I use an Dell Studio XPS 1640 and  have an integrated HDA Intel soundcard.

When I add (in terminal):

[B]sudo gedit /etc/modprobe.d/alsa-base.conf
[/B][B]
,[/B]I already have the line:  *options snd-hda-intel model=dell-m6* added in the end of that document, and had so for a long time.

So I try to "save" that document again (to see the reaction) and get the following error message 

in terminal: 

(gedit:216 **: Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed:
Failed to create file "/root/.local/share/recently-d.xbel.8WXJ4V": No such file or directory

---

### Post by NewReformist on 2011-11-14
Anyone got a clue what I could look for?

I'm totally clueless here. There's still no sound from the speakers, but still working fine via headphone.

---

### Post by MoreOrLess on 2011-11-14
Try booting an older kernel (if you have it). There are a bunch of "my sound suddenly stopped working" threads in the past few days.

---

### Post by inobe on 2011-11-14
type **alsamixer** in terminal, your front speakers may be muted.

or install pulseaudio volume control and tinker with that, i'm certain it's something simple as that.

---

### Post by NewReformist on 2011-11-14
> **MoreOrLess said:**
> Try booting an older kernel (if you have it). There are a bunch of "my sound suddenly stopped working" threads in the past few days.

I did try this already and it states that the speakers are on 100 (which I guess mean they are fully on).

---

### Post by NewReformist on 2011-11-14
> **MoreOrLess said:**
> Try booting an older kernel (if you have it). There are a bunch of "my sound suddenly stopped working" threads in the past few days.

What do you mean by booting an "older kernel" (I'm sorry but I'm still quite new beginner in this).

---

### Post by inobe on 2011-11-14
> **NewReformist said:**
> What do you mean by booting an "older kernel" (I'm sorry but I'm still quite new beginner in this).

when you start the system you hit escape, you will be presented with boot options, choose one that is not safe, and is a different kernel version.

---

### Post by NewReformist on 2011-11-15
> **inobe said:**
> when you start the system you hit escape, you will be presented with boot options, choose one that is not safe, and is a different kernel version.

I see. But this won't harm the files etc. I already got on my computer?

So if the sound would work (for some reason) while doing this, would I have to do this all the time then and never run my system "normally"?

---

### Post by NewReformist on 2011-11-16
I'm thinking of installing Windows or re-install the whole system if I can't find out how to fix this :(

---

### Post by Andrew_D on 2012-01-12
Old post, but, in case anyone stumbles upon thee :p..

Are you switching between Analog headphones/analog speakers in the default Ubuntu system settings? 

Noticed that when i didn't switch back to A.S, my laptop speakers played, then stopped randomly mid music. 

Probably best to keep then om analog speakers if sound quality is not a big deal to ya'.

But i bet it is :D. T Here is a improved difference in the analog headphones setting. A little cleaner bass i want to say, but then again it depends on the headphones or music!

---

