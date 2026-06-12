---
title: "Playback is choppy"
date: 2008-02-05
forum: Mythbuntu
---

### Post by browndog289 on 2008-02-05
Hello

My mythbuntu system is up and running but when I playback my recordings the video seems to be a bit choppy and seems to be dropping frames. I have tried every setting in TV settings -> Playback.

I find the best setting to be "Standard XVMC" with "Bob (2x Framerate)" deinterlacing on playback and "Use OpenGL for timing". Although the video still seems choppy although not as bad.

My system spec is:

AMD Athlon XP 1600+ Processor
512Mb DDR PC3200
PC-Chips M848A Mainboard
80Gb IDE Hard Disk Drive - For Mythbuntu and system files (Boot Drive)
250Gb SATA Hard Disk Drive - For Recordings (connected through PCI SATA Card)
MSI Nvidia FX5200 AGP Graphics card with TV-Out (Using latest drivers from envy)

All connecting through the TV-Out to a standard Thomson Widescreen TV.

I am in the UK so the TV standard is PAL-I.

I have run hdparm to test the HDD timings and they are:

[IDE HARD DISK - BOOT DRIVE]
/dev/sda1:
 Timing cached reads:   512 MB in  2.00 seconds = 255.76 MB/sec
 Timing buffered disk reads:  170 MB in  3.03 seconds =  56.04 MB/sec

[SATA HARD DISK - RECORDINGS DRIVE]
/dev/sdb1:
 Timing cached reads:   522 MB in  2.01 seconds = 260.28 MB/sec
 Timing buffered disk reads:  216 MB in  3.01 seconds =  71.74 MB/sec

My xorg.conf file is attached to this post.

Can anyone help me get 25fps video so that it is no longer choppy?

browndog

---

### Post by dflipb on 2008-02-19
does it happen if you open the video in vlc?

---

### Post by Levander on 2008-02-19
You don't say what kind of capture card you use.  The only reason I'm interested is because you know you can't do HD with that CPU, right?  I'm not in Europe.  Maybe PAL means that you are only doing SD.

Look in /var/log/mythtv/mythfrontend.log - I bet you have a few places where it says "Prebuffering Pause" it it.  Those prebuffering pauses are what was causing occasional choppylike blips on my myth box.  Note that every line in that log file is time-stamped.  So you can see how often the pauses are happening.

What it was on my machine was that I was using the same drive for both the operating system and for the recordings.  It was just too much for the disk to handle.  Solution for me was to throw a 2nd drive in and mount the reocrdings directory off it, which you've already done apparently.  You're sure the mounting was done correctly?

When I was searching for prebuffering pauses, it turned out there could be lots of causes.  Disk performance isn't the only one.

---

### Post by dflipb on 2008-02-19
The reason I ask is that I was having that same problem, but it went smooth in vlc.  So I thought I should be able to get it working in mythtv.  I just adjusted the playback settings, and magically it all worked perfectly.  the deinterlacing I did was one field so that it dropped the other field and all was right in the world.

I believe you should have no prob playing HD content with those specs. Just make sure your video card is good.  In my rig, I'm using an Nvidia 5500.

---

