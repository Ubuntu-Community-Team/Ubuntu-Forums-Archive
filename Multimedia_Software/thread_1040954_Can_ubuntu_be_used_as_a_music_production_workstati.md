---
title: "Can ubuntu be used as a music production workstation?"
date: 2009-01-16
forum: Multimedia Software
---

### Post by bobdobbs on 2009-01-16
Hi all.
I'm using ubuntu 8.10.

I'm getting interested in creating music. 
I will be creating mashups, mixes and remixes.

I'd like to know if ubuntu can serve a reliable and productive workstation for this.

I've installed a bunch of programs that I'm learning how to use: audacity, hydrogen, sweep and others.

But after a few days of playing with these awesome tools, I keep running into problems that seem to be ubuntu problems. Gnusound crashes X, audacity occaisonally seems to stop outputting sound randomly, amarok freezes or crashes working if I am or have been using something else that outputs sound, jack randomly decides to stop outputting sound, the audio device stops becoming accessible...
Some of these problems can only be solved with a reboot.

I'd like to know if I can actually solve these problems one-by-one and if I can do so with minimal pain.

There are so many cool linux sound tools out there, but is ubuntu a reliable platform for them? 

Are there any producers out there, bedroom producers or professional producers (or both) that use ubuntu? 

Thanks.

---

### Post by Jose Catre-Vandis on 2009-01-16
Try installing Ubuntu Studio, a variant of Ubuntu, that is set up specifically for the purpose with a real time kernel etc. It's downloadable as an iso.

---

### Post by bobdobbs on 2009-01-16
I am indeed considering Ubuntu Studio.

If it's possible I'd prefer not to have to do a re-install though.

Also, the current version of US doesn't have the realtime kernel by default.
I have installed the realtime kernel on my workstation already.

---

### Post by Jose Catre-Vandis on 2009-01-16
Surely you must have space to do a second install? I have four OS running on my PC and use Ubuntu Studio for "music" things. Installation gave me real time kernel (rt) by default (8.04 LTS)

---

### Post by JawsThemeSwimming428 on 2009-01-16
In addition to Ubuntu Studio there are three other Linux distro's aimed at this that are worth looking at:

1. Musix
2. 64 Studio
3. dyne:bolic

Good Luck!

---

### Post by eye208 on 2009-01-16
> **bobdobbs said:**
> But after a few days of playing with these awesome tools, I keep running into problems that seem to be ubuntu problems. Gnusound crashes X, audacity occaisonally seems to stop outputting sound randomly, amarok freezes or crashes working if I am or have been using something else that outputs sound, jack randomly decides to stop outputting sound, the audio device stops becoming accessible...
Some of these problems can only be solved with a reboot.
Ubuntu is using PulseAudio, a sound server that is currently in public beta testing. If you search the forums you will see that this piece of software is causing countless problems. If you consider using Ubuntu for anything serious, you should remove PulseAudio and use only ALSA and Jack. This will make your sound applications more stable and also give you reasonable latency. For very low latencies (less than 12ms) you need the RT kernel which is currently only available for Ubuntu 8.04 LTS (unless you build it yourself).

Ubuntu Studio is not really a separate distribution but standard Ubuntu plus a set of multimedia applications for sound, graphics and video, plus the RT kernel (if available). You can add these to a normal Ubuntu install as well. The result will be the same.

---

### Post by 73ckn797 on 2009-01-16
Look at this info, it might help.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Somewhere in the forums there is info to install all of the Studio programs within Ubuntu. You will have to search for that your self.

EDIT: Here is the link. I have it bookmarked:
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

---

### Post by markbuntu on 2009-01-16
If you go here, you will find a lot of information and links about sound in Ubuntu/linux including how to get alsa, pulseaudio and jack working properly and together. 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you are using Intrepid you can still get the ubuntuStudio packages and run with the generic kernel until the rt kernel gets straightened out which should be fairly soon.

If you want the rt kernel you need to use 8.04 for now. I use UbuntuStudio on both Hardy and Intrepid and I find there is not much difference.

---

### Post by bobdobbs on 2009-01-17
> **Jose Catre-Vandis said:**
> Surely you must have space to do a second install? I have four OS running on my PC and use Ubuntu Studio for "music" things. Installation gave me real time kernel (rt) by default (8.04 LTS)

It seems that its just the latest version that doesn't supply a realtime kernel. Apparenty they are working on it.

---

### Post by bobdobbs on 2009-01-17
Thanks for the advice and the pointers everyone.

I followed 73ckn797's advice and link, and installed ubuntu studio.
Thankfully, this went very smoothly. All the packages simply installed on top of my existing install.

