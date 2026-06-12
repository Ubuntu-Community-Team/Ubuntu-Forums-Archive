---
title: "intel HD audio Realtek Toshiba a205-s4577 no sound"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by venky80 on 2007-04-27
I have tried pretty much all the guides for this audio problem but nothing works please help if you have your sound working and have the same model
I am using feisty kubuntu

---

### Post by skeetre on 2007-05-21
I have a Toshiba A205-S4607 with Intel hd audio, Realtek ID 268. No sound, I've tried every solution I could find. no acpi, recompiled/installed alsa drivers, modified the alsa-base file, etc.  It appears to conflict with the modem, I have alsamixer controls for master, pcm, off-hook, and line.  I had usb sound working with a logitech headset, but after all the screwing around trying to get intel-hda audio working, my usb audio doesn't work anymore either.

---

### Post by venky80 on 2007-05-22
please post your solution if you manage to find a fix.
it is surprising there is so solution for it till now.

---

### Post by azunino on 2007-05-31
I have the same problem. Any solution?

---

### Post by venky80 on 2007-06-01
nothing yes have posted a bug, now it says fix committed . I have mailed asking more info
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

---

### Post by brightscreamer on 2007-10-09
Does anyone have a fix for this? I am a first-time Ubuntu/Linux user and am using Feisty.

---

### Post by saukya on 2007-11-30
I have Toshiba satelite A205-S4707 and the sound doesn't work, what should I do??

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by Yellow Pasque on 2007-11-30
You can try OSSv4 (see my sig).

---

### Post by flehnerz on 2007-12-21
> **Temüjin said:**
> You can try OSSv4 (see my sig).

And that works with Realtek? I dont see any Realtek cards on the supported list.


And what's going on here...is this going to cause a problem..
```

frank@frank-laptop:~$ sudo apt-get install gcc gcc-4.1 gcc-4.1-base gcc-4.1-multilib make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
gcc-4.1 is already the newest version.
gcc-4.1-base is already the newest version.
Package gcc-4.1-multilib is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc-4.1-multilib has no installation candidate
frank@frank-laptop:~$ 


```

---

### Post by flehnerz on 2007-12-21
Well it worked. I have sound on my Toshiba A205, thank you very much
The volume control no longer works. I understand the sound isn't controlled that way anymore but is it possible to program my volume wheel to control the ossxmix.

---

### Post by Yellow Pasque on 2007-12-22
Check [here]("http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=") for a patch for the volume control.

As you've figured out, Realtek codecs are covered under the hda-intel driver. As for the multilib package, you need not worry about that unless you're running Ubuntu64.

---

### Post by flehnerz on 2007-12-22
> **Temüjin said:**
> Check [here]("http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=") for a patch for the volume control.

As you've figured out, Realtek codecs are covered under the hda-intel driver. As for the multilib package, you need not worry about that unless you're running Ubuntu64.


Doesn't seem to do anything. I tried to follow another tutorial involvig alsa drivers to get my sound working before I stumbled onto this thread and since then Ubuntu will not detect my sound card. However, the oss library is churning out sound just fine. Quit an odd thing. 

Or maybe its because I used Nautilus to copy the file for the vol control over into the /usr/lib/gstreamer-0.10/ directory that I also had to create. Perhaps it just did not install? I double clicked on it a few times and even right clicked and made it executable as a program.

---

