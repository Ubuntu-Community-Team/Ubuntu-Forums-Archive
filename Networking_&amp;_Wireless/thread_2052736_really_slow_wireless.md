---
title: "really slow wireless"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by pyro.xyz on 2012-09-03
Okay, so I run a laptop, and obviously, I use the wireless 98% of the time. The other 2% that I don't use the wireless is because the wireless connection seems to be so slow. Here's the problem (in my understanding). I cannot open pages with a lot of content, or download large files, because the wireless is seemingly over-loaded. I have a 72 MB/S connection (currently), so that isn't the problem. If, say I want to watch anime, I will open the web-page hosting the content, but it doesn't load all the way, but instead stops loading, and then I can't load ANYTHING else without resetting my wireless card (turning wireless off and then on again). Needless to say, this is a very time-consuming and annoying thing to do, and it doesn't help me watch anime (that is only a single example. I also can't download a lot of software from the software-center without a wired-connection). ](*,) Can anyone help me with this? (Actually, I think it's a driver issue, but I'm not sure, because I had issues installing the wireless driver to begin with. Oh, yeah, I run Ubuntu 12.04, just so you all know.

---

### Post by iponeverything on 2012-09-03
> **pyro.xyz said:**
> Okay, so I run a laptop, and obviously, I use the wireless 98% of the time. The other 2% that I don't use the wireless is because the wireless connection seems to be so slow. Here's the problem (in my understanding). I cannot open pages with a lot of content, or download large files, because the wireless is seemingly over-loaded. I have a 72 MB/S connection (currently), so that isn't the problem. If, say I want to watch anime, I will open the web-page hosting the content, but it doesn't load all the way, but instead stops loading, and then I can't load ANYTHING else without resetting my wireless card (turning wireless off and then on again). Needless to say, this is a very time-consuming and annoying thing to do, and it doesn't help me watch anime (that is only a single example. I also can't download a lot of software from the software-center without a wired-connection). ](*,) Can anyone help me with this? (Actually, I think it's a driver issue, but I'm not sure, because I had issues installing the wireless driver to begin with. Oh, yeah, I run Ubuntu 12.04, just so you all know.

open a terminal and run "sudo tail -f /var/log/daemon.log"

post or google any clues that pop up in the log at the time of the issue..

---

### Post by pyro.xyz on 2012-09-04
So, you want me to run this and then cause my wireless to freak out?

---

### Post by pyro.xyz on 2012-09-04
Okay, so I tried, but it didn't work, because apparently, there is "No such file or directory." Is there something I should do before executing
```
sudo tail -f /var/log/daemon.log
```

---

### Post by pyro.xyz on 2012-09-06
Okay, somebody needs to help me with this, or else this thread is just going to die, and this problem will never get fixed.

---

### Post by MckayKnight on 2012-09-06
> Okay, somebody needs to help me with this, or else this thread is just going to die, and this problem will never get fixed.

What I have found works for me as I been having wireless issues with Ubuntu 12.04.1 LTS I installed Wicd first then I removed the program 'network-manager' seeing as it's the one used by Ubuntu. Then my wireless disconnectivity issues seem to go away. Seems like a stable wireless-n connection for me. You can always give it a run for it's money. :)

---

### Post by pyro.xyz on 2012-09-07
> **MckayKnight said:**
> What I have found works for me as I been having wireless issues with Ubuntu 12.04.1 LTS I installed Wicd first then I removed the program 'network-manager' seeing as it's the one used by Ubuntu. Then my wireless disconnectivity issues seem to go away. Seems like a stable wireless-n connection for me. You can always give it a run for it's money. :)

Hey, does anyone know if this will actually help with my problem?

---

### Post by iponeverything on 2012-09-07
> **pyro.xyz said:**
> So, you want me to run this and then cause my wireless to freak out?

ls -ltr /var/log 

will show you the most recent log to be written to -- when your wireless craps - look at the recently written to logs and look for clues.

Also -- in the grub menu boot to an earlier kernel to see if issues still exists -- if it does not just make that kernel your default

---

