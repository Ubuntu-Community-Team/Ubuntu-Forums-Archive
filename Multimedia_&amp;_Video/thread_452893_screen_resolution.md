---
title: "screen resolution"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by jameslee on 2007-05-23
Hi I just installed Feisty Faun, and my screen resolutions is all messed up.

i tried to edit my xorg.conf file but when i do change the screen resolution to 1680 x 1050

the resolution is all messed up and the bottom of the screen is all cut up.

I added the HorizSync and the VertRefesh as instructed from a different post, but the screen resolution is not correct. 


Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync     	31-81
	VertRefresh     56-75
Modeline "1680x1050@60" 134.32 1680 1712 2216 2248 945 964 973 993
EndSection

has any one else got this ?

my monitor is a samsung SyncMaster215tw 

thanks

---

### Post by veloce on 2007-05-24
Need a lot more info to help with that.  To start with, what graphics card are you using.  Have you tried the screen resolution howto?

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

