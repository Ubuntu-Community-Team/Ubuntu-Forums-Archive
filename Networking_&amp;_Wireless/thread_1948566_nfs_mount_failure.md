---
title: "nfs mount failure"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by bobosoft on 2012-03-28
I am trying to mount an exported disk on my local machine. I have the following line in my fstab

```
netapp6:/xxx/xxxxx/xxxxxxx /x/xxxxxxx nfs rw,addr=xxx.x.xxx.x 0 0

```

however I get the following error

```
mount.nfs: access denied by server while mounting netapp6:/xxx/xxxxx/xxxxxxx

```

and if I do dmesg I see

```
RPC: server netapp6 requires stronger authentication.
```

I am using Ubuntu 11.10, in a VirtualBox environment. What could be the problem ?

Thanks in advance

---

### Post by papibe on 2012-03-28
> **bobosoft said:**
> I am using Ubuntu 11.10, in a VirtualBox environment. What could be the problem ?
That would be my first guess.

Could you post the content of your /etc/exports on the server?

Also, could you post the result of these commands on both the server and the virtual machine?
```
ifconfig
```
This is what I'm asking: VirtualBox's default network setting is to use 'NAT', and that puts your VM on another network!

Regards.

---

### Post by bobosoft on 2012-03-28
Hi papibe, thanks for your quick reply

> 
Could you post the content of your /etc/exports on the server?


unfortunately I cannot as I don't have access to it. However I am quite confident that it is setup correctly, as all the other services of my account have been setup by the IT guys of the company (which are some unknown guys 10000 Km away from me). Also I can access successfully to the disk which is mounted automatically on other machines of the network

> 
Also, could you post the result of these commands on both the server and the virtual machine?
```
ifconfig
```
This is what I'm asking: VirtualBox's default network setting is to use 'NAT', and that puts your VM on another network!


To be more precise: I have windows (yes, I know, I should not, but my company does not allow me to wipe-it-out-in-no-time-as-I-would-have-normally-done) which is connected to the virtual network of the company, and vbox seems to get all the facilities of the network (servers, outloook accounts, and so on) 

Anyways, here it is

```

eth0      Link encap:Ethernet  HWaddr 08:00:27:xx:xx:xx  
          inet addr:10.x.x.xx  Bcast:10.x.x.xxx  Mask:255.255.255.0
          inet6 addr: fe80::xxx:xxxx:fe69:4131/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63853 (63.8 KB)  TX bytes:47421 (47.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2632 (2.6 KB)  TX bytes:2632 (2.6 KB)

```

Cheers,
R

---

### Post by SeijiSensei on 2012-03-28
If you're mounting the share from /etc/fstab, the process will be handled by the root user on your local machine.  It won't be using your account information. 

You really need to coordinate with the server managers.  They need to watch the log on their end while you try and connect to diagnose the problem.  I doubt you'll be able to solve this on your own.

---