I found a document that descibes how to fix pulseaudio, but I'm still getting stuttery sounds with mixxx and with the sound that plays when I log into my desktop, so I'm considering removing it.
My decision will rest upon what I discover as I investigate the differences between pulseaudio and ESD.
At the moment I'd prefer to fix PU. But, if it's a habit, then I'll get rid of it.

Thank you everyone.

I am open to further observations and advice.

---

### Post by markbuntu on 2009-01-18
If you find the sound stuttering etc, you can edit the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 8
;default-fragment-size-msec = 5

```
Change them to look like this :
```

default-fragments = 5
default-fragment-size-msec = 25

```
Save the file and restart Pulse Audio. 

This was written specifically for suttering in skype but will give you the general idea of how to deal with sound stuttering. Another cause of sound stuttering is that sound is not given enough priority in the kernel so gets suspended when higher priority apps use the cpu.


EDIT: I got the numbers transposed in the default fragment lines, sorry. I have corrected it.

---

### Post by simtaalo on 2009-01-18
any serious music stuff you should be just using JACK.

i'm currently making music using 8.10, and its fine, although going on a few different linux musican forums and it seems studio64 seems to be a popular option, its based on debian. this means won't be too different than ubuntu.

i recommend checking lmms out, my favourite music making program on linux [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

---

### Post by MedellinManDem on 2009-02-21
> **simtaalo said:**
> any serious music stuff you should be just using JACK.

i'm currently making music using 8.10, and its fine, although going on a few different linux musican forums and it seems studio64 seems to be a popular option, its based on debian. this means won't be too different than ubuntu.

i recommend checking lmms out, my favourite music making program on linux [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

This post completely muddies the waters.

Do you recommend installing Ubuntu Studio or not?

---

### Post by MedellinManDem on 2009-02-23
Anyone?

---

### Post by bsh on 2009-02-23
theoretically - yes.
practically - no.
i say that, because the linux sound systems are crap imho, and that the apps that are available on the linux platform are either useless or just buggy.
i have a lot of "exotic" hardware (which are not that exotic at all, at least on the computer music scene, but surely they are rarely found on an average pc), and they are absolutely not supported on linux. i can't even get my class compliant usb sound cards to work. doesn't even mention midi and usb controllers and exotic sound boards...
i would love to make music on linux and completely switch from windows, but i must say, linux is not good for this yet. too bad. :( windows is still superior for making music, or maybe apple and osx - which i don't know, but i know many people are using that for music.

---

### Post by markbuntu on 2009-02-23
There are lots of professionals and professional recording studios using linux but they do not use Ubuntu, they do custom builds from the ground up. Linux is about the only reasonable way to set up and use clusters, which have become necessary for the work these people are involved in, like sound tracks for movies etc.

Getting a linux studio up and running can be difficult if you do not invest enough time to learn it or if you try to use the wrong stuff the wrong way or if you expect it to work like in windows. The best thing you can do is just forget about everything you learned with windows because you will just get frustrated.

Many people also have unrealistic expectations, like using the latest releases and expecting them to be stable. It is not called the bleeding edge for nothing. 

I use Hardy UbuntuStudio and it is finally very stable and all dialed in and working just fine for me. I really have no compelling reason to move to Intrepid and go through all that again, so I wont. I will keep this for a few years, maybe update some pieces here and there but stability is what I am after so chasing the ghost is not for me.

I do have Intrepid and even Jaunty, but they are completely separate installs that I test out when I have the time but for any real work, I boot into hardy. I am not even considering moving to Intrepid or Jaunty as my main system. Intrepid is still buggy and neither one will be supported as long as Hardy

---

### Post by pgmer6809 on 2009-03-17
> **bobdobbs said:**
> Thanks for the advice and the pointers everyone.

I followed 73ckn797's advice and link, and installed ubuntu studio.
Thankfully, this went very smoothly. All the packages simply installed on top of my existing install.

I found a document that descibes how to fix pulseaudio, but I'm still getting stuttery sounds with mixxx and with the sound that plays when I log into my desktop, so I'm considering removing it.
My decision will rest upon what I discover as I investigate the differences between pulseaudio and ESD.
At the moment I'd prefer to fix PU. But, if it's a habit, then I'll get rid of it.

Thank you everyone.

I am open to further observations and advice.

Hello Bob:
Can I ask you what sound card you are using? I am having a VERY hard time finding reliable info on a sound card that will RECORD in Ubuntu.
Most will play, but I need a reliable card that will do simple stereo recording and playback at 24bit 96/192Khz.
Any hints? 
Or should I be looking at an external device attached via Firewire?
pgmer6809

---

