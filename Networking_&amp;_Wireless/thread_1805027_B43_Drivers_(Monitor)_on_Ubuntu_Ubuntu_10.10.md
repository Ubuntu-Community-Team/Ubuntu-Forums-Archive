---
title: "B43 Drivers (Monitor) on Ubuntu Ubuntu 10.10"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by MustangGT on 2011-07-15
Hello Everyone,

A while back I went through a lot of work to get the B43 drivers working on my 10.10 Ubuntu.  In an effort to get Monitor mode working with my Broadcom card.  I am a security consolutant and I did not want to by a new netbook nor card.  Injection was working too.

It was working great.  Months later I come back to use it and for some reason I can't get it to work.

It starts out working fine and that lasts about ..... 3 minutes and then it just stops working.  It stops working everytime at about 3 minutes, it will monitor fine .... airodump-ng runs fine, but only for 3 minutes, then nothing.  If I bring the interface down and restart it -- nothing.  I have to do a full reboot to get it working again.

Any ideas on what I might check to locate the issue?

---

### Post by MustangGT on 2011-07-15
Correction... 

I was able to exit airodump-ng, stop the monitor interface..... kick the card out of monitor mode.

Then bring it back into monitor mode, and airodump-ng is working fine now.

This is weird.  It just stopped working after a minute.

---

### Post by atomicben on 2011-07-15
There are a few cards/drivers that don't like scan mode with airodump.

I've experienced this before.  Not with the b43 but with an atheros card.

I know it's nice to scan all channels but try using the --channel switch and selecting a specific channel.

eg:
sudo airodump-ng --channel 6

how long does that work for?  If it doesn't stall/freeze after a few minutes it's a limitation with your driver or maybe your network manager is getting in the way.

For more info see:
[http://www.aircrack-ng.org/doku.php?id=airodump-ng](http://www.aircrack-ng.org/doku.php?id=airodump-ng)

scroll a little more than half way down to
[B]"Airodump-ng stops capturing data after a short period of time"

[/B]BTW: After 2 min you should probably have enough info to choose a target and specify a BSSID and a channel.  It's something I've learned to live with.

---