### Post by papibe on 2012-03-28
> **bobosoft said:**
> To be more precise: I have windows (yes, I know, I should not...
Don't worry about that.

If I understand correctly Windows is the host, and Linux is the guest. If so, run this on Windows:
```
ipconfig /all
```
and post your results.

Regards.

---

### Post by bobosoft on 2012-03-28
thank you again for your quick reply

> 
If I understand correctly Windows is the host, and Linux is the guest. If so, run this on Windows:
```
ipconfig /all
```
and post your results.


here it is

```

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Myname-E6420
   Primary Dns Suffix  . . . . . . . : mycompany.com
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : mycompany.com
                                       mycompany.com

Ethernet adapter Local Area Connection 4:

   Connection-specific DNS Suffix  . : mycompany.com
   Description . . . . . . . . . . . : Cisco AnyConnect VPN Virtual Miniport Adapter for Windows x64
   Physical Address. . . . . . . . . : 00-xx-xx-xx-7A-00
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::xxx:xxxx:42c2:e585%35(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.x.xxx.50(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 788530586
   DHCPv6 Client DUID. . . . . . . . : 00-01-xx-xx-14-xx-xx-AD-5C-xx-0A-2E-58-2F
   DNS Servers . . . . . . . . . . . : 192.x.130.xx
                                       192.x.200.xx
   Primary WINS Server . . . . . . . : 192.x.xxx.17
   Secondary WINS Server . . . . . . : 192.x.xxx.21
   NetBIOS over Tcpip. . . . . . . . : Enabled

Wireless LAN adapter Wireless Network Connection 2:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : DW1501 Wireless-N WLAN Half-Mini Card
   Physical Address. . . . . . . . . : 7C-xx-xx-xx-7A-C0
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::xxxx:a39e:9de4:5193%25(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.0.17(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Wednesday, March 28, 2012 18:55:31
   Lease Expires . . . . . . . . . . : Thursday, March 29, 2012 18:55:30
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 543728580
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-14-B7-CC-AD-5C-26-0A-2E-58-2F
   DNS Servers . . . . . . . . . . . : 89.xxx.xxx.1
                                       89.xxx.xxx.2
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
   Physical Address. . . . . . . . . : 08-xx-xx-xx-70-0D
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::71a6:1090:a62d:e3a9%44(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.56.1(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 738721831
   DHCPv6 Client DUID. . . . . . . . : 00-xx-00-01-14-xx-xx-xx-xx-26-0A-2E-58-2F
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled


Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . : mycompany.com
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-xx-xx-xx-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:xxxx:8432::c009:8432(Preferred) 
   Default Gateway . . . . . . . . . : 2002:xxxx:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 192.xxx.xxx.17
                                       192.xxx.xxx.21
   NetBIOS over Tcpip. . . . . . . . : Disabled

```

Cheers,
R

---

### Post by papibe on 2012-03-28
There you go. They are indeed on different networks.

Linux on VM:
```
inet addr:10.x.x.xx  Bcast:10.x.x.xxx  Mask:255.255.255.0
```
Windows host:
```
IPv4 Address. . . . . . . . . . . : 192.x.xxx.50(Preferred)
```

Even though SeijiSensei has an important point, the usual security restrictions that an admin uses for NFS are 'network' based. Check this [tutorial]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for example. Note the /etc/exports file.

If you change the way the virtual machine connects to the network you may have a chance for the mount to work.

Here's what I would test:
[LIST]
[*]Shutdown your virtual machine, so that you are back on VirtualBox without any guest running.
[*]Select your Linux machine and press 'Settings'.
[*]In the new window, select Network from the list on the left.
[*]Change the field 'Attached to' from NAT to 'Bridge Adapter'.
[*]Start your virtual machine again.
[*]Test that the guest is in the same network by running 'ifconfig'. You should be on the '192.xx.xx.xx' range now.
[/LIST]
Now try again the mount.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by bobosoft on 2012-03-29
Hi again,

just to confirm, it really looks like it is a virtualbox-related problem and not an ubuntu-related one. I tried the bridged approach with a mixed success: I can get access in read-only mode :-/ Anyways, I think it just boils down to play a bit with the various options and I'll succeed sooner or later. Thanks again

R

---

### Post by lisanels47 on 2012-03-29
I use "Bridged" networking on my virtualbox's.  That should pickup a dhcp address on your network and get them on the same net.

---

### Post by bobosoft on 2012-03-30
Yes, true, but the problem is that I need "the very same address of my windows machine" and not another internal one. So this is the last bit that I have left to fix somehow

Thanks,
Roberto

---

### Post by bobosoft on 2012-03-30
By the way ...

I tried to use **sshfs** and it works like a charm !

This is more than a valid alternative for those with the same problem as mine. 

In fact I think I will stick to this solution rather than trying to fix again nfs (yes I am lazy -- also, it works even if I keep the NAT settings for virtualbox)

---

