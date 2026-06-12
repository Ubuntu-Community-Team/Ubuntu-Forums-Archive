---
title: "WUSB600N Can sell all networks but my own"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by DijitalX on 2011-01-04
machine has Ubuntu 10.04.  

So I plugged in my WUSB600N and behold, it worked.  I can see all networks .... except my own.  Here is what I've done:

1) reset router
2) changed ESSID
3) changed the channel for 2.4ghz
4) I've compiled the driver rt3572sta that is on most of the posts that I've found via Google.  I completed all steps except for "sudo modprobe rt3572sta". When I try that I get an error 

> FATAL:  Error inserting rt3572sta (/lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/rt3572sta.ko): Device or resource busy

5) I've rebooted the machine into a CD version of Ubuntu and rebooted back to the copy on the machine and tried to insert again, no go.

6) I've taken the WUSB600N and plugged it into my ubuntu laptop (running 10.10 Maverick) and it works perfectly fine.  I can see my home network, connect to it, etc.

I'm at a loss.  I've considered upgrading to 10.10 on my desktop but not sure if I have an ethernet cable that long and have been avoiding it.  Any suggestions?

---

### Post by DijitalX on 2011-01-04
I found a long ethernet cable and updated to 10.10.  The network shows up fine.  Odd.  This doesn't necessary solve the actual issue, it's more of a work around, but for my case it is solved.

After doing the update I found that my connection would last for 5 minutes at the most and then would disconnect and just keep asking me for my auth code.  I saw that another user on here had a similar issue and was able to resolve it, he sent me the other key to the puzzle and it fixed my wifi issues for good.

Thanks to **themusicalduck** for this information:

> sudo gedit /etc/modules 

remove any lines relating to other drivers and he also added a line with "rt3572sta" to the end of the file, but it isn't certain whether that is actually necessary or not.

Then:

> sudo gedit /etc/modprobe.d/blacklist.conf 

add (at the end)
> 
blacklist rt2800usb
blacklist rt2800sta
blacklist rt2800
blacklist rt2870
blacklist rt2870usb
blacklist rt2870sta


I ran my machine for 12 hours and the wifi never went down after this.

---

