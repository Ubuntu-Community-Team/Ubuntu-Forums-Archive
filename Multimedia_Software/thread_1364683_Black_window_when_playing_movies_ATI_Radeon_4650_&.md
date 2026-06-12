---
title: "Black window when playing movies: ATI Radeon 4650 &amp; Compiz on 9.10"
date: 2009-12-26
forum: Multimedia Software
---

### Post by Laz23 on 2009-12-26
Hello all,
I just got an ASUS EAH4650 1GB PCI-Express graphics card for my Ubuntu PC. It has a Radeon 4650 chip and 1GB of graphics RAM.


After installing the card, everything worked fine. I could use the default community drivers or the proprietary ATI/AMD drivers - both worked fine.

My problem is this: after I tried to enable Compiz desktop effects in the Ubuntu 'Appearance' control panel item, I now cannot watch any videos in any application.

When I try to play a video, all I get is a black screen where the video should be. The rest of the UI is intact, but the video isn't there. This is the case both in VLC and Totem (and other gStreamer-based apps). I can hear the sound, and codecs aren't an issue as I've been able to play the movies before with exactly the same software. Also, in Nautilus I can see that the movies have preview icons which have stills of the video, so obviously the OS is able to read the movies but not display them somehow. I have tried a wide variety of file types, including MKVs with MPEG-4 H.264 video tracks, AVIs with DivX tracks, QuickTime and many others.

A screenshot of what happens is here:
[http://www.ubuntu-pics.de/bild/35620/screenshot_001_OWK1GU.png](http://www.ubuntu-pics.de/bild/35620/screenshot_001_OWK1GU.png)

You can see in the background of that picture that the movie has a video preview in its icon in Nautilus, but that the video track does not show in Totem.

I have turned Compiz off (by setting the Visual Effects level to 'none'), but it hasn't made any difference.

I have also tried reverting to the community ATI drivers, and restarting my machine. I have tried various combinations of Compiz levels plus drivers, none of which have made a difference:

ATI drivers installed using Ubuntu 'hardware drivers' CP + 'none' compiz setting
ATI drivers installed using Ubuntu 'hardware drivers' CP + 'normal' compiz setting
ATI drivers installed using Ubuntu 'hardware drivers' CP + 'extra' compiz setting
Open source drivers + 'none' compiz setting
Open source drivers + 'normal' compiz setting
Open source drivers + 'extra' compiz setting
ATI drivers installed manually from ATI web site + 'none' compiz setting
ATI drivers installed manually from ATI web site + 'normal' compiz setting
ATI drivers installed manually from ATI web site + 'extra' compiz setting

It seems I need a way to reset X and my video driver setup to their defaults so that I can undo whatever I did wrong by enabling Compiz. I would also like to know why this problem occurred, as it's very strange.


Context:

I'm running a clean install of Ubuntu 9.10 (32-bit), and I have an Asus P5KPL-VM motherboard and an Intel Core 2 Duo 2.0Ghz E4500 processor.

The ATI driver version I downloaded from the ATI web site to test if a manual install would improve things is 8.68.2. I don't know the version number that the Ubuntu Hardware Drivers control panel installed for me.

Thanks in advance for any advice.

---

### Post by llawwehttam on 2010-01-09
I have the same thing but with an Nvidia GT130M .
And I mean Exactly the same.

---

### Post by Laz23 on 2010-01-09
Hi there,
I meant to come back and update this thread after I found the solution, but forgot (too busy watching the movies that I can now see!)

Basically the GNOME config was messed up.

Try creating another user account, and see what happens. If it's OK in a new account, maybe GNOME is messed up like on my machine.

In the end all I did to fix the problem was delete the various GNOME desktop config files in my normal user account, [as detailed here]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/").

Really you just need to run:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

then restart.

Hope this helps.

---

### Post by pingu1 on 2010-03-22
I had a problem with just a black screen when playing movies, but I figured out that it had something to do with my external screen, and not the gnome config.

I did the > rm -rf .gnome .gnome2 .gconf .gconfd .metacity

How do I reset this, because now compiz does not run...

---

### Post by pingu1 on 2010-03-22
compiz check gives just this output:
> compiz check
aborting and using fallback: /usr/bin/metacity 


---

### Post by pingu1 on 2010-03-22
Please help...

---

### Post by pingu1 on 2010-03-22
Sorry folks. My bad! I'm a total moron. I ran it using "failsafe gnome" earlier because of some trouble I had with using an extended desktop on my external monitor... ... I thought this setting in the login-screen would automatically go back to Gnome, but it did not apparently. I switched to gnome-session - now compiz runs fine.

Sorry. So ... ... ... anyway - how 'bout that global warming? (conversation switch).... :)

---

### Post by Kendustin on 2010-05-08
I was having somewhat similar issue with totem and VLC  but with another card. When I run the rpm code I caught the problem where I was getting wrong and came to know that the problem was regarding to vlc gnome and vlc beta gnome both being installed.

---

