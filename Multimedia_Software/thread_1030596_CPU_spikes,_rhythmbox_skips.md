---
title: "CPU spikes, rhythmbox skips"
date: 2009-01-04
forum: Multimedia Software
---

### Post by fela on 2009-01-04
Often when I'm playing music with rhythmbox, 'everyday' stuff can make the CPU spike noticeably - i.e. make the song in rhythmbox skip which is really bad. I uninstalled pulseaudio but that didn't help. I shouldn't imagine that it's my hardware (specs below), but I will say that I run compiz and I don't have a very good video card. The skipping and spiking does happen with compiz disabled too though. I'm almost certain that it's something to do with the 'scheduling' of Linux, and that it's software related somehow.

Specs:
Athlon X2 6000 3.1ghz dual core
2gb memory
video card: nvidia geforce fx5200 PCI (note: I think the PCI bus might be causing a bottleneck).

I'm gonna upgrade to a much better PCI express graphics card next month, I'll see if it still happens then.

---

### Post by sebbouckaert on 2010-03-04
This is the kind of thread I wish would have more posts right now. 

See, I'm having exactly the same annoying behaviour lately. I used to play mp3's flawlessly with rhythmbox on an Asus eee 900 netbook (normally this device is strong enough to perform such a task). However recently I'm having these CPU spikes once every half a minute making the music stutter and skip, even when no other app is running exept rhythmbox. 

Tonight I was fed up, did a clean install of Karmic hoping to fix this, but still the same, aargh!! 

I'm puzzled why this suddenly acts up whereas everything used to work fine, my notebook was hooked up to the stereo downstairs doing just fine.

I'm streaming my music from a nfs server but the other (wireless) pc's are doing ok, so I doubt this is the issue.

Could this have something to do with some update (kernel or other), or is pulse acting up again?

I really can't seem to find what is causing these spikes, and quite frankly, after a complete reinstall of the OS this is one of those moments Ubuntu is really driving me nuts!

Any ideas? thanx

---

### Post by ngrieb on 2010-03-04
I was having problems like this too, but it is XOrg that sometimes randomly spikes for me. 

There was an update for Rhythmbox a few weeks back that helped considerably with the loading of my library, but I keep getting an mp3 demuxer error, which annoys me and prevents Rhythmbox from reading iPod format (mp4 or AAC, whatever iPods play) songs. 

I have found that Audacious has preformed the best for me if (you are interested in it, and don't have wav formatted music) especially when loading large playlists.

---

### Post by no2498 on 2010-03-04
try this you can undo it the same way if it does not help

i have a dell that wile its just setting still was running hot up an down fan speed

open a terminal type  ( gstreamer-properties ) click enter
click video set the plugin to (  x window system (no xv)

if you need to install gstreamer do it in add/remove

i think you need to restart the computer

hope this helps

---

### Post by sebbouckaert on 2010-03-05
Ok here's an update on the issue:

Running ```
top
```shows a process named ```
phy0
``` popping up every minute or so. This spikes up the cpu and therefore makes the sound stutter. It seems this is some process coming from the wifi driver of the eee 900. This bug seems to have gotten worse since last driver updates. That's a bummer. I'm going to find out some more about the driver. Keep you posted.

Any other owners of this wifi device affected by this?

---

### Post by sebbouckaert on 2010-03-05
Confirmation of the fact that the wifi driver was the problem. Seems like I traced the bug:

[https://bugs.launchpad.net/pulseaudio/+bug/293453](https://bugs.launchpad.net/pulseaudio/+bug/293453)

Workaround (for all affected with Atheros wifi cards) was to install the madwifi driver following these instructions:

[http://ubuntuforums.org/showthread.php?t=1309072&page=8](http://ubuntuforums.org/showthread.php?t=1309072&page=8)

madwifi replaces default drivers and now the phy0 process is gone, so are the CPU spikes and thus no more audio stutters or skips. :D

Hope they can fix this in the official 9.10/10.4 driver version.

---

### Post by bomgd3 on 2010-03-07
Bump.  I'm having a similar issue, but I'm on a Thinkpad T61.  The most recent update seems to have messed up my system badly.  My system monitor shows a nice little sine wave of my CPU going up and down constantly!

---

### Post by sebbouckaert on 2010-03-08
What do you see pop up when you run top in a terminal, when your system moniyor graph shows the cpu peak?

---

### Post by TenPlus1 on 2010-03-08
Try this: [http://ubuntuforums.org/showthread.php?t=1400798](http://ubuntuforums.org/showthread.php?t=1400798)

---

### Post by sebbouckaert on 2010-04-09
FYI: still the same issue on Lucid beta2 i386 on my Asus eee 900 :(

---

