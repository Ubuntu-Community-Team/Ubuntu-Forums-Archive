---
title: "Odd networking issue on small home LAN."
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by FrozenFlame22 on 2009-02-18
I'm having a rather odd home networking issue.

My setup: 1 dual booting Ubuntu 8.10/WinXP computer (wired connection) and 1 Vista laptop (wireless connection) connected through a Linksys WRT54GS-V.4 broadband wireless router to a Actiontek GT701 DSL modem. Qwest is my ISP. Both computers have a static IP. I use Open DNS. The desktop is always on and always connected to the internet. Software firewalls on the Windows operating systems. Bare bones firewall in the modem. Firefox 3.0.6 used exclusively on all operating systems.

A few weeks ago we started having problems with accessing certain sites while accessing anything else worked just fine. This would cause several sites to not load and show an error stating "The network link was interrupted while negotiating a connection. Please try again." Examples included weather.com and [www.usaa.com](www.usaa.com) (banking website) and affected all computers. This was fixed by simply rebooting the router and modem, but it became a recurring annoyance.

Now for the last week we have not been able to connect to USAA and so far it seems to be the only website that we cannot access. We have verified that this site does work by using other computers outside our LAN.

So far I have tried:
1. Reboot the router and modem.
2. Check DNS on router and modem.
3. Disable Greasemonkey.
4. Disable all Firefox addons.
5. Delete usaa.com cookie.
6. Attempt to use Internet Explorer. - Same results as Firefox.
7. Turn off all firewalls.
8. Verify that all hardware has a unique static IP.
9. Check settings on modem and router.
10. Update router firmware.
11. Bypass router to connect desktop directly to modem.

Now here's where it gets weird. When I attempted to connect the desktop to the modem I didn't get any connection at all. I couldn't even open the modem properties, much less ping it. I even tried using a different CAT5 cable that I'm certain works just fine. Nada. I get connection through the router, but not without it. I can't update my firmware on the modem (which is out of date) without a direct connection.

I am completely baffled and out of ideas. Does anyone else have a suggestion?

---

### Post by Iowan on 2009-02-18
I just signed up for DSL with Qwest (got an ActionTek M1000 modem). I hesitated for a long time - now I'm wondering what kind of problems I'll have... 

From what I've read, some modems "lock onto" the MAC address of their client.  If you connect directly to the modem, you may need to cycle power to make it "re-learn" the MAC address. (You'll need to repeat the process when you re-connect the router to the modem.)

---

### Post by ajkenney on 2009-02-19
Maybe a stupid question but, did you change the network settings in your computer so they match the ones in your Linksys router?  After that, reboot both devices (your computer and the modem) and try connecting again.

Like I said, maybe it's a stupid question but, you didn't mention it, one way or the other, in your post.

Cheers,

Andy

---

### Post by Matsukaze on 2009-02-19
Try running "traceroute www.usaa.com".

---

