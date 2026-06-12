---
title: "Xorg change to conf file, no change to performance?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by TAFKARS on 2009-03-25
Just a general query. I was having trouble with huge loss of CPU performance, which, following a search, turned out to be a problem with the Xorg configure file. I changed it as below and now get the warning on booting up my laptop that I am running in low-graphics mode, but I have not noticed any difference (apart from the now normal CPU usage).

What sort of compromise have I made on performance, and to what applications would this now affect?

Appreciate any comments!

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 IGP]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option "EnablePageFlip" "true"
        Option "RenderAccel" "true"
        Option "XAANoOffscreenPixmaps" "true"
        Option "AccelMethode" "EXA"
EndSection

---

### Post by markbuntu on 2009-03-26
What does the /var/log/Xorg.0.log have to say, in particular any WW or EE messages?

---

### Post by TAFKARS on 2009-03-27
Thanks for the reply, will check this when I return home and post.

---

### Post by TAFKARS on 2009-04-01
Apologies for the delayed response.

The only warning on the Xorg.0.log is as below:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.

There is another file called Xorg.0.log.old, and the warning is the same on this one.

Since taking this action I have noticed that The boot time has increased, and that sometimes booting fails, citing something like 'error when searching for drive....', but I cant remember exactly. If it continues I'll perhaps post elsewhere, but powering down and then switching the machine on immediately seems to do the trick.

Appreciate any comments, thanks.

---

