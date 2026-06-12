---
title: "Using JackCtl &amp; Presonus Firepod as soundcard"
date: 2008-02-21
forum: Multimedia Production
---

### Post by chales on 2008-02-21
First post, first question :)
I've been lurking here for a few months now, and so far have found almost all the answers i need.  Here is the one thing I can't figure out.

I'm using Ubuntu Studio 7.10 and a PreSonus Firepod, (I've read a number of threads on this, telling me how to setup FreeBob, JackCtl, etc). 

I can configure all most of the programs I need (Ardour, Audigy, Audacious, etc) to use Jack for audio recording and playback, but I can't find a way to get Ubuntu to configure the Jack/Firepod as its normal sound device.  My motherboard (MSI K8N Platinum) comes with a built-in sound device: RealTeck AC97, and Ubuntu wants to use that.  

This isn't too big a deal, but I'd like to be able to hear audio embedded in websites like YouTube, MySpace, etc.

Any suggestions?

---

### Post by Stochastic on 2008-02-21
I'd like this too but I don't think all of Ubuntu's apps are able to program jack as a sound manager.

There are two possible routes that I'm aware of to get a remedy (I'm opting for the second): 
1) Set jack as the output device for alsa.  Basically apps like firefox will still send to alsa, but then alsa outputs to jack.  Here's the instructions: [http://alsa.opensrc.org/index.php/Jack_%28plugin%29](http://alsa.opensrc.org/index.php/Jack_%28plugin%29)

2) Wait for pulse audio to be fully implemented in upcoming versions of Ubuntu. (dear devs: please hurry)

---

### Post by mimp on 2008-02-22
The alsa-jack plugin wont work in gutsy due to a bug, (it wouldn't for me at any rate)

However if you download hardy's alsa-plugins and alsa-lib sources and compile/install those they seem to coexist happily with gutsy and everything works fine.

I'm using normal gutsy (rather then studio) with svn compiled freebob/ffado/jack and a saffire pro (not a presonus card) so ymmv, I'm no linux guru so be careful in case this breaks everything :-)

[https://launchpad.net/ubuntu/hardy/+source/alsa-lib/1.0.15-3ubuntu3](https://launchpad.net/ubuntu/hardy/+source/alsa-lib/1.0.15-3ubuntu3)
[https://launchpad.net/ubuntu/hardy/+source/alsa-plugins/1.0.15-1ubuntu2](https://launchpad.net/ubuntu/hardy/+source/alsa-plugins/1.0.15-1ubuntu2)

---

