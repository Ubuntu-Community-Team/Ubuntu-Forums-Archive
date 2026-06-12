---
title: "Installing Broadcom Crystal HD drivers - how?"
date: 2012-02-25
forum: Multimedia Software
---

### Post by c-m on 2012-02-25
I have a broadcom crystal hd card that i've put in my dell mini 9.

I'm running 11.04, but can't for the life of me figure out how to install the drivers for this card.

Broadcom offers source code at: [http://www.broadcom.com/support/crystal_hd/](http://www.broadcom.com/support/crystal_hd/)

That comes in a .zip file. Once extracted there is a bzip2 file inside. What do i do with this? It's not an archive as when i try to open it in archive manager is displays

```
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

All other threads on this board refer to drivers at:  [http://git.wilsonet.com/crystalhd.git/](http://git.wilsonet.com/crystalhd.git/)

This page no longer exists it throws up a 404 error in the browser and git times out when run from the terminal.

Can anyone help?

---

### Post by mudd1 on 2012-03-09
Ok, this is how far I got: there are Ubuntu packages for Crystal HD. There's crystalhd-dkms which is the kernel module you need. This one works great for me, crystalhd shows up in dmesg and all. Then there is crystalhd-firmware. No idea what it does. The package description is incredibly helpful: "This package contains the CrystalHD firmware." Duh. Then there is gstreamer0.10-crystalhd which is the gst plugin for Crystal HD and to my understanding should enable for example totem to actually use the darn chip. There's also a library called libcrystalhd3.

Mplayer is also supposed to support Crystal HD. However, neither totem nor mplayer nor any other player I tried (VLC, kaffeine ...) seemed to make any use of the acceleration.

According to this (German) page [http://geekparadise.de/2011/04/crystalhd-libcrystalhd-und-gstreamer-plugin-in-ubuntu-kompilieren/](http://geekparadise.de/2011/04/crystalhd-libcrystalhd-und-gstreamer-plugin-in-ubuntu-kompilieren/)
tail -f /var/log/syslog should spit out the line "crystalhd 0000:02:00.0: Opening new user[0] handle" as soon as a video is decoded by the Crystal HD hardware. There is also an indicator applet [http://code.google.com/p/indicator-crystalhd/](http://code.google.com/p/indicator-crystalhd/)

So, as I said, this is how far I got. If anybody can take over from here, I'd be just as happy as the original poster.

Oh and maybe I should add that all howtos I found mentioned that the Ubuntu packages are crap and you have to compile everything yourself. Those howtos are two years old though and I'm just not ready to believe that these packages survived till Precise without being improved or thrown out.

---

### Post by mudd1 on 2012-03-12
Ok, now here's a sad solution to fix the gstreamer support: the darn device has no write permissions per default. So just giving /dev/crystalhd group write permissions and putting it and your user in some sensible group should make an off-the-shelf Ubuntu with the right packages installed Crystal-HD ready. mplayer/ffmpeg seems to be a different story. I had to compile it myself and actually edit out the experimental tags in the crystalhd.c file in ffmpeg to make it work. There gotta be a nicer way for the last step but I was to lazy to find it.

BTW, the crystalhd device doesn't seem to get initialized correctly after a suspend so I have to watch videos on a freshly booted system if I want hardware support. Anyway, it uses *much* less of my Atom CPU but 2W *more* power overall. Brilliant.

Anyway, someone should file a bug report for this but I'm just too fed up with Ubuntu bug reports to convince myself of doing it.

Edit: Someone already did: [https://bugs.launchpad.net/ubuntu/+source/crystalhd/+bug/944353](https://bugs.launchpad.net/ubuntu/+source/crystalhd/+bug/944353)

---

### Post by wolfen69 on 2012-03-12
I've tried to get crystal hd working on my netbook for almost 2 years with no luck. I've pretty much given up, and just watch non hi-def videos on it. But if someone can chime in with some answers, I'm all ears.

---

### Post by c-m on 2012-03-12
I actually got mine to work by using precompiled debs. No worries.

I would like to get VLC 2 compiled with CrystalHD support. It supports it, but I don't know how to got about turing on the support during the configure/make/install process.

---

### Post by mudd1 on 2012-03-12
> **wolfen69 said:**
> I've tried to get crystal hd working on my netbook for almost 2 years with no luck. I've pretty much given up, and just watch non hi-def videos on it. But if someone can chime in with some answers, I'm all ears.

Did you try the packages I mentioned? And did you try them on Precise? Then it should just be a matter of permissions to get crystal hd to run in totem and flash actually. As I said, you'll have to compile mplayer yourself if you want support there.

---

### Post by mudd1 on 2012-03-12
> **c-m said:**
> I actually got mine to work by using precompiled debs. No worries.

I would like to get VLC 2 compiled with CrystalHD support. It supports it, but I don't know how to got about turing on the support during the configure/make/install process.

Glad it works!

I assume you installed the dev package, too, and of course ran ./configure with --enable-crystalhd? What does the config.log say then?

---

### Post by BicyclerBoy on 2012-03-12
Is the VA-API backend for crystalHD an option ?
[http://freedesktop.org/wiki/Software/vaapi](http://freedesktop.org/wiki/Software/vaapi)

But the crystalHD git source has not been touched since Dec2010..
Shame because it is a better approach than building in support in VLC.

[http://wiki.videolan.org/VLC_configure_help](http://wiki.videolan.org/VLC_configure_help)

---

### Post by c-m on 2012-03-13
> **mudd1 said:**
> Glad it works!

I assume you installed the dev package, too, and of course ran ./configure with --enable-crystalhd? What does the config.log say then?

I haven't tried yet. I'll give that a go tonight.

---

