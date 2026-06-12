---
title: "Absolutely No Bass with Ubuntu 13 and Conexant CX20641 (Dell Optiplex 390)"
date: 2013-09-11
forum: Multimedia Software
---

### Post by BigToe2010 on 2013-09-11
Hi,

As per the title.  After watching a couple of YouTube videos in my new installation of Ubuntu 13.04, it was very apparent that there is hardly any bass being passed through to the speakers at all.  In fact, it's almost like Ubuntu is treating my speakers as satellites, whilst reserving the bass for a sub-woofer channel that doesn't exist (the output on my Optiplex onboard audio is simple stereo).  I have it hooked up to an amp and bookshelf speakers that have a reasonable output down to around 40Hz or so, but they now sound like they have been cut-off around 80Hz or so.  As they are absolutely fine in Windows 8, my only logical conclusion is that it's a driver / mixer issue and something to do with 2.1 or 5.1 perhaps.

Please help!  I want to get to know Ubuntu and Linux in general, but I can't do without my audio.

Thanks

---

### Post by absinthe on 2013-09-24
I am having this exact same problem! I have a Dell Inspiron 6600 with the conexant onboard and I am getting no bass at all. If I plug my speakers into the headphone jack - sound works fine? But this is a temporary workaround. Anyone know how to fix this?

---

### Post by lidex on 2013-09-29
I'd be interested to see more detailed info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by absinthe on 2013-10-02
> **lidex said:**
> I'd be interested to see more detailed info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Here you go:
[http://www.alsa-project.org/db/?f=113aa5ee5a50c3340aee51d1bc6117618681e92f](http://www.alsa-project.org/db/?f=113aa5ee5a50c3340aee51d1bc6117618681e92f)

Thanks!

---

### Post by dannymichel on 2013-11-15
> **lidex said:**
> I'd be interested to see more detailed info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

I'm having the same issue. Not sure why, but I've got no bass at all. [http://www.alsa-project.org/db/?f=018c3004a03b82c696599bf83a60be3cb6f90a67](http://www.alsa-project.org/db/?f=018c3004a03b82c696599bf83a60be3cb6f90a67)

---

### Post by Owen Z5 on 2013-12-17
Same problem for me with the Conexant CX20641 (Dell Inspiron 620MT / HDA Intel PCH on-board sound card), but with Ubuntu 12.04.3.

I tried the conexant/linuxant driver 'alsa-driver-linuxant 1.0.23.1', which didn't work. In fact it was pretty hazardous - it's a source package which tries to rebuild a bunch of snd- modules; the build fails, leaving the package half-installed. Subsequent removal of the package removes all snd- modules, leaving the machine with *no* sound capabillity at all. Repairing the damage for me required the re-installation of linux-image-3.2.0-57-generic-pae.

I'm going to try out a budget usb sound card...

---

### Post by lastfm on 2014-01-05
I've had the exact same problem with my Inspiron 660 on Gentoo. After about a week I have got the issue worked out - reassigning the jacks with hdajackretask worked.

[http://forums.gentoo.org/viewtopic-p-7475926.html#7475926](http://forums.gentoo.org/viewtopic-p-7475926.html#7475926)

---

