---
title: "VPNC Problems"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by Musicalmidget on 2008-12-14
I've been trying for some time now to get VPNC working on my new Ubuntu 8.10 (x64) installation but I'm having some serious problems.

VPNC is setup, I've entered my VPN details, saved the configuration and I seem to be able to connect to the VPN correctly.  However, I don't seem to be able to do anything once I'm connected.  I can navigate to the company intranet through a browser and a couple of the links work, but most other internal addresses fail to load.  It's as if the browser has connected but is taking forever to load the page, as I sometimes get the page title if nothing else.  Additionally, I can't seem to SSH onto any of the servers on the network or open any remote desktop sessions, again with a timeout related error.  The strange thing is that I can ping all the same machines and servers with a 100% response, yet SSH and remote desktop connections never seem to work.

Whatever the problem is, I'm sure it's related to my Ubuntu installation.  I've successfully connected from Vista, Mac OS X and another machine using Ubuntu 8.04 on my home network.  I've even saved the working configuration from the 8.04 machine and imported it onto my normal 8.10 machine and still the problem remains.

So far I've been unable to find what might be causing this issue but if anyone has any suggestions I would be very much appreciate the help.

Thanks.

---

### Post by joebeasley on 2008-12-17
Make sure you are getting the correct name servers in /etc/resolv.conf once you are connected.

---

### Post by Musicalmidget on 2008-12-17
> **joebeasley said:**
> Make sure you are getting the correct name servers in /etc/resolv.conf once you are connected.

Hi,

I've just compared the contents of /etc/resolv.conf to the contents of the same file on the working machine and they appear to be the same.  A new DNS entry is added to the file on connection as I believe it should be.

Any other suggestions?

---

### Post by Musicalmidget on 2009-01-09
Well, it's been over three weeks now and I'm still having this problem.  I must have tried everything I can think of and I'm still no closer to a solution.  This is getting to be quite an issue as I'm trying to use Ubuntu for pretty much everything now, but that simply isn't possible without a way of reliably using VPN.

I would be very grateful for suggestions that anyone may have.

---

### Post by tpurch on 2009-01-12
> **Musicalmidget said:**
> Hi,

I've just compared the contents of /etc/resolv.conf to the contents of the same file on the working machine and they appear to be the same.  A new DNS entry is added to the file on connection as I believe it should be.

Any other suggestions?

can you print out your routing tables before and after you connect to vpnc?

---

### Post by Musicalmidget on 2009-01-12
Hi tpurch,

Before connecting:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

After connecting:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
194.81.0.117    192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
10.2.100.16     0.0.0.0         255.255.255.240 U         0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.40.1.0      0.0.0.0         255.255.255.0   U         0 0          0 tun0
10.2.0.0        0.0.0.0         255.255.0.0     U         0 0          0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

I'm not totally sure what I'm looking for here but hopefully it'll mean something to you.

---

### Post by tate on 2009-01-13
i'm having the same problem.  i even sat with another network engineer at work and went through a lot of troubleshooting.

i can connect fine, ping servers fine, resolve hosts fine.  when i try to ssh to my servers i get the login prompt, enter my password and then it just locks at the Last Login...screen.  every once in a while, it will give me a prompt and then as soon as i list a directory, it locks up on the listing.

this is usually a sign of dropped packets, so we set the MTU on the adapter and even at the router level to match the vpn router.  no luck, same thing.  the cisco official client is acting the exact same way.  we've gone through ever configuration imaginable and still no luck.  i'm wondering if the problem is lying within the current kernel or something.  i'm running 8.10 and vpnc version 0.5.1.  i was thinking about compiling version 0.5.3 from the site, but don't want to go through with all of that if other people are having problems.  i would like to find the root so we can get it fixed for everyone in the community.

anyone else have any ideas?

---

### Post by tpurch on 2009-01-14
Musicalmidget your routing tables look fine!

Are you connecting via a GUI or at terminal prompt?  

if you are running at terminal prompt try:

vpnc --natt-mode cisco-udp 'your_config_file.conf'

if GUI check if you have NAT Transversal Mode Cisco-udp enabled (if not, enable it and give it ago) 

it may also be worth enabling the vpnc debug mode and posting the some of the resulting output to the forum but **BEWARE** what you post because the output may contain hex-encoded username and password information.

---

