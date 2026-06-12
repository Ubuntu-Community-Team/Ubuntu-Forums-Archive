---
title: "NetworkManager and static IP"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by eugenia on 2009-04-25
For some years now I have maintained my wired home network using a desktop connected to the internet (server) and desktop and laptop clients with static IP configurations.

Earlier versions of Ubuntu allowed me to go into System>Administration>Network and easily setup the static IP addresses, gateway and DNS on each and they worked flawlessly.

8.10 and now 9.04 are different.

I downloaded 9.04 yesterday and am trying it 'live' (on a different computer to this one as it won't connect to the internet - I can ping this computer from it though!!) before installing it.

Ubuntu Documentation > Ubuntu 9.04 > Internet and Networks > Connecting > Wired (LAN) states:-

"Static Connections

If you don't use DHCP then you can configure a static connection.

   1.Right click the NetworkManager icon in the system notification area.
   2.Click Edit Connections.
   3.Click the Wired tab.
   4.Select the connection and click Edit.
   5.Click the IPv4 tab.
   6.Choose Manual from the Method drop down.
   7.Enter your details and click OK.
   8.Click Close."

The above steps would have to be incorrect as step 7 will not retain the settings input for some unexplained reason.

Are the developers aware? Is this a problem with Gnome?

Does anyone know of any up to date documentation from Ubuntu that has the correct method?

---

### Post by ccrs8 on 2009-04-27
Shoot - I was hoping there was an answer for this already.  I am experiencing the same thing.  I upgraded from 8.04 to 8.10 and my static IP address that I configured in 8.04 made the migration to 8.10, so I did not realize that this was a problem in 8.10.  However, today I did a clean install of 9.04 and was dismayed to find this exact issue.  The bit of data that specifically is not being retained when setting a static IP is the gateway.  The address, submet, and dns info does stay after saving and closing the network manager.  However, with a gateway that always reverts to 0.0.0.0, you can imagine the difficulties in getting to the internet.

---

### Post by Doncr on 2009-04-28
I have not had any success getting Network "Manager" to configure a static ip for a wired connection, and my searches of the Internet suggest I'm not alone. 

There is a long thread in the Fedora newsgroup that goes around and around in circles - basically it goes 'Set up your DHCP server to give out a static IP address". "Our DHCP Server is on our router and cannot do this." Go back to the beginning. 

I've disabled network manager and set up networking manually. 

My /etc/network/interfaces looks like

```
# added by don@robertson.net.nz 28-04-09

auto lo eth0
iface lo inet loopback

iface eth0 inet static
 address 192.168.1.2
 netmask 255.255.255.0
 gateway 192.168.1.1
```

and my /etc/resolv.conf looks like 

```
# added by don@robertson.net.nz
nameserver 10.1.1.1
nameserver 202.27.158.40
nameserver 202.27.156.72

```

Network "Manager" will overwrite the resolv.conf file.

I guess the number of people who want static ip's on a desktop machine is pretty small these days, but still ...

---

### Post by cb951303 on 2009-04-28
I can't believe it's not fixed yet. A lot of people (including me) experienced the same thing after 8.10 release. Back then you could have abuse the GUI to save the settings properly but as far as I see they removed the "System Setting" check box this time so I believe we have to modify conf files manually.

---

### Post by ccrs8 on 2009-04-28
I ended up getting it working by following a set of instructions that I found here:
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)
and several other places on the internet.

Generally speaking, the instructions give you two options.  Option number 1 is to manually edit the config files.  Option 2 is to manipulate/trick the network manager by adding another connection instead of editing the existing connection, and then disabling the original connection.  I used method 2, and while it did not go 100% smoothly (I experienced an automagically created third connection as described in some of the comments on the linked article, but after disabling that third connection and reverting back to the connection I created, things seemed to have settled down), I now have a static IP address that lasts through reboots and shutdowns and keeps the gateway info.

It definitely seems silly that this bug has lasted so long, but I have not created a bug report so I guess I can't complain.

---

### Post by mnrbig on 2009-04-28
Install wicd.

---

### Post by Yashiro on 2009-04-28
If you use a wired connection and don't move your PC around then just set it up manually after un-installing Network Manager.

---

### Post by ravinsp on 2009-05-14
Install **wicd** through synaptic. Works like a charm. Network Manager is automatically removed from the tray.

You may need to go to System->Preferences->Startup Applications and disable the Network Manager.

Access **wicd** from Applications->Internet. Settings gets applied as soon as you close the IP address dialogbox. (use **ifconfig** command to check)

---

### Post by adhika_rexuss on 2009-05-14
> **ravinsp said:**
> Install **wicd** through synaptic. Works like a charm. Network Manager is automatically removed from the tray.

You may need to go to System->Preferences->Startup Applications and disable the Network Manager.

Access **wicd** from Applications->Internet. Settings gets applied as soon as you close the IP address dialogbox. (use **ifconfig** command to check)

I don't get it, WICD is better than NetworkManager but why NetworkManager became the default instead of WICD

---

### Post by cb951303 on 2009-05-14
> **adhika_rexuss said:**
> I don't get it, WICD is better than NetworkManager but why NetworkManager became the default instead of WICD

AFAIK networkmanager is more than just a GUI. It's a daemon. Which I think is the way to go.

---

### Post by imdano on 2009-05-14
wicd = Wired/Wireless Interface Connection **Daemon**.  

Both wicd and NM use a daemon/client model.  NetworkManager is the default because it's been around a lot longer (it was already mature and well-integrated into many distros before wicd development even started), is developed by Red Hat, and has support for things like VPN and mobile broadband that wicd is lacking.

---

### Post by IronArjen on 2009-05-14
I do not get two things. How do you install wicd when you do not have internet and where do I find it Synaptic does not show it?

---

### Post by Iowan on 2009-05-14
Maybe I'm for an unpleasant surprise next time I try it, but when my "auto eth0" quit getting a DHCP address, first I built a static address assignment in /etc/network/interfaces and manually edited /etc/resolv.conf - it worked. Later, I commented out all these lines and set up a manual address under Network Manager - it also works. In fact, when "auto eth0" fails, it then tries "manual" and succeeds. Though I'm still hoping to get DHCP working, the static address works for now.

---

