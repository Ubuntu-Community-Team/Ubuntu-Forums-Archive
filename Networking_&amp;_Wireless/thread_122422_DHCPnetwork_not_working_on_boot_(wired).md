---
title: "DHCP/network not working on boot (wired)"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by sisooktom on 2006-01-27
My network card doesn't receive a DHCP response on bootup, and I can't figure out why.  I have "auto eth0" in my /etc/network/interfaces file, and it tries to obtain a DHCP lease on startup (it hangs for about 30 seconds) but it never gets one.  The same thing happens if I try ifdown eth0 ifup eth0.  BUT, if I try dhclient eth0, I get an offer immediately and everything's fine.  Also, I do have the hotplug info in /etc/network/interfaces that was put there during the install.  Basically, I'm trying to figure out why ifdown/ifup fails but dhclient succeeds.  My hardware is really basic, an old 3c9x 3com NIC and a Linksys WRT54G router.  Any ideas?

---

### Post by fangorious on 2006-01-27
I'm having a possibly related problem. At boot, DHCP returns a valid IP configuration, and I can even ping my router. But some internet traffic doesn't work (web) until I run 'sudo dhclient' in a terminal. Some traffic (like IM) seems to be unaffected. It just started today. It's really bizarre. There was someone on #kubuntu talking about it the other day, so I think there might be a bad update in the repos. I know the problem isn't my connection, as my work machine (running windows) has no problems whatsoever.

---

### Post by sisooktom on 2006-01-27
Doesn't sound like the same problem to me.  Mine is a fresh install; the network configuration didn't work during install either since it couldn't get an IP.  Is there something I need to do post install to configure it then?

---

### Post by stream303 on 2006-01-28
I wonder if the old cards are having problems with ipv6?  This doesn't sound like a real solution to the problem, but might be worth a try - admittedly this isn't very scientific of me...

edit **/etc/modprobe.d/bad_list**   (you'll need to create bad_list as it isn't there by default)

and add:
alias-net-pf-10 off

reboot or bring your interfaces down and up again for ipv4 only

just a thought...

---

