---
title: "DHCP3 broke SSH?"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by JohnnyGear on 2011-04-05
Hello Ubuntu Forums,

This is my first time posting here, so please go easy on me.

Background: I am setting up an Ubuntu router and have done most things correctly so far I believe.
- setup ssh access on port 222
- Statically configured eth0 (LAN) and eth1 (external)
- created a bridge device, br0 (eth0 and wlan1)

Now I installed a DHCP server (dhcp3-server) and it seems to be working partially at least.

It has given another computer on it's net an ip address which corresponds to the pool I setup.

I can ping the ubuntu router from the PC.

I can ping the PC from the ubuntu router.

Here is the annoying part, after I installed the DHCP server, SSH access to the router seems to have broken.

I try to SSH to it's IP address on port 222 and it tells me connection is refused. I thought it was a DNS issue or something, but my PC gets the DNS server's which include the ubuntu router itself and on the ubuntu router obviously it itself is included in hosts&resolv.conf

Someone please let me know what I am doing wrong, would be greatly appreciated, so I don't have to keep moving my single screen from 1 computer to another :(

Thanks,

Johnny

---

### Post by JohnnyGear on 2011-04-07
Ok, I was having a look through my Syslog to see what I could find out about this issue last night.

It seems as if the SSH daemon is getting shutdown everytime it attempts to start.

I changed the init.d config for it and added a $network for the start conditions - found this advice somewhere...

It is still getting shutdown. I will have more time to investigate additional logs tonight.

---

### Post by JohnnyGear on 2011-04-08
So, I got sick of trying to troubleshoot the issue I was having and considering how young the installation was, I decided to start again with a clean slate.

I reinstalled and started from the  beginning - DHCP, DNS, and NAT is configured and working.

I will surely be back again with some problems when I start configuring my Squid Proxy and probably when I tighten my firewall rules a little more.

Until then, thanks for all the help, or er, a place to post about my frustrations :)

Johnny

---

