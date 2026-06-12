---
title: "Belkin Wireless 54G Notebook Card help"
date: 2006-05-27
forum: Networking &amp; Wireless
---

### Post by starfire1983 on 2006-05-27
I've read around and know I need the drivers for this card (F5D7010 rev 5000)to work properly under NDISwrapper but I have one slight problem. I lost the installation CD and the driver download from Belkin's site is a self-extracting exe so I can't find where it extracts on Windows. Anyone out there got any solutions or maybe send me the driver file(s)/zip of the install cd?

---

### Post by spd106 on 2006-05-27
Try searching for bcm* 
You need to find to find the .inf and .sys files should be something like bcmwl5,inf and bcmwl5.sys. Under win2k they're in c:/program files/belkin/belkin...utility/drivers/ or something like that.

---

### Post by starfire1983 on 2006-05-28
I don't think my revision uses the Broadcom chips since I just noticed that I have an Atheros service in Windows. Its using an Atheros chip. And the inf and sys files aren't in the Belkin directories.

---

### Post by Joeagain on 2006-05-28
Hello,

I used unzip on the Belkin setup.exe, (forget where I read that this works), and it extracted all the files.

It was for the driver for F5D7000, but it will probably work for yours as well.

Joe.

---

### Post by Joeagain on 2006-05-28
I just tried it (typed in a command line: "unzip F5D7010_V5000.EXE" obviously without the quotes) on what I think is the driver for your model.  This is the name of the file I downloaded:

F5D7010_V5 Wireless Notebook Network Card
Description:	F5D7010_V5 Wireless Notebook Network Card	
Release Date:	12/27/2005	
Files:		
Filename:		F5D7010_V5000.EXE
Size:	 	13.4 M


It made a directory named "Driver" and in that directory there were files named:

BLKWGN9x.sys
BLKWGN.cat
BLKWGN.INF
BLKWGN.sys
Driver.2k
Driver.98
Driver.ME


Which I think are the ones you need.  Good luck, I hope that's it.

If you need, I can email the expanded files to you.


Joe

---

### Post by starfire1983 on 2006-05-29
Sweet! Thanks guys, I didn't even think to do that! I'm in Windows right now and opened up the EXE in WinRAR and extracted the files I need to my jump drive. Thanks for the offer and help, Joe. Now to go look up guides to getting WPA Supplicant to work.

---

### Post by starfire1983 on 2006-05-30
Well, now that I have the drivers installed with NDISwrapper and it says the hardware is present, how do I go about getting a PCMCIA card working and powered up? I have zero experience with this. The lights don't come up at all. An lspci reveals that it acknowledges the hardware is there but as far as hardware goes installing the driver and knowing it's there is as far as I know how to do. Any help is appreciated.

---

