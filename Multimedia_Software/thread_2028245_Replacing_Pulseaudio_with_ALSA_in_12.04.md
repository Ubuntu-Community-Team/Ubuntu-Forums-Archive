---
title: "Replacing Pulseaudio with ALSA in 12.04"
date: 2012-07-17
forum: Multimedia Software
---

### Post by g-raf on 2012-07-17
I'm using ubuntu 12.04 64bit.

I tried to disable Pulseaudio and replace it with ALSA as the default sound in order to reduce xruns when recording audio in Ardour. I followed this guide: [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

I couldn't get past this part of the guide: > sudo dpkg -i libsdl1.2debian-pulseaudio-dummy_1.0_all.deb

That's because the package libsdl1.2debian won't allow the pulseaudio dummy to be installed. The libsdl1.2debian-pulseaudio package is packed into the entire libsdl1.2debian package, so I can't uninstall the libsdl1.2debian-pulseaudio separately.

Is there any newer method to disabling pulseaudio in order to reduce xruns? I tried to undo the pulseaudio disabling attempt because banshee and rhythmbox no longer play music...there seems to be no way to configure them to use ALSA.

---

### Post by cek on 2012-07-17
Sadly after nearly 10 years of making music on linux, I still cannot get reliable results with Jack/Ardour in Ubuntu.

I have a dual boot setup now -- I use Ubuntu for most day to day tasks, but when I have to do recording or editing with low latency, I reboot into Gentoo.

I believe the problem to be in the various kernel configurations -- never been a great fan of using the RT patch set, but even the preempt and low latency kernels for Ubuntu give poor results.

In gentoo, I'm using a vanilla 3.2.12 kernel, and the only real changes of note are CONFIG_HZ=1000, support for RTC and HPET, low-latency scheduler, and compiling specifically for my architecture.

I've tried custom compiling kernels on Ubuntu in the past, as well as using the RT kernels found in various PPAs, but I've never had success.

Fedora fared a bit better (the default low latency Fedora kernels appear to have CONFIG_HZ=1000), but still have never been able to approach the reliable results of the Gentoo system.  I can easily record 4 tracks simultaneously, with 8ms latency with no XRUNS.

---

### Post by g-raf on 2012-07-17
I've moved to AVLinux, using dual boot. I've been using Ubuntu for a few years though, so I'm not totally giving up on it. I'm probably just going to do the same thing and use it for day to day tasks, then produce audio/video on AVLinux.

I just need to undo what I did so I can use Banshee and/or Rhythmbox in Ubuntu...

---

