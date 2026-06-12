---
title: "Network not re-obtaining dynamic IP after network outage"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by doobiest on 2009-06-15
Hey guys, let me run this issue by you and I'll get back with more details if you have any questions.

I'm not sure what the initial cause is but here's what I observe. 

1) My ubuntu box no longer shows an IP when doing an ifconfig for eth0, it used to have a dynamic IP and it gets lost somehow, maybe the network connection dropped.
2) It does not automatically try to obtain an IP. I'm assuming this based on the fact that the network connection is up but has no IP. However maybe it is attempting to gain an IP and is failing, just not sure where to check to verify that.
3) Manually running dhclient obtains an IP.
4) This happens about every 2 days.

I'm going to write a cron to just check for an IP every 5 minutes and if it doesnt have one then run a dhclient. This will be an OK work around for now but I'd like to find out why it's not automatically trying to get an IP and if it is trying why is it failing.

Thanks.

---

### Post by scrooge_74 on 2009-06-15
The only similar case to yours that I know if when power goes at my house or something funny happens to my router and it will not assign me an IP, I have to reboot router and sometimes the PC after the router

---

### Post by superprash2003 on 2009-06-16
you could try logging in to your router and extending the DHCP lease time..

---

### Post by scrooge_74 on 2009-06-16
I tough of that, but the underlining issue still remains, it should just reassing IPs, not cut you off

Nice blog by the way

---

