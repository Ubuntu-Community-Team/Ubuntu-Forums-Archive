---
title: "linux as bluetooth/a2dp *receiver*"
date: 2009-09-06
forum: Multimedia Software
---

### Post by birnam on 2009-09-06
I have my Kubuntu Jaunty set up nicely to send a2dp audio to my bluetooth headset. That's no problem.

What I want is to be able to **receive** a2dp audio and play it as an audio source on my desktop.

I have a windows mobile phone (omnia) that's capable of playing the Zune subscription drm'd wma files, but there's no real way of playing them in linux (that I've found). I download the music with the zune software and sync that to my phone through a vista virtualbox machine, but I'd rather listen to it through my computer's speakers than my phone/headset. 

It seems like a2dp is a fairly straightforward solution, and I can get my phone and linux to pair. But I can't figure out how to set up my desktop to have an audio profile service to my phone.

Any ideas? Has this been done? I've googled and googled some more and haven't found anything useful.

---

### Post by blackbird-xx on 2009-10-10
I second that!

I would love to stream audio from my mobile phone to my stereo, which happens to have an xubuntu box connected.

But alas, ubuntu does not seem to be able receive a2dp.

---

### Post by elmicha on 2009-11-24
Have a look at [João Paulo's site]("http://jprvita.wordpress.com/2009/07/17/bluez-now-has-a2dp-sink-support/"), he made a A2DP sink for Bluez.

Alas, the Bluez version in Karmic is too old (4.39), and perhaps Pulseaudio is also too old. But probably with Ubuntu 10.04 it might work.

---

### Post by daryl314 on 2010-03-06
> **elmicha said:**
> Have a look at [João Paulo's site]("http://jprvita.wordpress.com/2009/07/17/bluez-now-has-a2dp-sink-support/"), he made a A2DP sink for Bluez.

Alas, the Bluez version in Karmic is too old (4.39), and perhaps Pulseaudio is also too old. But probably with Ubuntu 10.04 it might work.

He posted a set of instructions that worked perfectly for me on Kubuntu 9.10

[http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/)

---

### Post by everythingsround on 2010-05-08
Any help with understanding some of these - what appear to be - generalizations.  Things like:

edit /etc/bluetooth/audio.conf and add the following line: Enable=Source ;

and

load-module module-loopback source=<name> sink=<name>

It seems like I would need to change some of that to fit my config.  Thanks in advance.

---

### Post by megamanexent on 2010-08-09
[http://ubuntuforums.org/showthread.php?t=1464189&highlight=A2DP+audio](http://ubuntuforums.org/showthread.php?t=1464189&highlight=A2DP+audio)

Thread has more detailed instruction, page 1 last post!!

---

