---
title: "Noob - Network Manager Intrepid and WPA"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by ubnub1 on 2009-02-06
1.  I am brand new to and totally clueless on this UBUNTU stuff.
2.  I have Ubuntu 8.10 and have run it on my Vista 32 bit machine as a live cd to check out my wireless card (that works in Vista).
3.  I Accessed the Help icon on the desktop and went to the "Internet and Networking" section.  I followed the hints there and ran lshw -C network to find that Ubuntu recognized my wireless card ad an RTL8180 (it's an rtl8185) and was apparently using its rtl8180 driver).  The help text said I should see one of four words (CLAIMED, UNCLAIMED, ENABLED, or DISABLED) - I saw none of those.  I moved on to the next step that was suggested by help for the ENABLED case and ran iwconfig.  That returned what the help text expected, including 'wlan0: IEEE 802.11bg ESSID: "" '.  According to help, this meant I had to configure WPA security (which is the security implemented on my wireless router).
4.  At this point, things got confusing.  The help text said I had to go into Network Manager and configure the security.  There is no "Network Manager"; there IS a "Network Tools", but opening that yields no clue as to how to configure WPA.  The help said that I could also do this manually by clicking on the link to a wiki (which, of course, required a working network connection, which I do not have on that machine - I am typing this on another machine in a nother location).
5.  I seem to be so close yet still far away from getting this done.  Could someone please help me get over this remaining hump?  Specifically, how can I configure the wireless card (that Ubuntu seems to have recognized and installed) so that it can connect to my wireless network under WPA security?
6.  Also, how do I get this "Network Manager" - do I have to actually install Ubuntu on my machine?  I have tried to avoid doing that until I was sure the machine's hardware, etc. will actually work under Ubuntu

Thanks

---

### Post by ubnub1 on 2009-02-06
Solved.  I instlalled the 8.10 version using the wubi installer.  8.10 picked up on the wireless card automatically AND I was able to give it the WPA pass phrase and connect.

It still requires me to connect to the network each time I boot up.

Something that may be obvious to all the experts out there completely eluded me: there is a little icon at the top of the desktop that calls out the network manager.  The instructions I had been following said to go into administration to find network manager.

Now, if I could just find the next obvious thging and that is how the hell do I tell this forum that the issue is resolved?

---

### Post by da mono on 2009-02-06
in thread tools

---

### Post by superprash2003 on 2009-02-07
i think. the SOLVED feature is still suspended..

---

