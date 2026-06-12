---
title: "Is Ubuntu crashing my router??!"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by Jimstehrman on 2012-09-18
Hey guys,

I have had a strange problem with my internet for the past week or so.
Last week I moved back into my group house after having been away for a while, and we all noticed that the internet was pretty bad. It seemed that I could never get more than 5 or so minutes before the router would seemingly begin a reboot cycle.
I thought that this was due to a faulty modem, and out landlord ordered a new one. It just came in and I set it up using my machine. It dual boots Windows 7 and Ubuntu 12.04. Since there was some software involved I booted into windows 7 to set up the router and it seemed to work fine. As soon as I tried to get on the web after booting into Ubuntu 12.04, the new router did the exact same thing that the old one did.
I'm writing this now from windows 7 and so far the internet seems fine.
I'm pretty puzzled by this and have really no idea how ubuntu could be crashing my router, but it seems that whenever I try to access internet from ubuntu, in less than 5 minutes the router fails.
Any thoughts or ideas?

Some more context, I was living in this house last semester (Jan-April) and running ubuntu 11.10 and 12.04 with no issues on the old router.

---

### Post by iponeverything on 2012-09-18
I have seen the like behaviour with mixed mode. To test -- set the router to "n" or "g" only -- - if it becomes stable - play with different combinations.

---

### Post by Jimstehrman on 2012-09-19
can you give a bit more explanation on this? I'm not sure what those things mean.
Sorry and thanks!

---

### Post by Statia on 2012-09-19
The WLAN settings: 802.11n or 802.11g or mixed mode.
You should be able to find those settings in your router's administration console.

---

### Post by Bucky Ball on 2012-09-19
Is this a new modem/router, a new modem, a new router or a new modem *and* router? Is anyone else in the house running Ubuntu and do they have a similar problem? If not check how they have their wireless setup.

If the router has not been changed; I had a problem with a dodgy power supply on a router. To awhile to figure it out. It was old and dying. Replaced it and the router was fine.

---

### Post by Mark Phelps on 2012-09-19
Most likely, the only Windows software activities will be to provide an interface for configuring the router -- which you can do by opening a Browser and pointing it to the router.

The Windows software does not RUN on the router, so apart from changing the settings, it does not affect it in any way.

Same is true of Ubuntu.

So, if there are problems using Ubuntu, it's not the router itself as it looks the "same" to Windows and to Linux.

---

### Post by Bucky Ball on 2012-09-19
[I]Thread moved to [B]Networking & Wireless

[/B][/I]> **Mark Phelps said:**
> Most likely, the only Windows software  activities will be to provide an interface for configuring the router --  which you can do by opening a Browser and pointing it to the router.

The Windows software does not RUN on the router, so apart from changing the settings, it does not affect it in any way.

Same is true of Ubuntu.

So, if there are problems using Ubuntu, it's not the router itself as it looks the "same" to Windows and to Linux.

+1

---

### Post by Jimstehrman on 2012-09-19
Thanks for the replies guys,

more info:
first of all, sorry for the confusing wording, there was no modem involved, the case relates only to an old and a new thomson router.

second, i have three machines running ubuntu, one with 11.10, another testing 12.10, and my main one running 12.04. the 11.10 and 12.10 both can connect to the internet fine, and have no impact on the router. 
I put 12.10 on my main machine (the one that I suspect is crashing the router with 12.04) and it can access fine with no issues. So then I loaded 12.04 on a pendrive and booted my main computer from that. Trying to access the internet crashes the router.
I also then tried an old install of 12.04 I had on my testing machine and it also crashed the router.

As for power supply, I don't think it's the issue, a new one came with the new router.

Still very puzzling...and inconvenient. Does anyone have any idea what would be different between 12.04 and 11.10 or 12.10 that would cause this?

Also I went into my routers admin page, and it is supremely unuseful, I cant seem to find any WLAN settings.

---

### Post by BrianBlaze on 2012-09-19
I am assuming it is a modem/router from your landlord or ISP, and I am thinking this sounds like an overheating thing so if they replaced the modem with the same modem it could have the same problem... My ROUTER used to do this constantly until I got a cooling pad for it...

---

### Post by mevun on 2012-09-19
I will note that typically if you reboot an OS, then the computer will  use the DHCP protocol to get an IP address from the router.  It is quite  possible that the DHCP packet sent is different in each version of the  OS and maybe the router crashes because of that difference.  It is also  possible that the router simply does not properly handle a new DHCP packet for a computer that it thinks already has an IP address (meaning it didn't expect the reboot.)   From the router's point of view, your PC was already given an IP address and suddenly  it wants a new one again.  The router might have a bug that does not  handle this case properly.  Meaning that the bug is in the router and  not the PC.  So that's what you need to figure out by trying different  combinations and sequences of events.

I think you will need to run some potentially time consuming tests with sequences of router reset and computer reset and possibly changing the OS version.  Basically, you MAY have to run combinations of OS versions AND try a sequence of whether the router or computer is reset first.

BTW, it is possible to check for differences among the DHCP packets among the OS versions.  It is less time consuming for a experienced network person, but maybe not for you if your network knowledge is limited.  If you really want to, search for "tcpdump dhcp protocol".  You'd also have to enable/disable the network to get the packet exchange, because it is probably enabled already at startup.

Also maybe less time consuming is googling for your specific router and any crash reports for it.  Obviously, it is a bug in the router (because a malformed packet from an OS should not crash it).

---

### Post by Bucky Ball on 2012-09-19
Obviously isolated to 12.04. As mentioned, have you right clicked Network Manager icon, been into 'Edit Connections' and compared the setup there with the one in 11.10 or 12.10 to see if they're the same?

---

