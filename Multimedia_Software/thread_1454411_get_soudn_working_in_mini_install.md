---
title: "get soudn working in mini install"
date: 2010-04-14
forum: Multimedia Software
---

### Post by clutch| on 2010-04-14
Had Xubuntu on my old laptop previously, and decided I wanted something even lighter, so I installed fluxbox.  Everything was working great, played around with all the config files for a while and decided I liked it.

So I decided to start over fresh and used the Ubuntu Minimal ISO to do the command line install.  Got fluxbox and other assorted stuff (wireless, firefox, etc) up and running.  I cannot for the life of me get sound working with ALSA though.  I have installed alsa-base, alsa-utils, alsa-tools, linux-sound-base, and ubuntu-restricted-extras to no avail.  Went through alsamixer and unmuted/turned up all channels.  Still nothing.

lspci | grep audio shows my integrated sound card as an Intel 82801DB AC'97 Audio Controller.  aplay -l lists the same card (although it does list it twice for some reason).  I am about to download and compile the latest ALSA from [www.alsa-project.org]("http://www.alsa-project.org") to see if that helps, but I wanted to know if I'm missing something stupid.  

modprobe -v snd- comes back as FATAL: Module snd_ not found.  I'm guessing I need a driver for my sound card that was preinstalled in xubuntu/ubuntu/kubuntu.  Not sure what it is exactly though, because the repos have alsa version 1.0.20 and alsa-project.org only seems to have files for version 1.0.22.*

Any help would be hugely appreciated, I've spent all morning and part of the afternoon trying to get this working.

/edit found some backported drivers in the repo.  Trying that now.  Not much faith though.

/edit2 still nothing.  removing those now.  lsmod | grep snd shows snd_intel8x0.  That seems important.

---

### Post by clutch| on 2010-04-15
Bumping for help.  Still haven't compiled the latest stuff from alsa, because I've been busy and I'm not even sure if that's the problem anyway.

---

### Post by Scott82 on 2010-04-20
I've been having the same problem, the easiest way of corse is to just install normal ubuntu then add fluxbox and configure it, but that's taking the entire 'minimal' ideal out of the situation.

I'm still trying to find out how to get it going, so there's no info that I know to get it working right now, but if I find anything, I'll let you know.

also, if any super Ubuntu ppls O.o read this, it'd be nice to add the info to the help page (if there is info to add of corse): [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

edit:
O.o got mine working but also realized that I probably have a different problem.

---

### Post by Yellow Pasque on 2010-04-20
Can you play sounds directly through ALSA?
```
aplay <some .wav or .ogg file>
```

---

