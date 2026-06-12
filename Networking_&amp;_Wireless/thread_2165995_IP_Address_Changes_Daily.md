---
title: "IP Address Changes Daily"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by Stormspace on 2013-08-07
I recently upgraded my box with a fresh install of 13.04, set up Webmin, pyTivo, and DHCP server. The install routine didn't give me the option of setting a static IP like earlier versions, so I let it install using my routers DHCP server to assign the initial IP address. I did the webmin install first and then used webmin to assign a static ip to the second NIC in the machine (eth1). Eth0 is an onboard NIC that was damaged in a power surge so I don't use it. 

So, I've been using this particular box for several years and before doing the upgrade I saved the DHCP config file to an external so I could just pop it back in once the DHCP server was running. I used Webmin to install the DHCP service, however due to changes in the DHCP software or Ubuntu I had to make some path changes in the DHCP module before I could get it working. That's all good. The machine will hand out addresses correctly, so no problems there. 

The issue I'm having is that every day around 9:30 PM the server is reverting to the ip address it was initially assigned via the routers dhcp server. I've disabled the router from the start and it's taken me several days to verify that it's changing on it's own, but that is exactly what is happening. I've checked the interfaces file and the static address is assigned correctly and if I do a network restart the static ip reasserts itself, however each night it gets the old address back. 

Last night as a test I added a reservation in the DHCP.conf file for the server with the correct ip hoping that maybe the cause was that this new version of the server was giving itself an ip address from its own DHCP service. For now the address has taken, but tonight at 9:00 something will be the test. Anyone else experiencing this? Is this new behavior in 13.04? What gives? Admittedly I'll know more tomorrow, but I wanted to go ahead and post this now in case someone else has seen this and my fix isn't correct. Any help would be appreciated.

---

### Post by TheFu on 2013-08-07
Disable the DHCP server on the router. Conflicting DHCP servers on the same subnet are bad. Which ever DHCP server answers first wins.

I've never used webmin. I consider it a security liability.  To control server IP addresses, learn about the **/etc/network/interfaces** file and edit it manually.
```
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 192.168.1.200
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1
```

You probably want stanzas for eth1.

---

### Post by Stormspace on 2013-08-07
> **TheFu said:**
> Disable the DHCP server on the router. Conflicting DHCP servers on the same subnet are bad. Which ever DHCP server answers first wins.

I've never used webmin. I consider it a security liability.  To control server IP addresses, learn about the **/etc/network/interfaces** file and edit it manually.
```
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 192.168.1.200
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1
```

You probably want stanzas for eth1.

Thx, but did all that. It should have worked which is the reason I'm confused. It's almost as if I have a rogue DHCP server on my network that only affects the server. Also while the initial change in IP was done via webmin (my server is in a location that's difficult to access, so I either use webmin or putty.) I have reviewed the file in nano and made certain that the changes were correct. For an internal machine I find webmin to be completely secure.

---

### Post by TheFu on 2013-08-07
> **Stormspace said:**
> Thx, but did all that. It should have worked which is the reason I'm confused. It's almost as if I have a rogue DHCP server on my network that only affects the server. Also while the initial change in IP was done via webmin (my server is in a location that's difficult to access, so I either use webmin or putty.) I have reviewed the file in nano and made certain that the changes were correct. For an internal machine I find webmin to be completely secure.

Are you running desktop or server Ubuntu?  Desktop has extra-friendly network tool packages that should probably be removed (IMHO).  On Linux, the network comes up before the DHCP server, so the IP has to be provided by an outside machine ... or a huge-ass DCHP reservation timeout.  After that point, your server is probably quicker than a little home-router, so DHCP addresses to other devices come from it.  Perhaps if you turn off the server, then bring on any other DHCP client, you'll be able to tell which router is doing it by the other settings like gateway or DNS servers or routing table?  Maybe not, but it is worth a try.  If no IP is provided, the client will get an 169.x.x.x address - right?

Webmin security is a matter of opinion, just like using nano is a matter of opinion.

Why would you use Putty? Stuck on MS-Windboze?  I'll prey for your seoul. ;)

---

### Post by Stormspace on 2013-08-08
Thx for the help. Even after the reservation it's still changing nightly. Your idea of shutting down the server and renewing my IP is a good one. I'll give that a try. As for Windows, I use quite a few free video encoders that I'd rather not pay for, or figure out how to configure a linux app to encode for the picky TiVo's on my network. :)

---

### Post by Stormspace on 2013-08-08
OK. For the record. Setting a reservation for the server on the server is not recommended. Do that and the DHCP service won't start at all. :) 

In other news the Linux box is the only dhcp server, so somehow it's reverting on it's own to the other IP address.

---

