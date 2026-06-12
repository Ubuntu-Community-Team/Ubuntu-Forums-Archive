---
title: "printing over wireless through port 9100 stalls"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by edgar_knarretje on 2009-06-17
Hi All, 

I have connected a canon 610 printer via a wireless printer server to my network. On of the servers in the network is Windows XP and I have shared a the canon printer using the (windows!) printer driver and (windows!) printserver driver. On my (beloved) ubuntu laptop I use SMB:// printing and that works. Not fast, but it works... So far so good... :) 

Now comes the tricky part. The printer server (sitecom wl-201) also supports printing through port 9100 (appsocket/hpjet direct). That way I can bypass ye olde windows. Whatever I do: the printing stalls after 30 secs. I have a standard cups (1.3.7) from ubuntu hardy 2.6.24-24-generic. Linux drivers for the printer are all correct, since I can print through SMB... All the parameters are the same, except for the device URI of course... btw: the print test page prints correct...

I traced the ethernet packets, since I suspect some buffer overrun or protocol error. This trace can be made available to anyone who likes to inspect it... (I will post it on request)

My questions:
- anyone experienced this problem before?
- any suggestions for a next step?

Since... I feel a bit stalled myself ;)

regards, -- @gar --

---

