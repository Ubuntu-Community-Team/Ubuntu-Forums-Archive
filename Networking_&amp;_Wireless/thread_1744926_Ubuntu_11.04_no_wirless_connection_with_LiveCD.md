---
title: "Ubuntu 11.04 no wirless connection with LiveCD"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by cx1964 on 2011-04-30
For upgrade-check I used today Ubuntu 11.04 X64 LiveCD om my Sony Viao VPCF13Z1E Laptop to check if all my hardware can be used with Ubuntu 11.04.

When Ubuntu 11.04 X64 LiveCD was started I could connect to my network with my wireless network adapter. But when I tried to browse with Firefox
I could not get a connection. A ping to my router or to an other machine did neither work.
 
To browse the internet with Firefox and a wired connection works normally.
When I use Ubuntu 10.10 X64 on my laptop the wirelss connection works normally.

The command lspci | grep -ni network on my Sony laptop responds with:

23:02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

I use a wireless connection based on wpa/wpa2

Connection information from Ubuntu 10.10 X64:

Interface 802.11 WiFi (wlan0)
Driver iwlagn


Does anyone have an idea how to solve this problem?
Or do I have to report a bug?

---

### Post by mdlavin on 2011-05-01
I have the same problem on my Thinkpad W510.  I have the same wireless card, Intel Corporation Centrino Advanced-N 6200 (rev 35), and I noticed that I can connect to my router if I re-configure the router to use B/G mode only instead of allowing 'N' mode.  

This isn't a real solution, but it's a possible workaround while a proper fix is being created.  I think a bug should be created, but I have to stop using the computer to watch my kid.  I'll open a bug later today if one hasn't been created by then.

---

### Post by cx1964 on 2011-05-02
If I use my router in "Mixed 802.11g and 802.11b" mode instead of 
"Mixed 802.11n and 802.11g and 802.11b" (my default setting) my wireless connection of my LiveCD on my Sony vaio Laptop also works normally.

Thanks for your help.

Did you report the bug?

---

