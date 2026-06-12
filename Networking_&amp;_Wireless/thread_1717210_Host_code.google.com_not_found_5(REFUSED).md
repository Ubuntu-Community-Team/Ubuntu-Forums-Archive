---
title: "Host code.google.com not found: 5(REFUSED)"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by sschafer on 2011-03-29
Hi All,

I have a number of computers on my router with various OS's but I'm only having this problem on my Ubuntu 10.10 box.  It can't resolve some domain names.  Specifically:  code.google.com and imgs.xkcd.com.  Those are the only two I've noticed.   It's had intermittent problems with imgs.xkcd com over the past few months but the problem with code.google.com just started today.  If I type

host code.google.com

I get:

;; Truncated, retrying in TCP mode.
Host code.google.com not found: 5(REFUSED)

I can resolve both of those domain names on all the other computers in my LAN.  Can anyone tell me what's going on and how I might be able to fix it?

Thanks in advance.

---

### Post by Do_Japan on 2011-03-29
Maybe you have already tried this, but a few basic suggestions:
Check the DNS server on your ubuntu box.  Is it getting the same server as your other PCs?
If the DNS server info is the same, check for proxy settings.
No proxy settings, renew the DNS settings with the following command:

sudo /etc/init.d/networking restart.

If it's still not working I suggest that you reset your network:
Unplug your router, reset your modem, once the modem has a connection reconnect the router.  You may need to restart your PCs or renew DHCP lease:

sudo dhclient -r

Your last two things you can try:
1) Factory reset the router, press and hold the reset button on the back, this should wipe out network settings and restore the router to its original configuration.

OR

2) Bypass the router, plug the ubuntu box directly into modem.  You will probably need to reset the modem by pressing and holding the reset button on the back of it.  If it doesnt work connected directly to the modem then you have something going on with the ubuntu box.  (Don't try pulling that it's my ISP BS, your ISP isn't conspiring against your Ubuntu box and no amount of whining on the phone will fix the issue).  At that point I would ask somebody for a second opinion, try a second NIC, or format and reinstall...

---

### Post by sschafer on 2011-03-30
Thanks for the reply.  Turns out, upon further investigation, to be my router.  I still don't know why the problem is occurring but if I assign the downstream DNS servers to my network settings the problem goes away.  I'll try resetting the router.

---

