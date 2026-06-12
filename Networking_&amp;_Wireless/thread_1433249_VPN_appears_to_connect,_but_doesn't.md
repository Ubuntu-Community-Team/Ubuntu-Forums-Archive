---
title: "VPN appears to connect, but doesn't"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by tnunamak on 2010-03-18
I'm using Kvpnc in KDE am importing a Cisco pcf file to connect to a VPN network. The application shows a green check mark and says connection successful, but none of the servers or IP addresses that I try to connect to on the network resolve.

Any help? The closest thing to a hint that I have is the following, although after these messages are logged both Kvpnc and vpnc processes are still running.

/var/log/syslog:
```

Mar 18 18:49:24 tnunamak-laptop kernel: [ 1763.050630] tun1: Disabled Privacy Extensions
Mar 18 18:49:26 tnunamak-laptop vpnc[4635]: select: Interrupted system call
Mar 18 18:49:26 tnunamak-laptop vpnc[4635]: terminated by signal: 15
Mar 18 18:49:54 tnunamak-laptop kernel: [ 1792.453577] tun0: Disabled Privacy Extensions
```

---

### Post by ybbon66 on 2010-04-22
Did you resolve this? I get the same problem. I can use Cisco VPN Anywhere but that has an inbuilt timeout function that just hangs up without warning. It's not a big issue but I'd prefer to use KPvnc or vpnc - I got scripts etc from a colleague but although connected, I can't then see any internal sites - which sounds the same so I was curious if you resolved this?

Thanks,

---

### Post by jje on 2010-04-22
I have ubuntu 9.10 and a similar problem.
my vpn connection type is 'Compatible with Cisco VPN (vpnc)'.
I can connect to vpn but it doesn't work.

I tried to connect via KVpnc but I coudn't. The error was:
"Timeout while connecting to vpn-ext.cec.uchile.cl (vpn facultad) after 0s. Please check if the VPN server is reachable and the settings (UDP/TCP, local port, UDP encapsulation port) are correct. Maybe the timeout must be increased too"

I don't know why this is happening because it did not happen few minutes ago. When I connect via vpnc I can conect but,like I said, it doesn't work.

Thanks.


P.S.: Sorry for my bad english.

---

### Post by ptipper on 2010-05-10
I'm having a similar problem connecting from the vpnc Cisco VPN client to our company VPN server, where the VPN connection seems to be established OK (i.e. the password authenticates, the VPN link is shown as up), but I can't access any addresses within the private network. I've been using the latest versions of Ubuntu (9.10 up until late last week, and 10.04 now), and I'm using a VPN profile that worked perfectly up until about 2 weeks ago. If I use exactly the same profile, user id and password with the Cisco VPN client on my Windows XP laptop, the connection works perfectly, and I can access servers within the private network without any problems. About 2 weeks ago, when I was running Ubuntu 9.10, the Update Manager included a kernel update, which I duly installed, and I'm pretty sure that up to that point, the VPN connection using vpnc worked perfectly, and that the problems started at or soon after the kernel update.

Here are the outputs of the ifconfig and netstat -nr commands when I'm connected to the VPN:

```
kccppt@ubuntu:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:bd:a7:f8  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:febd:a7f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4131972 (4.1 MB)  TX bytes:733232 (733.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:512729 (512.7 KB)  TX bytes:512729 (512.7 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.31.188.143  P-t-P:172.31.188.143  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kccppt@ubuntu:/etc/init.d$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
195.81.253.244  192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```As things stand right now, I can't ping or otherwise access any address within our private network, and so my VPN connection (and therefore my entire Ubuntu system) is rendered useless. Can anyone suggest what the cause of my problem might be, and how I might go about diagnosing and eventually fixing it?

---

### Post by dca on 2010-05-10
@* ptipper*

This is probably what you're not going to want to here, I was using that Juniper 'Network Connect' VPN dealie (there's a good how-to somewhere on forums from 'mad-scientist').  Worked fine in 9.10 but upgraded and I lost something in the mix, VPN stopped working.  Performed clean install of 10.04, re-did the script & install instructions and back up and running.  It looked like it was a DNS resolving issue but was just happy to find clean install resolved issue.

---

### Post by ptipper on 2010-05-11
I did a clean install of 10.04, but it made absolutely no difference at all - I can connect to the VPN, but I still can't see any of the servers in our private network. So it appears that vpnc is currenly broken, at least with my profile. Can anyone confirm whether they are still able to use vpnc successfully to connect to a Cisco VPN server when running either 9.10 or 10.04? I guess a next step would be to compare my profile with a profile that's known to work to try to hone in the part of vpnc that's not working.

---

### Post by aias on 2010-05-19
The problem is that vpnc needs resolvconf (sudo aptitude install resolvconf).  once you do that, the problem should go away.  However, this is a dependency issue (past versions always had to install it w/ vpnc) and hopefully, they'll fix it for the next version

---

