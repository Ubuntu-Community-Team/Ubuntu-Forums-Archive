---
title: "No wifi signal found"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by mdock2003 on 2010-12-07
I just installed 10.10 on a Dell Inspiron 1300. The wired connection(eth0) works fine but I get no wireless signal when I unplug and try to connect to my network/internet. It shows that wlan0 does exist but it gets no signal. I've used the rfkill to make sure that it wasn't blocked and everything seems to be ok, except I get no wireless signal. 

I uninstalled Network Manager and installed Wcid and it found nothing. I even tried installing several signal scanners I found in the package manager. I've removed, updated and reinstalled the broadcom drivers. I still get nothing. The wireless signal from my router is nonexistent according to Ubuntu.

The wireless works fine when I put my windows XP HD in and it also works fine when I put my Mepix or PCLinux OS HDs in the laptop. So I know that the wireless card is not busted. 


Someone please help, I'm stumped and have no idea what else to do.

---

### Post by mdock2003 on 2010-12-07
today no network connection. The eth0 and wlan0 are both not connecting. 
I run all the various rfkill commands and get nothing.

---

### Post by dandnsmith on 2010-12-07
Have a hunt (on this site, for a start) for mentions of broadcom and problems - I think I remember one a couple of days ago, with a suggestion to remove the linux drivers and use the Windows inf file (via ndis...?)

[ this post ](http://ubuntuforums.org/showthread.php?t=1617380) goes further, and tells how to fix (one) failing broadcom chipset.

---

### Post by mdock2003 on 2010-12-13
I figured it out. I had to uninstall the driver and install a new one. once I did that I worked just fine. 
I searched the forums/site and did everything mentioned, but none of those drivers worked. I actually found the correct one by mistake.

---

