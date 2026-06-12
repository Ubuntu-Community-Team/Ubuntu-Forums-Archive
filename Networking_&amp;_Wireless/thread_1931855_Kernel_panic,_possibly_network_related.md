---
title: "Kernel panic, possibly network related"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by dave0109 on 2012-02-26
I just had 2 instances of a kernel panic in what appears to be a replicable event, at least on my machine. I'm running the 64-bit version of Xubuntu 11.10, with the Ralink wireless driver source from the Ralink website, built and installed locally.

I'm currently sharing my wired connection with a Windows XP machine that I'm setting up for a friend.  On that machine I've been downloading stuff successfully enough, except on this occassion when I tried to download evince for Windows via the Gnome site.  When I clicked on the link in Firefox on the Windows machine, the Ubuntu machine blew out.  The stack trace hinted at some networking stuff, which made me wonder about the download.

When the machine came back up, I tried to do the download again, and again got another panic.

So this time after rebooting, I downloaded the file on the Ubuntu machine, which came down OK.

I noticed the download was an FTP one, so after I've posted this, I'll have a go at other FTP links, but it's going to take someone with more knowledge than me to track this to the root cause.

Anyone have any ideas for me to try?

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"xxxxxxx"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: xxxxxxxxx   
          Bit Rate=216 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-72 dBm  Noise level:-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

