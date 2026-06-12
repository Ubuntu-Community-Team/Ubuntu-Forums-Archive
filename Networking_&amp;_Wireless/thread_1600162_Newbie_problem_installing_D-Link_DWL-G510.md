---
title: "Newbie problem installing D-Link DWL-G510"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by orchardstreet on 2010-10-18
Greetings.  I'm new to Linux and wireless so bear with me.  I have installed Ubuntu (10.4) on a friends machine.  The install was great, no problems.  I plugged the machine into my wired network and it connected immediately.  However my friend has a wireless network..........  I did some research on the forums and found that a D-Link DWL-G510 card was supported and I think the page said "works out of the box"
 
Having purchased the card I read the install guide.  It cautioned against plugging the card in until the CD had been inserted and the wizard started.  When I inserted the CD nothing happened other than an icon appearing on the desktop (no Auto run?)  I clicked the icon to see the contents of the CD.  I could click on various .exe's but all I got was an error message each time.  
 
"Archive: /media/DWL-G510/DWL-G510.exe 
[/media/DWL-G510/DWL-G510.exe] 
End-of-central-directory signature not found. Either this file is not 
a zipfile, or it constitutes one disk of a multi-part archive. In the 
latter case the central directory and zipfile comment will be found on 
the last disk(s) of this archive. 
zipinfo: cannot find zipfile directory in one of /media/DWL-G510/DWL-G510.exe or 
/media/DWL-G510/DWL-G510.exe.zip, and cannot find /media/DWL-G510/DWL-G510.exe.ZIP, period."
 
However the CD is not faulty as I tried it on my Windows 7 PC and everything was fine. 
 
I could not find a way to enable auto run in Linux.  My question is:  should I ignore the manual and just install the card and see what happens?  Under Windows this would bring up the "found new hardware" wizard and install the drivers automatically, what happens under Linux?
 
Any advice greatly appreciated.

---

### Post by chili555 on 2010-10-18
Please see here: [http://www.linuxquestions.org/hcl/showproduct.php/product/2115/cat/133](http://www.linuxquestions.org/hcl/showproduct.php/product/2115/cat/133)

There are apparently three versions of this card. Please install the card and run:```
lspci -nn
```We will then have information that will tell us what version you have. Two of the versions have drivers built in!

---

### Post by orchardstreet on 2010-10-19
Thanks chili555.
 
The information from the system is:
 
Network controller [0280] RaLink RT2561/RT61 rev B 802.11g [1814:0302]
 
However I suspect that all is well. After installing the card I opened Devices-Network Tools and found under Network device, Wireless Interface (wlan0) under Interface Information I find the correct MAC address, multicast: Enabled MTU: 1500, State: Active.
 
As I do not have a wireless network I can't do any configuration (that will be up to my friend) but it looks to me that it has installed OK.
 
Thanks again for the help, if there are any future problems I'll post again

---

### Post by chili555 on 2010-10-19
> it looks to me that it has installed OK.Looks that way to me, too. I am confident that, once you are near a wireless network, it will connect.

---

