---
title: "Trouble with Static IP after Standby or reboot"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by racerraul on 2009-04-28
Upon attempting to set up my static IP by editing the /etc/network/interfaces file I noticed that my eth0 interface was not setup to use DHCP there.

All I had was
```
auto lo
iface lo inet loopback
```

I need to know where is my eth0 set to use DHCP by default, as I believe this is causing me some problems setting up a static IP.

The problem I am having is that after setting up the static IP as such...
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```

I can get it to work by sudo /etc/init.d/networking restart

sometimes... it's very frustrating.  And when it does work, I loose my connection after a reboot or resuming from standby.

When this happens, ifconfig does not show my eth0 adapter, only lo

From my router, I thought I needed to assign a port or IP to a the mac address, but it isn't that robust.  It waits for that info from the hosts.
That said, after changing my IP to static, the router still sees my computer as a DHCP querying host.  Which leads me to believe I need to turn that off on my computer since it is obviously not configured to DHCP from the /etc/network/interfaces file

Hope someone can help.

---

### Post by racerraul on 2009-04-28
Ok thinking the problem was with Network Manager... I disabled it.
sudo update-rc.d -f NetworkManager remove

Will report later to see how the system reacts after reboots and coming up from suspend.

---

### Post by racerraul on 2009-04-29
After setting up /etc/resolv.conf with my router IP for a nameserver everything seems to be OK.

Tested reboot & return from standby and the network is working.

However... I can't see my computer connection on the router.
And unfortunately, its a cheak 2wire DSL router from ATT and I can't hard code the mac address on it to the static IP, bleh...

But for some reason, when the computer was setup with DHCP, it did show up on the routed with the leased IP.

Any ideas?

---

### Post by Cerberus2k7 on 2009-04-29
> **racerraul said:**
> After setting up /etc/resolv.conf with my router IP for a nameserver everything seems to be OK.

Tested reboot & return from standby and the network is working.

However... I can't see my computer connection on the router.
And unfortunately, its a cheak 2wire DSL router from ATT and I can't hard code the mac address on it to the static IP, bleh...

But for some reason, when the computer was setup with DHCP, it did show up on the routed with the leased IP.

Any ideas?

What model 2wire?  The 2700/01s can be hard coded.  The one thing that truely cripples them are IPSEC50/51.

---

### Post by racerraul on 2009-04-29
I have a 2701HG-B 

Today after bringing up the system from standby I noticed the network wasn't working again.

ifconfig did not show my eth0 as up, I had to restart Networking.

Assuming that Network Manager was still trying to take my network adapter hostage I purged it.

sudo aptitude purge network-manager

Hopefully this does the trick

---

### Post by racerraul on 2009-04-29
Bleh, removing Network Manager removes opengeu-desktop and that takes along other packages for the ride with it that I need to have control over fonts and icons... sucks.

Had to install it again...

This seems far more complicated than it should be.  I may just set this back to DHCP, unless a networking guru can show me how to use Network Manager to setup a static IP.

---

### Post by racerraul on 2009-04-30
Well I can say that removing Network Manager did fix my problems, but I wasn't happy about having to re-install it due to other dependencies.

However, re-installing it didn't re enable it, as the /etc/NetworkManager/nm-system-settings.conf file still reads, 
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
**managed=false**

```

After a few reboots and testing standby, the network comes up automatically as it should.
I sure wish I knew what changed when removing and reinstalling NM.

---

### Post by racerraul on 2009-05-22
Well guess it didn't fix it.

Resuming after suspend breaks the network, requiring a restart or networking.
sudo /etc/init.d/networking restart

 RTNETLINK answers: No such process
 SIOCDELRT: No such process
                                                                       
 [ OK ]
 racerraul@raul-6000:~$  * Stopping NTP server ntpd
  ...done.
 * Starting NTP server ntpd
  ...done.
After that I have access to the network.

Anyone have any idea why is Networking not set to restart on resuming from suspend?

---

