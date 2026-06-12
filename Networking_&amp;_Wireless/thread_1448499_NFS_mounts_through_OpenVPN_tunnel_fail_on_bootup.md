---
title: "NFS mounts through OpenVPN tunnel fail on bootup"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by dvrvm on 2010-04-06
Hi,

I have two NFS mounts /home and /bla which should be mounted after OpenVPN goes up. OpenVPN must go up conditionally, i.e. only if I am not already in a certain network.
So I wrote two init.d scripts, my_vpn and my_nfs.

my_vpn checks my IP and brings up the VPN if needed, it is linked as S16 in /etc/rc2.d
my_nfs checks if the servers are available and brings up the mounts if available. It is linked as S99 in /etc/rc2.d (it was S17 before, but this doesn't change anything.)

Note that the OpenVPN connection is built up via a Network Manager-managed wireless connection. This wireless connection works fine, and is indeed brought up before gdm, because the corresponding password is not stored in the keyring. Also, the OpenVPN script seems to work great, since the VPN comes up as it should. 

The NFS script gives me problems though. It works fine when launched from the command line once my system is up, but doesn't work as init.d S99 symlink. The ping command (which checks if the server is up) says *network unreachable*, and if I deactivate the ping check, the nfs mount says *DNS resolution failed for 192.168.98.3: Name or service not known*. 

Why should that be? The OpenVPN script clearly works. The tunnel is up afterwards. OpenVPN goes into daemon mode only when the connection is up (right?) and therefore init.d stuff should not proceed before the tunnel is running.

---

### Post by Raimund Eimann on 2010-05-21
I had a similar problem on openSuSE where starting independent boot services in parallel to speed up booting broke the classical init.d/rcx.d/ S... and K... sequence. There, I found extra files in /etc/init.d/ which define the dependencies between the services. I simply disabled parallel boot service startup (somewhere in /etc/sysconfig) which got the boot going in the classical fashion. Ever since, my openvpn tunnel comes up before the NFS mounts happen.

Cheers,
Raimund

---

