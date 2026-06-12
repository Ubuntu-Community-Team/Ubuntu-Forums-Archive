---
title: "Manual IP resets at reboot (8.10 Intrepid Ibix)"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by bsodmike on 2008-12-20
Hi,

I have just installed 8.10 today and tried to setup a manual IP via the Nautilus Network Manager.  To do this, I modified the 'Auto eth0' profile and set the ip as 10.0.0.20, /24, 10.0.0.138 (Speedtouch), and two DNS addresses.

If I press OK, and do an 'ifconfig', the IP appears as needed.  On a reboot, however, the system creates ANOTHER 'Auto eth0' profile and that defaults the IP to 'DHCP' (which my router serves as 10.0.0.1

How can I force the system to stay on a fixed IP?

Thanks!
Mike

---

### Post by bsodmike on 2008-12-21
I managed to fix this by installing 'wicd' using apt-get.  The IP is now permanently fixed, and 'wicd' feels far more robust.

---

### Post by stringkarma on 2009-01-07
@bsodmike I'm glad that wicd does the trick for you.

@anyoneelse I need to use network manager because it can do the 802.1x for my wireless at work. I am having the same problem that upon reboot I have a new eth0 created for me with DHCP settings. Every reboot I have to go into edit connections and delete the new eth0 at which point the old settings eth0 kicks in.

Any suggestions?

---

### Post by superprash2003 on 2009-01-07
have you tried editing the /etc/network/interfaces file

---

### Post by Iowan on 2009-01-07
Check [this]("http://ubuntuforums.org/showthread.php?t=974382") workaround - skip over the ones about removing NM (since you say you need it).  Either the workaround or another thread mentions deleting the extra auto eth0 profile.

---