### Post by ptipper on 2010-05-20
> **aias said:**
> The problem is that vpnc needs resolvconf (sudo aptitude install resolvconf).  once you do that, the problem should go away.  However, this is a dependency issue (past versions always had to install it w/ vpnc) and hopefully, they'll fix it for the next version

I went about installing resolvconf as you suggested (which actually appeared to remove and reinstall resovconf), but I'm afraid it made no difference at all - I still can't connect to any nodes within the private network, using either IP addresses or server names. :( Thanks anyway for posting.

---

### Post by jdougmoore on 2010-06-23
> **ptipper said:**
> I went about installing resolvconf as you suggested (which actually appeared to remove and reinstall resovconf), but I'm afraid it made no difference at all - I still can't connect to any nodes within the private network, using either IP addresses or server names. :( Thanks anyway for posting.

Same here, can't contact anything.  Ping to internal IP's from terminal give me "sendmsg: operation not permitted".

I can ping my default inside VPN ip, but no DNS or routing info if being pulled by the built-in 10.04LTS client and Vpnc.  I did the resolvconf install also, zero on my side.  :(

---

### Post by zzantozz on 2010-07-06
> **jdougmoore said:**
> Same here, can't contact anything.  Ping to internal IP's from terminal give me "sendmsg: operation not permitted".

I can ping my default inside VPN ip, but no DNS or routing info if being pulled by the built-in 10.04LTS client and Vpnc.  I did the resolvconf install also, zero on my side.  :(

+1

I have the same problem on two separate machines. One is a freshly installed Ubuntu 10.04, and one is an upgrade. On both, I installed network-manager-vpnc, set up the VPN, and connected. After connecting, I can't ping anything on the VPN network. I don't get the "operation not permitted" error. It just drops 100% of the packets. I also tried installing resolvconf with no change to the results.

Anybody else have suggestions?

---

### Post by bjoarn on 2011-03-11
I can see that this is an old thread, but since it has not been resolved I will post my problem here as well. I believe this is the same issue.

First some details:
PC Dell Latitude 830 w. Intel Centrino Processor
Ubuntu 10.10
VPN Client vpnc version 0.5.3
Connecting via wireless or wired

My problem is as follows:

I am trying to connect to my work VPN server, the VPN appears to connect but I can not reach any of the internal network services the VPN should give me access to. I can reach other services, e.g. web and email, but they are responding much slower than when not connected to the "faulty" VPN.

My colleague can connect using cisco VPN on a Windows 7 machine with no problems. We've tried the exact same profile on both machines (.pcf import) but nothing works on my Ubuntu Laptop.

I've tried the suggestions on this thread with no success. 

I don't suppose anyone has found a solution to this problem in the past 8 months?
Does anyone know where to find logs for the VPN client? 
Is /var/log/syslog the best choice here?

Thanks

---

### Post by zzantozz on 2011-03-11
> **bjoarn said:**
> I can see that this is an old thread, but since it has not been resolved I will post my problem here as well. I believe this is the same issue.

[....]


Have you tried connecting with vpnc at the command line? My Network Manager VPN profiles still don't work (since my July 2010 post in this thread), but I can connect from the command line just fine with "sudo vpnc <target>". I'm still waiting and hoping that NetworkManager will start working with some update. Maybe in 11.04...

---

### Post by bjoarn on 2011-03-14
Thanks zzantozz, the command line works :D I sure hope that they will fix this issue in a near-future release though.

I did notice that the Network Manager VPN seems to work from some sites (e.g. from my wlan at home) but not from others (the wlan at work). I am not sure what the difference is but the command line works in both locations so this is no longer a show stopper for me.

I will paste in the vpnc parameters that worked for me, in case it helps someone else until this issue gets fixed. 

```
sudo vpnc --gateway  <gateway ip address> --id <group name> --username <user name> --domain <domain name>
```

The command line prompts for a secret, where I typed in the Group Password, and then for the password for my user.

Thanks again.

---

### Post by zzantozz on 2011-03-14
Note that you can also create a vpnc config file so that you don't have to keep all that on the command line. See "man vpnc" for details, but briefly, create a file named <whatever>.conf in /etc/vpnc. The vpnc man page has the corresponding conf file setting for each command line arg. For instance, I have a file /etc/vpnc/sat1.conf, which looks like:
```
$ cat /etc/vpnc/sat1.conf 
IPSec gateway <the vpn gateway>
IPSec ID <group id>
IPSec secret <group password>
Xauth username <user id>
IKE Authmode psk
# Xauth password <user password>
```

With this file, I can then just run "sudo vpnc sat1", and it uses those settings. My user password is based on a rotating RSA token, so I've commented that out, and it asks for my password each time.

As an alternative to manually writing the file, there's a Perl script out there called "pcf2vpnc" that will convert a Cisco pcf config file to a vpnc one. There's also some C code called "cisco-decrypt.c" that will decrypt encrypted passwords from said pcf files if you need those. Just google around a bit to find them as well as instructions for using them.

---

### Post by bjoarn on 2011-03-14
Brilliant, thanks again zzantozz :D

---

