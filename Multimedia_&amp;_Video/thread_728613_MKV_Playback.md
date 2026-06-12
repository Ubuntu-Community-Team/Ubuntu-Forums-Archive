---
title: "MKV Playback?"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by jon_herr on 2008-03-19
My system specs...

Ubuntu v7.10 AMD64, and 32 Bit
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Nvidia Drivers on SLI'd 7600s
4GB of DDR, dual channel RAM @ 400MHz

I can't for the life of me get .mkv files to play without lag, frame dropping, or skipping.  I've tried VLC, Mplayer, Smplayer, xine, etc.  

This same computer is quadruple booted with Windows XP, Windows Vista, Ubuntu v7.10 32 bit, and Ubuntu v7.10 64 bit.

I can play .mkv files without issue in each different copy of WIndows - so I don't think this is a horsepower issue.

What should I do to play these files?  Is it even possible in Ubuntu?

The codec listed in 'media info' for one problem video is "AVC1"

Is this a DMA issue?  Driver issue?  Codec issue?  

Thanks,
Jon 

BTW: I'm a huge Ubuntu Fan and user - please help me get Windows off of my boxes!

---

### Post by uberlube on 2008-03-19
Have you installed the restricted extras from the repositories?

---

### Post by jon_herr on 2008-03-19
I've installed the restricted extras - but they aren't needed for VLC to play .mkv files...

Since my first post - I've figured out that the videos play much better (but not perfect) in a Windows Virtual Machine using Innotech Virtualbox.

This tells me that there is a fundamental problem with the codecs or some other optimization.  

How can this be?  Isn't a native X session using VLC player 'closer' to the hardware than a Virtual machine?

---

### Post by rvm4000 on 2008-03-19
Did you install the w32codecs package?

---

### Post by disturbedite on 2008-03-19
they work fine for me & always have with kaffeine & smplayer and i'm on a 4 year old PC.

---

### Post by jon_herr on 2008-03-19
Ok...  proved that the hardware CAN play the videos - using CoreAVC in Windows.  

[http://www.coreavc.com/](http://www.coreavc.com/)

Now I'm off to see if I can get this codec to load in Ubuntu.  

I thought this was a codec issue!  

Jon

---

### Post by shirilover on 2008-03-20
If you are using VLC or MPlayer, it is not a codec issue.
By chance, are using a composited desktop(desktop effects, beryl, compiz-fusion)?
If so, try disabling destop effects and playback will improve.

---

### Post by ericesque on 2008-03-20
I know you've tried VLC and mplayer, but I thought I'd throw out my observation that MKV plays much better in mplayer than in totem.  I have an older system (replacing it in May!!) that comes to a grinding halt on MKV in totem, but mplayer is smooth as silk...

---

### Post by jon_herr on 2008-03-20
I have tried with desktop effects on / off without any difference.  From what I can tell it's a codec issue - since there is such a reference to using "COREAVC" in place of specialized hardware for playback.

[http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/)

and I quote: "CoreAVC is a proprietary Windows codec for H.264 video decoding. It is much faster than any currently available open-source codecs."

My limited testing verifies that this is absolutely true.

When I get a chance, maybe tonight, I'll try this:
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

The difference between my experience and others with MKV / H.264 playback must be the resolution I'm trying to play.  It's 1080P L4 of the standard - which from what I gather is a challenge.

Jon

---

### Post by shirilover on 2008-03-20
I have used the patch from the link in your post, but I could never get MPlayer to actually use the coreavc decoder.

The quote from the site is somewhat misleading. All coreavc does is decode avc video streams; whereas, libavcodec has a lot nore to do.

Even with your current setup, you're probably pushing the limits to get smooth playback of a 1080P AVC video.

---

### Post by x0d on 2008-05-06
I've been trying to figure out how to play mkv files properly.  This box is powerful enough but I couldn't get mkv's to play without skipping and/or the color hues being way off.  I tried a bunch of different codecs and players to no avail.  They were unwatchable.

After stumbling upon this thread, I went ahead and shut off compiz-fusion by going to System / Preferences / Appearance and selecting the "Visual Effects" tab.  I selected the **None** button and the desktop flickered for a sec and things got flat.  I went ahead and tried a random .mkv file and it ran perfectly.  All .mkv files that I have tested so far run without a glitch.  With compiz-fusion shut off I can watch .mkv videos, and when I'm done I just go ahead and re-enable **Extra** in "Visual Effects".

tHx.

---

### Post by x0d on 2008-05-06
OK, so I wanted to make a couple of launchers (shortcuts) for quickly switching compiz-fusion on and off so I can watch .mkv files at my behest.

I created the launchers by going to System / Preferences / Main Menu.  From there I selected the directory "System Tools" and hit the 'new item' button (it has the big plus sign on it).  
I went ahead and named the first one *Compiz - Enable* and in the Command field I put **compiz --replace** then hit the OK button.  
Repeating the process to create a second launcher which I named *Compiz - Disable* and in the Command field I put **metacity --replace**

Now it's even easier for me to switch compiz on-and-off.

---

### Post by x0d on 2008-07-11
Fusion-icon is even better for switching fusion on-and-off.
It's in the repositories, search for **fusion-icon** in Synaptic or just launch a terminal window and type the following:

sudo apt-get install fusion-icon


[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)

---

