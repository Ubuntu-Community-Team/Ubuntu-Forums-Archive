---
title: "Weird network problem defies analysis"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by johnzbesko on 2009-12-28
Something got messed up on my Hardy x86 desktop, possibly when I attempted to install a new wireless router and inadvertently had two DHCP servers running at the same time.

Currently, the desktop will not access outside my local home network. All my other PC's work perfectly fine- including virtual machines running on this desktop! I can ssh, mount samba and NFS shares, but cannot web browse or fetch email, etc. from the internet. If I boot a thumb drive version of linux, the internet works fine.

There is no firewall on this desktop, i.e. "iptables -L" shows nothing. All other network options are set as expected for my home network. "nslookup some_site" hangs. "traceroute some_outside_IP" stops after 1 hop. Rebooting and/or using a previous kernel version does not help. I've checked resolv.conf and "johnz:~$ route"

I set up a squid proxy server on my home server and configured the desktop to use that for all connections. This fix works! The desktop can now access this forum.

What in the world could I be missing?

---

### Post by shairozan on 2009-12-29
Just a random question, what is the network addressing scheme? You had mentioned that you had two DHCP servers running at one time, so it would be most prudent to make sure that the box in question is getting the correct subnet info as well as a valid gateway. This would explain why using a proxy would allow you to get to the internet. 

Run the following

```
sudo ifconfig
```

It sounds more than probable that the device has an incorrect default route or does not know how to get to the gateway.

---

### Post by johnzbesko on 2009-12-29
I've run ifconfig so many times it clogs up my .bash_history file ;-)

Another clue: I had also tried installing a new graphics card and had problems with xorg drivers. At several points, I had to "pull the plug" to reboot. Even with ext3 filesystems, I suspect some files may be corrupted. (I noticed my KDE settings had changed, too.)

I'm wondering what packages I should try re-installing. On the other hand, this problem (and the new nvidia card) is a good reason to do a fresh install of Karmic...

---

