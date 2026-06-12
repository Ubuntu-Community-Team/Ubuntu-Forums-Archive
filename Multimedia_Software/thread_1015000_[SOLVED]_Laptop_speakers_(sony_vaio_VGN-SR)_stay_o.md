---
title: "[SOLVED] Laptop speakers (sony vaio VGN-SR) stay on when headphone in use"
date: 2008-12-18
forum: Multimedia Software
---

### Post by SerpicoUK on 2008-12-18
Hi all,

First time trying linux and I've been very impressed that Ubuntu gave me 99% functionality straight out of the box. The one thing that appears not to work correctly is that my laptop speakers stay on when I plug in my headphones (which also have sound through them).

I have a new Sony Vaio VGN-SR19VN (using Centrino 2 if that makes a difference):

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

From my forum searches I've tried the following:

Removed and then re-installed alsa (also had to re install gdm and ubuntu-desktop)

Problem was not rectified.

I've also amended the alsa-basic file with:

options snd-hda-intel model=auto

I also tried

options snd-hda-intel model=vaio position_fix=0

(I rebooted after each amendment)

Neither worked.

I was just wondering if there was anything else I could try.

Although, as this is only a minor annoyance and as I'm not very experienced I don't want to try anything that significantly risks breaking the 99% in trying to get the 1% to work!

Oh - great forum/community by the way.

Serp

Additional info:

aptitude show alsa-base

Package: alsa-base
State: installed
Automatically installed: no
Version: 1.0.17.dfsg-2ubuntu1
Priority: optional
Section: sound
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 418k
Depends: lsof (>= 4.64), module-init-tools (>= 3.2.1), linux-sound-base
Recommends: alsa-utils
Suggests: apmd (>= 3.0.2-1), alsa-oss
Conflicts: alsa-utils (< 1.0.9a-4), discover (< 2.0.7-1), discover1 (< 1.7.3),
           lsof-2.2 (< 4.64), modutils (= 2.3.20-1)
Provides: alsa
Description: ALSA driver configuration files
 This package contains various configuration files for the ALSA drivers.

---

### Post by wudsta on 2008-12-18
mute the front speakers in alsa mixer, make sure headphones is ticked in the switches tab. I have a Vaio and had the same issue - this resolve it. :)

---

### Post by atomizer on 2008-12-18
on my hp dv7-1110ed I had a simular problem...

Anwser was as easy as:

open mixer control, and pull faders "front" down

(seperate volume-control for headphones and speakers)

I use pulseaudio for my sound

---

### Post by SerpicoUK on 2008-12-18
Thanks for your speedy replies. That would be a viable work around (and one I will use) but is there a way to actual solve the problem?

i.e to get the system to mute the front speaks when I plug my headphones in?

If not - I wonder if it's possible to set up a quick key or button to mute the front speaks? That would be a bit more efficient than opening up the sound console each time.

Serp

---

### Post by SerpicoUK on 2008-12-21
Just thought I'd update this after I found the solution else where on the web:

Edit the file:

/etc/modprobe.d/alsa-base

To include this line at the end:

options snd-hda-intel model=sony-assamd

Headphones now work in stero rather than mono and cut the laptop speakers when in use.

Cheers,

Serp

---

### Post by ech0s7 on 2008-12-22
Hi, i have the same notebook sony vaio (sr19), i would know if to you works internal mic (with alsa)...
Thanks You so much, and Merry Christmas to all!

---

### Post by SerpicoUK on 2008-12-22
I don't use microphones but a quick try indicates that neither my internal or external mic options work.

But I've found that if I amend the line to include enable=1 I can get the external mic socket to work. 

options snd-hda-intel enable=1 model=sony-assamd

Will report back if I find something that works for the internal mic.

Serp

---

### Post by fernandoch on 2009-09-09
Can you adjust the brightness with Fn keys?

Can you also use the top buttons on the keyboard?

---

### Post by dragupl on 2009-09-09
sorry to bump such an old topic but i've searched the forums for similar problem (sound in headphones and speakers simultaneously) in Sony Vaio VGN-NS31S and finally i found this topic, applied the solution with options snd-hda-intel enable=1 model=sony-assamd and it works perfectly :) thanks!

---

