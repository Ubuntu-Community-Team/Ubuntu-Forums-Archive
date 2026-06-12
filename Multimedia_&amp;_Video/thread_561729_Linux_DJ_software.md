---
title: "Linux DJ software"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by djuniah on 2007-09-27
Hello, I am a DJ who recently switched my laptop over to linux.  I was looking for good reliable software akin to atomix's Virtual DJ.  I tried Mixxx and a few others listed here ([http://sound.condorow.net/ddj.html](http://sound.condorow.net/ddj.html))  but none of them really provide the reliability and stability that VirtualDJ did.  I tried VDJ in a virtual machine, but the speed on it just cant provide the reliability it had in native windows.  I'm really trying not to dual boot.

So basically, my 2 options seem to be finding a suitable alternative or figuring out how to speed up my winXP Virtual Machine.  (VDJ does'nt run in WINE, at least not well)

Any suggestions would be greatly appreciated.

---

### Post by djuniah on 2007-09-27
ok..im going to try VMWAre instead of virtualbox now and see how that works out for me.  From what i read, its a good deal faster

---

### Post by bladext on 2007-10-12
Hello, can you say if it worked? I'm searching some software like virtual dj por ubuntu 7 but I cant find one :( please giveme a tip :)

Thanx.

(( Blade ))

---

### Post by djuniah on 2007-10-13
sadly, my little laptop just isnt powerful enough to do it with enough stability.  
Heres what i'm doing in the meantime.  My HD on my laptop has somewhat easy access.  I have 2 laptop HDs right now, my main 120GB with ubuntu and all my music, and an older one that has windows and VDJ on it thats 40GB.  When i have a gig i put the windows one in and put my one with the music in an external enclosure.  I then installed the EXT2(3) drivers in windows so it can read the drive.  They are found here:
```
http://www.fs-driver.org/
```

I know this isnt an optimal solution at all, but i had to do it in a hurry and the drive already had win installed.  You could dual boot your system and basically do the same thing.  Also (and i havent tried this yet, but its on my list of things to do) you could install windows to a USB drive and boot from that when you need it.  I'm not sure how that is going to affect speed or reliability of it, but it shouldnt be too bad.

---

### Post by abhiroopb on 2008-01-16
Since this is Linux you're not going to fin dexactly what u had in windows, just search for DJ in synaptic and see if there is anything good there :)

---

### Post by djuniah on 2008-01-16
Yea, i tried that and there we're some nice offerings, but the sound stability of those apps was a little lacking sadly.  With the other one that i use, no matter what i do, it wont skip a beat or drop the audio under any kind of system load.  I couldnt find one that matched that.  I'm fine with dual booting for that purpose, its not a 24/7 thing so it works out for me.

---

### Post by abhiroopb on 2008-01-16
how much ram do u have? I have 2gb with a 256mb dedicated graphics card and I've been able to run virtualbox (winxp pro) and use photoshop and adobe indesign.

I set virtualbox to use 540mb ram and 32mb video memory, minimum settings for photoshop but this way my ubuntu host system runs fine.

With these sorts of settings I can't imagine having any problems using something like virtualDJ.

---

### Post by eternal-one on 2008-01-16
Been thru all of this myself. Had to accept that a dualboot is still needed. Only thing on my windows is numark cue. Networking disabled. Linux dj apps still suck at the moment and would never rely on one live. Plus my maya44usb is only supported by 2 channels by alsa and firebox seems to be the only good interface that supports 4x4 for timecode vinyl but buggy as hell.

I suggest using Mixxx or a good DJ app under wine (still looking myself) to piss around with while using ubuntu and boot windows if live ....until more audio interfaces/ drivers are supported and maybe a commercial or at least solid dj app comes out for linux.

---

### Post by djuniah on 2008-01-16
My lappy just isnt powerful enough to run VDJ flawlessly in a VM.  Photoshop and a few other apps run just fine, but I have to have constant reliability with my DJ software.  I plan on switching over to deckadance soon as well, and the system reqs for that are a little heavier than VDJ, so at this point going into windows seems like the only solution.
    I have a GPU, but its a Radeon 200m, with shared mem (1.25 GB total system mem with 256 allotted to the GPU).  The real issue is my CPU, which is only a 1.6 AMD sempron.  I plan on getting a new laptop by the end of the year, so maybe it will fare better on a new machine.  We'll see.

---

### Post by eternal-one on 2008-01-17
Apparently deckadance is buggy as hell when it comes to track loading...takes a long time to load and there is some kind of difference from how it buffers the track that is no good compared to the others...(I read this somewhere but dont remember details.maybe old news compared to new versions) anyways  I do know VDJ or Numark Cue (exact same software) are super-stable by experience. Mixvibes apparently is the best for latency compared to serato, vdj, and traktor, but I've never used this app either.... 

Completely off-topic (sry) but I must note I installed FL Studio 7 and Zero-X beat slicer using wineasio and almost pissed myself when the heavy demo song in FL7 played fine with no lag on a cheap $5 USB c-media sound plug...I could even turn the latency down!!

---

### Post by t3tech on 2008-01-28
You might want to try switching to the Ubuntu Studio version in any case. It gives you a low latency kernel which is better suited to sound apps and would probably give better stability. I've been out of dj'ing for quite a while and for the last couple small gigs I did as favors I just used Amarok and a CD deck.
Here's a couple links to check out though.
[http://sound.condorow.net/ddj.html](http://sound.condorow.net/ddj.html)
[http://www.hitsquad.com/smm/linux/DJ_MIXING/](http://www.hitsquad.com/smm/linux/DJ_MIXING/)
[http://www.ultramixer.com/](http://www.ultramixer.com/)

---

### Post by brw02005 on 2008-01-28
Well if you can't beat it run it.  Looks like version 4.2 of the program runs under wine.

apt-get install wine

then just click on the installer

check the site for compatibility looks like it works up to version 4.2 for sure.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1704](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1704)

---

### Post by djuniah on 2008-02-01
I appreciate the effort brw02005, but if you read my first post, I tried wine and even though it does run (quite well actually) It is EXCEEDINGLY slow, upwards of 4 minutes to load a track. (with the audio skipping the entire time)  And that isnt acceptible for use at a live performance.

EDIT: I've tried tweaking it, but it sadly is still not fast enough with just about everything disabled to be of any use.

---

### Post by jnbptst on 2008-02-13
I'm a laptop-based DJ, I use Virtual DJ with Vestax VCI-100

for now it seems only dual boot will do. I haven't tried it but I suspect virtual machines are not able to handle MIDI properly (anyone can confirm?)

i use linux for everything except the djing in itself

basically i set up my playlists in amarok, then i save them on the FAT32 partition of my internal HD. I restart to windows, edit the m3u file with wordpad to change it to windows format (edit> replace "/media/hda5/" by "D:\" then "/" by "\"). I then load the m3u list onto virtual DJ

it's a pain in the ***, but it works... the thing is, I can't use Traktor, since you can't import m3u lists and you have to manage your whole library through Traktor itself (or iTunes which is a pain too if you're on linux most of the time)

---

### Post by eternal-one on 2008-02-17
If you dont need timecode UltraMixer seems ok.

---

