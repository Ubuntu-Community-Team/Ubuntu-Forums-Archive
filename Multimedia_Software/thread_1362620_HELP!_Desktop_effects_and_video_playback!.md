---
title: "HELP! Desktop effects and video playback!"
date: 2009-12-23
forum: Multimedia Software
---

### Post by Haitoyou on 2009-12-23
Hello everyone! I gotta say I love these forums. Most of the problems I've had with Ubuntu were solved with a simple search of this site and I am grateful that there are so many people willing to help around here.

I fear that I may need some big guns for my current problem/s:

I have a P4 desktop computer with a Radeon HD 3650 AGP video card. I am having all sorts of video playback problems with the card as well as enabling compiz graphics. This is what I've done so far and where it goes wrong:

**What I've done so far that works**:
[LIST]
[*]Fresh install of ubuntu 9.10 into a single hard drive.
[*]blacklisted the wrong driver for my rt2870 wifi card
[*]enabled wifi, and went online and updated everything
[*]installed ccsm
[/LIST]

**Where it goes wrong**:
[LIST]
[*]installed ati LINUX driver release 9.12 (also tried 9.11) but can not enable effects
[*]decided to use the ati driver located in ubuntu hardware drivers and effects can now be enabled yay! BUT WAIT! Now video playback is painfully slow, messed up, etc. My computer acts like it is struggling to manage playing the video even if not in full screen mode. I know this can not be the case because I've had windows installed on this computer before and it was able to play video fine without bringing everything else to a halt.
[*]disabled desktop effects and poof! everything is smooth again! BUT WAIT! Video playback has some pretty bad horizontal tearing that won't go away!
[/LIST]

Believe me when I say that I've searched for this topic already and tried setting ccsm's sync to vBlank enabled as well as manually setting 60hz. It did not fix the problem. Is this because ccsm is not enabled unless I have at least some desktop effects enabled?

Someone please help me with this problem.

---

### Post by Haitoyou on 2009-12-23
I'll post a summary on my setup:

-P4 processor, radeon HD 3650 AGP video card
-ubuntu 9.10 installation using safe graphics driver
-setup wifi rt2870 card and got online, did software updates
-tried installing ati linux driver 9.11, 9.12, but can not enable effects
-installed proprietary hardware driver found in hardware drivers
-video playback (vlc) with normal desktop effects enabled is horrific
-video playback with desktop effects disabled is ok, but horizontal tearing makes fast moving scenes unbearable
-changed ccsm sync to vBlank to enabled and disabled automatic detection of refresh rate, manually put 60hz
-MEOW!

---

### Post by Astrals on 2009-12-24
I had a similar problem with display getting lines through it, i also use ati radeon hd cards. I also use asus 22 inch lcd.
End result for me was that the lcd scaling chip was failing, lcd about 6 months old.
I not saying this is your problem with the horizontal lines but do take this into consideration, i was lucky enough one of my friends has the same monitor, so we tested them both on each system to find this issue.
I hope this is of some help to you.

---

### Post by Haitoyou on 2009-12-24
I have my computer connected through a DVI-to-HDMI connector into an HDTV. The resolution is 1920x1080@60hz. Meow!

---

### Post by Haitoyou on 2009-12-25
Update:

Ok I re-installed ati's 9.12 linux driver after removing everything else, and disabled desktop effects. My avi video in VLC is still doing some bad horizontal tearing. I also just noticed that if I try to play a video on youtube in HD my computer starts going into heart-attack mode and everything slows down and becomes nearly unusable. What the heck is going on?

Anyone got any ideas?

---

### Post by Haitoyou on 2009-12-26
Video playback is painful to watch :(

I really don't want to have a dual boot solution with windows xp just to watch movies. Someone please help me fix the horizontal tearing and the horrific desktop effects problem I am having.

---

### Post by kopiwe on 2010-01-30
Did you install the proprietary driver *(I believe for ati it is fglrx)*  through ubuntu's hardware driver manager?[I]
(System -> Administration -> Hardware Drivers)[/I]

If not, do that. 

Then install CompizConfig Settings Manager to enable VSync, which should help in the case of [Screen Tearing]("http://en.wikipedia.org/wiki/Screen_tearing"). 
```

sudo apt-get install compizconfig-settings-manager
```Open: CompizConfig Settings Manager: (System -> Preferences -> CompizConfig Settings Manager)
Find: General Options - Display Settings
Change:

[LIST]
[*]"Sync To VBlank" to "enabled"
[/LIST]
restart X.

Hope this helps

Update: Just noticed you already did that like your post suggested, however for the compiz vsync setting to work, desktop effects need to be enabled.

---

