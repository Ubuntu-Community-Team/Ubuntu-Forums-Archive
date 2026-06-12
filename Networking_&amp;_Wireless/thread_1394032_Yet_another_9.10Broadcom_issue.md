---
title: "Yet another 9.10/Broadcom issue"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by blufindr on 2010-01-30
I was playing around with Aircrack the other night, and trying to utilise the patches that would allow packet injection, but it wasn't working for me, so I rebooted.  After that, though, my wireless card seems to have gone completely haywire.  It doesn't show up at all in iwconfig.  Before, I had 4 entries:  lo, eth0, irda0, and eth1, which was the wireless.  Now, only the first three show up.

This is what it comes up as under lspci:

```
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I've tried a number of solutions I've found online, including doing a cold boot, reinstalling the driver (Broadcom STA) and starting up from a cold boot, and am now trying [this]("http://linuxfans.keryxproject.org/?page_id=54") approach.  Nothing has worked, so far.

I'm getting really desperate.  I need my wireless working for university, which starts shortly, and I might even switch back to Windoze if there's no feasible solution.

Thanks, guys, for anything you can help with.

---

### Post by Chris-Chicken on 2010-01-30
I'm still something of a new person in this world, however, this is similar to a problem I had with a different card after trying to get things to work.

I found that I'd managed to tell the utility(?) modprobe to blacklist the driver modules for my card.

Not sure quite how I did that, (probably some late night capy/paste commands!) but it might be worth checking out /etc/modprobe.d/blacklist and using the sudo gedit command to comment out your driver from the list if it's there.

I found that somehow, new blacklist files (Blacklist~, Blacklist~~) were being created. I think this was caused by adding Ndiswrapper to modprobe (sudo modprobe -a ndiswrapper) ..... So, I removed it (sudo modprobe -r ndiswrapper) and deleted the extra blacklists...... all was well.

Not sure if that's of any help at all...... :D

---

### Post by blufindr on 2010-01-30
My drivers haven't been blacklisted, I checked that before.

I'm seriously frustrated.  I did something a few minutes ago, got it working of a sort (recognised, at least, in iwconfig), rebooted, and it's all gone to shite again.

---

### Post by blufindr on 2010-01-30
Also, I can't turn the wireless card on or off, because for some reason, the switch on my case isn't working.

---

### Post by blufindr on 2010-01-30
I really need to keep an eye on what I do to my system!  I did something, I think the openfwwf drivers or something, and everything's working fine now.  :)  My wireless connection has even changed over from eth1 to wlan0, which is what I wanted it to be but couldn't work out how to change it before.

[/thread], IMO.

---

