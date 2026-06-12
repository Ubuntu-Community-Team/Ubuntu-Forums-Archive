---
title: "static ip in 8.10"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by jadoti on 2009-01-26
Last I read (and attempted) there was a bug with network-manager in 8.10 that prevented the user from setting a static ip address.

Has this been resolved yet in 8.10?  Anyone know if it is going to be?

Is anyone running 9.04 that can confirm whether or not this issue is fixed yet?

Thanks,
Mike

---

### Post by puppywhacker on 2009-01-26
As far as I know static ip-addresses work in Network Manager at least in 8.10. But if it doesn't you can always specify them in /etc/network/interfaces and bypass the networkmanager.

---

### Post by normanp on 2009-01-26
It is fixable by either specifying not to configure the network during installation, or going to /etc/network/interfaces and commenting out or deleting all lines under the primary network interface. Then restart and Network Manager functions.

This is all OK. After setup the icon top right reports all OK. ifconfig reports the IP address etc OK. I can ping my IP address fine.

However I cannot successfully ping another machine set up identically with 8.10 connected to the same switch. Is there some firewall or do the interfaces refuse ping?

---

### Post by paulthing on 2009-01-26
It allows you to set an IP but you need to reset that IP after a reboot.

---

### Post by Iowan on 2009-01-26
**superprash2003** has [this]("http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html") How-To on setting up static address via NM.

---

### Post by normanp on 2009-01-26
This doesn't use NM.
Looking at other posts I think 8.10 may be broken in some way. It can't get any simpler than connecting 2 machines with a switch with static IP addresses surely? The hardware on each machine is different, but this problem is identical on each machine - it must be Ubuntu at fault.
If NM doesn't write to /etc/network/interfaces then where does it put its settings?
I'm really trying to avoid using the CLI as I would like to recommend 8.10 to users used to XP, so would like to use only GUI setup methods.
Reverting to an earlier version is really a mad option that I don't want to try...

---

### Post by jadoti on 2009-01-26
> **normanp said:**
> This doesn't use NM.
Looking at other posts I think 8.10 may be broken in some way. It can't get any simpler than connecting 2 machines with a switch with static IP addresses surely? The hardware on each machine is different, but this problem is identical on each machine - it must be Ubuntu at fault.
If NM doesn't write to /etc/network/interfaces then where does it put its settings?
I'm really trying to avoid using the CLI as I would like to recommend 8.10 to users used to XP, so would like to use only GUI setup methods.
Reverting to an earlier version is really a mad option that I don't want to try...

I think ping is blocked by default on ubuntu.  You can either unblock it, or try some other method (i.e., SSH from one box to the other, just make sure you have the openssh-server package installed).  Reason I say this is I can't ping any other boxes on my network, but can ssh to them just fine.

Mike

---

### Post by jadoti on 2009-01-26
> **Iowan said:**
> **superprash2003** has [this]("http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html") How-To on setting up static address via NM.

I followed instructions similar to these, but again, hosed up my networking.  NM *is* broken as far as static IP's are concerned (will overwrite the static settings on reboot) I was just wondering if it got fixed.

---

### Post by lensman3 on 2009-01-26
I agree it is broken.  I run Fedora Core 10 and I have had remove NM at all run levels.  

The behavior I noticed was that if the eth0 was not being used NM stopped the interface.  So the next time I had to go to the internet it had to started up again.

Sorry I don't have a fix except remove it and hand edit the config files.

---

### Post by dmizer on 2009-01-26
Install the old networking tool (under system > admin > network) with this command:
```
sudo aptitude install gnome-network-admin
```

Then, disable networkmanager:
```
sudo update-rc.d -f NetworkManager remove
```

Bug reports (with lots more information) here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214) and here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284298](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284298)

---

### Post by madverb on 2009-01-27
I've found I can use NetworkManager with no problems using a static IP. The problem is that I have to reset it up after a cold boot. If I restart the computer it stays as static. But a cold boot causes it to reset to DHCP. Pretty annoying.

Edit: Never mind... found another thread with the fix. You have to untick that stupid 'System Setting' box. Why is it 'System setting'? That is some poor GUI design right there. It should say 'Revert to DHCP on Reboot'

---

### Post by normanp on 2009-01-27
I think I have fixed it:
(I have also posted this in another similar thread)

In Network Connections, Add, type the following:
Wired Connection 1, IPv4 Settings: 192.168.0.22, 24
Toggle a few times then leave both 'Connect Automatically' and 'System Setting' as ON, then OK.
Delete connection 'auto eth0'
OK & close.
If necessary click icon top R on screen and enable network.
Reboot.
Network Manager now has ONLY Wired Connection 1 in it.
sudo ifconfig gives correct info.
ping own IP is OK, ping other Ubuntu 8.10 IP is OK.
Set up shared folder in Places, Home with Guest access, can browse to them from each computer using Places, Network (each computer has own icon here, no need to go into 'Windows Network').
(can't yet access shares without Guest access - will pursue in another thread)
Connection remains on further reboots.
Connection also OK when logged in as a non-admin user.
auto eth0 does not re-appear.

Just for completeness (posted further up):
You must do this or Network Manager will not function:
During install do not opt to configure the network.
If it was done during install then edit the file /etc/network/interfaces and delete all the lines under Primary Network Interface, Save & reboot.
Now use Network Manager as above.

---

