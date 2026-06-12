---
title: "mythfrontend.re starts twice"
date: 2009-04-11
forum: Mythbuntu
---

### Post by dualboot on 2009-04-11
Since upgrading from 8.04 to 8.10 I have had poor video performance and lock-ups.  I noticed that if I exit the frontend there is another copy running.  I confirmed by running 'top' in an SSH terminal.

How can I stop this ?

---

### Post by ghuber on 2009-04-11
Don't have a fix for this but I just ran updates on my Myth.  Got the last 7 updates and this started after the reboot.

---

### Post by dualboot on 2009-04-13
Thanks for the info Ghuber - at least I'm not alone - is there any way to see what starts up at boot ?  (like autoruns in a ahem... Windows environment)

---

### Post by tehsi on 2009-04-29
This is affecting me too. I've had no luck in working out what is responsible for starting the spurious frontend instance.

As a workaround, I've hacked some code into the start of mythfrontend.sh, to exit if mythfrontend.real is already running.

Does anybody know what could be causing this? I found
[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/241015](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/241015), which looks as though it might be related somehow.

---

### Post by superm1 on 2009-04-29
> **tehsi said:**
> This is affecting me too. I've had no luck in working out what is responsible for starting the spurious frontend instance.

As a workaround, I've hacked some code into the start of mythfrontend.sh, to exit if mythfrontend.real is already running.

Does anybody know what could be causing this? I found
[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/241015](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/241015), which looks as though it might be related somehow.
Please feel free to submit a patch to this bug: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/352077](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/352077)

and we can integrate it into weekly builds..

---

### Post by elgordo123 on 2009-04-29
I have the latest updates, but it isn't happening with me.  Could it be that you are running vncserver?   I know when I manually start it (I dont have it run as a service) it starts an instance of mythfrontend.  (However I am starting vncserver as a new desktop "vncserver :1")

---

### Post by pssturges on 2009-04-30
This one might be worth looking at:

[http://ubuntuforums.org/showthread.php?t=784896]("http://ubuntuforums.org/showthread.php?t=784896")

---

### Post by tehsi on 2009-05-07
The suggestion from [http://ubuntuforums.org/showthread.php?t=784896]("http://ubuntuforums.org/showthread.php?t=784896") worked for me. I found that

```
rm -rf ~/.cache/sessions/*
```

was sufficient to stop the multiple frontend instances from being started.

---

### Post by dmfrey on 2009-08-24
I started running into this issue.  It caused issues with, for instance, if one .real process was playing music, I could never stop it via the remote control and the music would play over other actions like watching tv.  It seemed it would stop if I could get a dvd to play its audio track.

My question about this is what is continually storing these sessions?  It seems to me that the cache should be cleared on boot, or is this just the nature of the .cache directory?

---

### Post by jb5 on 2009-08-24
This problem usually surfaces for me after an update to the kernel.
 
As I have MythWelcome starting on boot & sometimes while updating I also start MythFrontend, when it comes time to re-boot 'for updates to take effect', the machine struggles to close everything down properly & reboot. 

So I end up with several open windows on the next boot, rather than just MythWelcome.

It took a lot of digging around before I found the .cache fix, (wish I'd seen this thread).

So, *I guess*, the session is stored if there is an unusual or incomplete closure of your account. Perhaps someone more knowledgeable would confirm?

---

