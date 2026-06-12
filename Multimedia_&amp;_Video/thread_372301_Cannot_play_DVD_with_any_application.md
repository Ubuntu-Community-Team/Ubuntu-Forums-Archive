---
title: "Cannot play DVD with any application"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by NevadaDave on 2007-02-28
I have recently installed Ubuntu 6.06 on a second HD on my XP system. The install went well, and I have been trying to install different packages to get acces to my XP partitions (whoopee - ntfs-3g finally worked!) and get the media players working. I was able to play part of a DVD (Titan AE) in gxine, not at all in Totem. I installed mplayer, and as far as I know, did it correctly. AT any rate - all of them seem to be able to play mp3 files and .avi files, but I can't seem to play DVD's now. When I put a DVD in, Totem will come up, but never plays anything. I can see a lot of flickering LED's on the DVD drive and the HD, but nothing ever happens. After minutes of this, I click the quit box & generally get a message saying that the application is not responding, and I select force quit. I am a complete noob at this linux stuff, and although I'm getting better at using the terminal window to do things, I still am not always sure exactly what it is I'm doing. I tried using the Synaptics manager to re-install gxine and totem, but to no avail.
I would appreciate any help.
The system is a 2.4 GHz P4, 512 mb RAM, 120 GB HD for XP, and a 40GB HD for Ubuntu.

---

### Post by openix on 2007-02-28
In order to play DVD's you will need the libdvdcss2 package. I suggest you look at [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") if you have not done so already.

---

### Post by RomeReactor on 2007-02-28
Hi. If you already have [libdvdcss]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability"),  as the previous post suggested, and still can't play dvd's, it may have to do with having **Gstreamer** instead of **Xine** as Totem's backend; so i suggest you install Totem-Xine from Synaptic, along with LibXine-ExtraCodecs, or to do it from the terminal

```
sudo apt-get install totem-xine libxine-extracodecs
```

If you don't have Totem-Xine already.

---

### Post by NevadaDave on 2007-02-28
Openix,
I did install libdvdcss2 package, after I got a "You don't have the codec for DVD" error message. After this install, I didn't get the error message anymore, but I still couldn't play DVD's. I'll try the solution in the next post and see what happens!

---

### Post by Cobikegeek on 2007-02-28
I've had the most success playing dvds with VLC or Kaffeine.  VLC downloads most of the codecs it needs to run during the install.  You still need to make sure you have regionset assigned on your dvd drive (see the restricted formats page mentioned above for instructions).  Kaffeine works best with KDE.  Either can be installed with synaptic.

---

### Post by NevadaDave on 2007-02-28
Hmmm... well, now I feel a bit embarrassed. I looked back & saw that the package I actually installed was libdvdcss-1.3.9, NOT 2.
I started looking for the v2 package, but several of the links I found were no longer active. On the Ubuntu site, there's a link to [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.1-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.1-1_i386.deb)
Is this the correct decoder?
I did install totem-xine  and libxine-extra codecs.
Now, when totem starts up, I get an error that says something like, "Are you trying play an encrypted DVD without libdvdcss?". At least totem seems to realize that there is a DVD in the drive & doesn't just lock up!

---

### Post by NevadaDave on 2007-02-28
OK, the 1.2.5 version of libdvdcss2 did not work (some kind of depndency issue in gdebi)
However, 1.2.1 did - and I'm watching Star Trek:Nemesis as I type this!
Thanks for all the help! Now, if I can figure out how to share my printer over my network, I'll be very happy with Linux.

---

### Post by talon 2 on 2007-03-13
> **NevadaDave said:**
> OK, the 1.2.5 version of libdvdcss2 did not work (some kind of depndency issue in gdebi)
However, 1.2.1 did - and I'm watching Star Trek:Nemesis as I type this!
Thanks for all the help! Now, if I can figure out how to share my printer over my network, I'll be very happy with Linux.

I  found your post and had the same problem as you.  I used your link and fixed my problem.  Just want to thank you.

I have to say the ubuntu community is geat!

---

### Post by NevadaDave on 2007-03-13
"I found your post and had the same problem as you. I used your link and fixed my problem. Just want to thank you.

I have to say the ubuntu community is geat!"
No problem! I also figured out how to share my printers - unfortunately, I didn't bookmark the link, but if necessary, I can find it again.

---

### Post by koshari on 2007-03-13
as far as adding the dvdlib package , adding the medibuntu repos is prolly a better way as you can use synaptic and have the packages updated without dependency problems.

---

