---
title: "Can't share internect connection between Lucid PCs"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2010-05-24
Hi,
I'm trying to share my internet connection between Ubuntu computers (10.04). Since my server is also a thin client server (and needs a static address of 192.168.0.254), I couldn't simply allow Network Manager to control my IPv4 Settings. Therefore, I followed the "Ubuntu Internet Gateway Method (iptables)" from here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
and initially got the connection going (using a static ip address of 192.168.0.100 on the client). When I rebooted the client however, the connection had disappeared and my client's ip address was now 192.168.0.20 - meaning, I suppose, that it had lost its static address and come under the control of my server's DHCP.
So I set the client's /etc/network/interfaces manually as 
address 192.168.0.254

netmask 255.255.255.0
gateway 192.168.0.254
...but I still get no internet access.
I can ping the server (192.168.0.254
) but not the router (a PC running ipcop - 192.168.1.1 - which is also the name server).
Network Manager on my client also gave up control of eth0 - listing no wired network connections at all.
Does anyone have any ideas?
Thanks

---

### Post by Iowan on 2010-05-24
You can set a manual (static) IP address via Network Manager. Alternatively, you can probably set your DHCP server to issue a static lease - based on MAC address.

I'm confused why you'd use the machine as it's own gateway - ordinarily, that would be the next upstream machine. Maybe that was a typo - but the router is in a different subnet.

---

### Post by dbclinton on 2010-05-24
Thanks for your reply. I think I'm still missing something important in my understanding of all this.

[INDENT]You can set a manual (static) IP address via Network Manager.[/INDENT]
I did try that using the IPv4 "manual" settings (with IPv6 set to "ignore) and it didn't work - although I'm really not sure that there wasn't something else I'd messed up that was holding things back.
Since Network Manager is now not recognizing my eth0 connection, could I add a new eth0 manually or is there some way to force it back?

[INDENT]Alternatively, you can probably set your DHCP server to issue a static lease - based on MAC address.[/INDENT]
I really don't mind what ip address my client gets (192.168.0.20 is also within the network range), but I understood 192.168.0.20 as a symptom that my settings based on "Ubuntu Internet Gateway Method" were being overridden by the regular DHCP server and that that was killing my Internet share. Would the server's dhcpd.conf not have that same effect?

[INDENT]I'm confused why you'd use the machine as it's own gateway - ordinarily, that would be the next upstream machine. [/INDENT]
The 192.168.0.254 gateway is the address of the server. Are you suggesting that I should use the address of my ipcop firewall (192.168.1.1)?

I appreciate your help!

---

### Post by Iowan on 2010-05-24
> **dbclinton said:**
> Thanks for your reply. I think I'm still missing something important in my understanding of all this.
I'm probably the one missing something ;) I may be confused between the server and the client:
> So I set the client's /etc/network/interfaces manually as
address [COLOR="Red"]192.168.0.254[/COLOR]
netmask 255.255.255.0
gateway [COLOR="Blue"]192.168.0.254[/COLOR]Network Manager gave up control of eth0 because it is defined in */etc/network/interfaces*. You can remove the definition from there - or edit */etc/NetworkManager/nm-system-settings.conf*.

I seem to remember a thread where a machine was originally configured via DHCP, and the lease kept trying to renew itself - even though the machine was supposed to have a static address. I'll need to look for which file needed flushed...

---

### Post by dbclinton on 2010-05-24
Thanks. I'll try this tomorrow...

---

### Post by dbclinton on 2010-05-24
> I'm probably the one missing something  I may be confused between the server and the client:
Quote:
So I set the client's /etc/network/interfaces manually as
address 192.168.0.254
netmask 255.255.255.0
gateway 192.168.0.254


Oops. I just realized...that was a typo on my part. I actually set the clients own IP as 192.168.0.100. Sorry.
In any case, I will give it another try tomorrow.
Thanks

---

### Post by dbclinton on 2010-05-25
> Network Manager gave up control of eth0 because it is defined in /etc/network/interfaces
Thanks. That did the trick. So I've properly set the client's eth0 to

address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.254 

Following the instructions from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing), I also ran 

sudo route add default gw 192.168.0.254

- which I now realize does the same thing as setting the gateway in NetworkManager.
In any case, I still don't have any internet...any idea what I'm doing wrong?
Thanks

---

### Post by dbclinton on 2010-05-25
Update:
UPDATE:
I'm not quite sure how, but the network is now up and running with Internet access - perhaps it had something to do with the fact that I redid the configuration on my server just to make sure.
Thanks!
FURTHER UPDATE:
The problem was that the iptables rules I set on the server (see [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) weren't surviving reboots and had to be saved. For information on how to do that, see the "Saving iptables" section from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

