---
title: "Virtual ethernet card - VPN"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by pmla on 2009-07-04
Hi,

I usually use a vpn connection from home to my work.
The Gateway at my work is a **Fortinet** (Fortigate) and I'm using Ipsec DHCP/Ike/mutual PSK preshared key/XAuth to domain server.

I just made a fresh install of Ubuntu 9.04 desktop over windows. And I'm really happy with it. In windows I used the fortinet client... but the client is under license and therefore would have to pay for it.... sucks big time and trying to avoid it.

So, I decided to install **Shrew VPN 2.1.4** from the repositories and it's working great. Except that I can ping all Ip's from work but not hostnames!?  So, there's something wrong with the DNS.

One thing I have noticed was that fortinet used a virtual ethernet adapter... that I'm guessing allowed me to have the correct IP/subnet/gateway/dns from my work lan.


Now, in Shrew I have the option to use my physical ethernet card or a virtual one. I have been using my physical because shrew does not install a virtual one. And I guessing that I would actually use shrew with a virtual card (like forticlient) I could probably pind hostnames.


So, my questions are:
1. Is there a way to install a virtual ethernet card in Ubuntu 9.04... maybe with a GUI if it's not asking too much? or maybe available through the network manager GUI after installation?

2. Is there an open source VPN client, maybe better than Shrew?

3. Am I doing something wrong, and should be able to ping hostnames using my physical ethernet card? even doe my home network is in a completely different Ip range and DNS?

---

### Post by pmla on 2009-07-05
**** BUMP 1 of 3 ****

---

### Post by SpawnHappyJake on 2011-10-05
I think you will be happy to read my replies here: [http://ubuntuforums.org/showthread.php?p=11311563#post11311563](http://ubuntuforums.org/showthread.php?p=11311563#post11311563)

It says how to get FortiClient for Linux for Free (legal as far as I know), and talks about hardware emulation, in special regard to network adapter emulation (there isn't a difference, BTW, unless you do "higher-level" emulation of a network adapter that doesn't appear as hardware.).

Cheers,
Jake

---

