---
title: "No network connection; Jaunty 32 bit Server 9.04"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by InvisibleMan on 2009-06-02
I installed 32 bit 9.04 Server successfully on an old desktop. This machine is on a company LAN where I have access to various network admin tools. I say "successfully installed" because after the initial load it picked up updates over the net as part of the installation process. 

However, now it cannot get a connection, sort of.

When configured as DHCP, the network automatically assigned nameservers to /etc/resolv.conf, but no IP was picked up. When configured as static, the correct IP, gateway, broadcast and mask show from ifconfig, and other network server logs show that some activity is taking place on the network, but the new server cannot access the outside world. A handshake is taking place, but unsuccessfully on the server side.

Other info: 
ufw status: inactive
iptables: everything allowed

I've checked the archives, but I don't see anything that quite fits.

Ideas?

---

### Post by Iowan on 2009-06-02
What's in /etc/dhcp3/dhclient.conf?  My system (a laptop, not a server) had problems with the new rfc3442 stuff - details [here]("http://ubuntuforums.org/showthread.php?t=1156441").
As a sidenote - if your server needs a static address, but loses too much of the DHCP versatility, consider setting up a static lease (based on MAC address) in the DHCP server.

---

### Post by InvisibleMan on 2009-06-03
Everything in /etc/dhcp3/dhclient.conf is remarked out except:

# edit: remove rfc3442 and corresponding reference below
# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-ntu,
        ntp-servers;

# edit: previous line used to say
# rfc3442-classless-static-routes, ntp-servers;


My original DHCP configuration did as you suggested, assign a static lease based on the MAC.

---

### Post by Iowan on 2009-06-03
Do you have access to the DHCP server to set up static lease? If not, have you tried manually adding DNS entries in /etc/resolv.conf? (DHCP tends to overwrite)

---

### Post by InvisibleMan on 2009-06-03
Yes to both. 

I originally manually set a static IP in the DHCP server based on the MAC address, and I've manually added a search, domain and nameserver line in /etc/resolv.conf with a DHCP configuration and static configuration. I've tried various combinations of entries in /etc/resolv.conf, with and without search and domain, and I've varied the nameserver.

---

### Post by Iowan on 2009-06-03
The static lease didn't work? It's also possible to use the "prepend" option in */etc/dhcp3/dhclient.conf* to set preferred DNS server(s).

---

### Post by InvisibleMan on 2009-06-04
Prepend didn't work either.

And now my default Runlevel is 2, not much use for networking. I checked /etc/event.d/rc-default and it still says Runlevel 5, but rebooting starts in Runlevel 2.

---

### Post by InvisibleMan on 2009-06-09
I have wiped and reinstalled Jaunty server. Some additional research shows that runlevel 2 may be appropriate for this distro.

That said, here's the latest:

1. /etc/resolv.conf shows a good search option and 3 valid nameservers.
2. The static lease assigned matches during installation and corresponds with the correct hostname.
3. The correct IP is being assigned according to network monitoring devices.
4. ufw status: inactive
5. iptables: everything allowed
6. Default runlevel: 2
7. ifconfig shows no IP
8. lsmod shows e100 as loaded (Intel Pro/100 VE is the hardware)

Ideas, anyone?

---

### Post by Iowan on 2009-06-09
**sudo dhclient** ends with something like "No Working leases in persistent database - sleeping"?

---

### Post by InvisibleMan on 2009-06-09
I'll check.

If YES, then what are you saying that means?

If NO, then what are you saying that means?

---

### Post by Iowan on 2009-06-09
Isn't it obvious? ([SIZE="1"]Sorry, frail attempt at humor.[/SIZE])
If yes, then the DHCP server isn't issuing a lease (or Ubuntu isn't receiving/acknowledging it). 
If no, then the output might be interesting.
I'm kinda curious how (3) the right IP can be assigned, but (7) ifconfig shows no IP address???

---

### Post by InvisibleMan on 2009-06-09
The DHCP server is issuing a lease with the correct static lease IP based on the MAC address. My server is not completing the handshake and accepting the IP.

Of course, the whole point of this thread is how the IP address can be assigned without ifconfig showing it.

---

### Post by pdaalder on 2009-06-19
Hi sorry to ask, did you get it working?

I'm not using server, but just desktop, but having also lots of fun with the wired connection. I've been reading the whole day on internet, I've tried many tips (Thanx to all), but no luck.

---

### Post by InvisibleMan on 2009-06-20
No luck yet, but I'll be trying something new on Monday or Tuesday. I'll post the results.

I tried installing this on different hardware with complete success. It's got to be something with the Intel on-board network card, a Pro/100 VE.

---

### Post by InvisibleMan on 2009-07-14
Complete and utter failure.


No support exists for Intel Pro/100 VE in Ubuntu 9.04 Server.

---

