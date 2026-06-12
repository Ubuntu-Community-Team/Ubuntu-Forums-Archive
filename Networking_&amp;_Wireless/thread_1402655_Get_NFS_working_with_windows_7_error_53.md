---
title: "Get NFS working with windows 7 error 53"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by zonemikel on 2010-02-09
Ok i have a working nfs server that works for all my (wired) ubuntu machines. I have windows 7 on a netbook and it just wont connect for some damnd reason. My nfs server is a wired connection to a wireless router. 

On the linux machine this is the situation (its ip is 192.168.3.133)
```

zonemikel@GalacticAC:~$ sudo exportfs
[sudo] password for zonemikel:
/mnt            uspc
/mnt/sdb4       uspc
/mnt/sdb4       netbook
/mnt/sdc1       192.168.1.11
/mnt/sdb1       192.168.1.11
/mnt/sdb4       10.0.2.2
/mnt/sdb4       10.0.2.3
zonemikel@GalacticAC:~$ sudo cat /etc/hosts
127.0.0.1       localhost
127.0.0.1       GalacticAC
192.168.3.105   uspc
192.168.3.103   netbook
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
zonemikel@GalacticAC:~$


```

Then on the windows machine (192.168.3.103) i get this

```


C:\Users\NetBook>showmount -e server
Exports list on server:
/mnt                               uspc
/mnt/sdb4                          uspc, netbook, 10.0.2.2, 10.0.2.3
/mnt/sdc1                          192.168.1.11
/mnt/sdb1                          192.168.1.11

C:\Users\NetBook>mount server:/mnt/sdb4 z:
Network Error - 53

Type 'NET HELPMSG 53' for more information.


C:\Users\NetBook>

```

I dont have samba on the server so idk how i could possibly join a workgroup. Pls help!

---

### Post by johnson.d on 2010-02-10
This may occur when the iptables blocks nfs traffic. You can try mounting nfs shares after disabling the firewall by using the following command for testing purpose.

$ iptables -F

If you find this working, you can setup iptables to allow nfs traffic and check.

---

### Post by zonemikel on 2010-02-11
The iptables on the "server" machine arent doing anything. Basically the server is wired to a router (dd-wrt) and the "client" (netbook) is connected to the router dd-wrt via wireless.

When i try to mount from the client while running tcpdump on the server this goes through, not sure what to make of it though. GalacticAC is the server,dd-wrt is my router.

I'm running "mount server:/mnt/sdb4 z:" and it sends these packets to the server and returns the error 53
```

zonemikel@GalacticAC:~$ sudo tcpdump -i eth7 port 2049 -v
tcpdump: listening on eth7, link-type EN10MB (Ethernet), capture size 96 bytes
09:40:07.129061 IP (tos 0x0, ttl 128, id 8233, offset 0, flags [DF], proto TCP (6), length 52)
    DD-WRT.987 > GalacticAC.hsd1.tx.comcast.net.nfs: Flags [S], cksum 0x0116 (correct), seq 834439307, win 8192, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
09:40:07.129113 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 52)
    GalacticAC.hsd1.tx.comcast.net.nfs > DD-WRT.987: Flags [S.], cksum 0x3afe (correct), seq 2204388309, ack 834439308, win 5840, options [mss 1460,nop,nop,sackOK,nop,wscale 5], length 0
09:40:07.136379 IP (tos 0x0, ttl 128, id 8234, offset 0, flags [DF], proto TCP (6), length 40)
    DD-WRT.987 > GalacticAC.hsd1.tx.comcast.net.nfs: Flags [.], cksum 0x919e (correct), ack 1, win 256, length 0
09:40:07.141668 IP (tos 0x0, ttl 128, id 8235, offset 0, flags [DF], proto TCP (6), length 84)
    DD-WRT.1220945707 > GalacticAC.hsd1.tx.comcast.net.nfs: 40 null
09:40:07.141723 IP (tos 0x0, ttl 64, id 62542, offset 0, flags [DF], proto TCP (6), length 40)
    GalacticAC.hsd1.tx.comcast.net.nfs > DD-WRT.987: Flags [.], cksum 0x91bb (correct), ack 45, win 183, length 0
09:40:07.142014 IP (tos 0x0, ttl 64, id 62543, offset 0, flags [DF], proto TCP (6), length 68)
    GalacticAC.hsd1.tx.comcast.net.nfs > DD-WRT.1220945707: reply ok 24 null
09:40:07.297588 IP (tos 0x0, ttl 128, id 8248, offset 0, flags [DF], proto TCP (6), length 40)
    DD-WRT.987 > GalacticAC.hsd1.tx.comcast.net.nfs: Flags [F.], cksum 0x9155 (correct), seq 45, ack 29, win 256, length 0
09:40:07.297817 IP (tos 0x0, ttl 64, id 62544, offset 0, flags [DF], proto TCP (6), length 40)
    GalacticAC.hsd1.tx.comcast.net.nfs > DD-WRT.987: Flags [F.], cksum 0x919d (correct), seq 29, ack 46, win 183, length 0
09:40:07.301648 IP (tos 0x0, ttl 128, id 8249, offset 0, flags [DF], proto TCP (6), length 40)
    DD-WRT.987 > GalacticAC.hsd1.tx.comcast.net.nfs: Flags [.], cksum 0x9154 (correct), ack 30, win 256, length 0
^C
9 packets captured
9 packets received by filter
0 packets dropped by kernel

```

Oh and error 53 means " the network path was not found ". 

I might have to go to the server and run wireshark so i can filter better, also i'm gonna try my bro's win7 machine to see if it connects ... maybe i should try a wired connection to my router.

---

### Post by zonemikel on 2010-02-11
Ok now i'm really stumped, i loaded ubuntu onto my netbook via ext usb drive and tried to mount the drive on the server and it still didnt work

client
```

michael@UsbDrive:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:1d:7d:4a:50:d5  
          inet addr:192.168.3.103  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe4a:50d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5285840 (5.2 MB)  TX bytes:430859 (430.8 KB)
          Interrupt:18 

michael@UsbDrive:~$ sudo mount 192.168.3.133:/mnt/sdb4 /home/michael/server/
mount.nfs: access denied by server while mounting 192.168.3.133:/mnt/sdb4

```

server
```

zonemikel@GalacticAC:/etc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
zonemikel@GalacticAC:/etc$ sudo cat exports | grep netbook
/mnt/sdb4/ netbook(rw,sync,subtree_check,no_root_squash)
zonemikel@GalacticAC:/etc$ sudo cat hosts | grep netbook
192.168.3.103   netbook
zonemikel@GalacticAC:/etc$ sudo ping -c 1 netbook
PING netbook (192.168.3.103) 56(84) bytes of data.
64 bytes from netbook (192.168.3.103): icmp_seq=1 ttl=64 time=3.70 ms

--- netbook ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 3.706/3.706/3.706/0.000 ms

```

Whatever it is it is not a windows problem ... i think its more of a wireless to wired across my router problem. Funny ssh works fine though.

---

### Post by johnson.d on 2010-02-12
Now You can try the following steps to check whether the nfs server is working fine
1)$ exportfs
This command shows you the folders that are shared, if the output is empty it shows that no folders have been shared or server is not running

2) Try to mount the folder locally in the server itself. This may show you if there is any error with nfs server.You can use the following command

$ mount -t nfs localhost:/<share-path> /<mount-point>

---

### Post by zonemikel on 2010-02-12
> **johnson.d said:**
> Now You can try the following steps to check whether the nfs server is working fine
1)$ exportfs
This command shows you the folders that are shared, if the output is empty it shows that no folders have been shared or server is not running

2) Try to mount the folder locally in the server itself. This may show you if there is any error with nfs server.You can use the following command

$ mount -t nfs localhost:/<share-path> /<mount-point>

of course i've already tried exportfs .... that was in my first post. and i tried what you just said in my last post. 

I'm just wondering why wired-wired nfs sharing works but wired-wireless does not. I think i'm on my own though.

---

### Post by zonemikel on 2010-02-14
So i guess no one has run into this error before . . .

---

### Post by dmizer on 2010-02-14
Your exports file should look like this:
```
/mnt/sdb4/ 192.168.3.0/24(rw,sync,subtree_check,no_root_squash)
```

---

### Post by johnson.d on 2010-02-15
NFS server has an option of working in insecure mode (Allowing higher incoming port numbers). Windows NFS client often uses higher port numbers. You can enable this option by adding an option to the share
Example: /share *(insecure,rw)

You can also try installing Windows services for UNIX package which contains a nfs client. You can try to connect the nfs server using this utility and cross check again. You can download the package from the following link
[http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=896c9688-601b-44f1-81a4-02878ff11778&displayLang=en](http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=896c9688-601b-44f1-81a4-02878ff11778&displayLang=en)

---

### Post by Jose Catre-Vandis on 2010-02-15
I gave up trying to get Windows 7 to connect to my nfs server in the end, having had previous successes in XP and Vista using the UNIX toolset. To gain access to the files on the server I set up samba. This was easy and just works. Also makes life easier if other Windows machines come into the network. Not the answer you want, but an alternative solution. These is a great howto on the forum about how to do this.

---

### Post by zonemikel on 2010-02-16
wow it worked ! all i did was as suggested 
```
/mnt/sdb4/ 192.168.3.0/24(rw,sync,subtree_check,no_root_squash)
```

and that made it work ? no idea why but i'm happy. I made it ro since im opening it up to all puters on the router. 

thanks

---

### Post by zonemikel on 2010-02-16
well i spoke too soon, it mounts it and all but it never opens it. It just times out then says it took longer than some timeoute value. unusable even with the insecure option . . .

---

### Post by dmizer on 2010-02-16
> **zonemikel said:**
> well i spoke too soon, it mounts it and all but it never opens it. It just times out then says it took longer than some timeoute value. unusable even with the insecure option . . .

All machines work except Win7?

---

### Post by zonemikel on 2010-02-16
> **dmizer said:**
> All machines work except Win7?

All machines work except wireless. I need to boot from my usb drive to test to see if i can connect to it via ubuntu/wireless, sorry didnt have time today. 

Its weird because it mounts it and shows it but then when you click on it the progress bar just takes forever then it says
```

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\NetBook>mount server:/mnt/sdb4 x:
x: is now successfully connected to server:/mnt/sdb4

The command completed successfully.

C:\Users\NetBook>x:
The semaphore timeout period has expired.

C:\Users\NetBook>


```

I'll use ubuntu tomorrow on my netbook and see if it works, thanks for the help so far
!

---

### Post by zonemikel on 2010-02-17
Wow it is a windows7 only problem. I just loaded ubuntu on my netbook via my usb hdd and it connected fine. 

```
michael@UsbDrive:~$ sudo mount 192.168.3.133:/mnt/sdb4/ /home/michael/server/
[sudo] password for michael: 
michael@UsbDrive:~$ cd /home/michael/server/
michael@UsbDrive:~/server$ ls
backup  free  lost+found  movies  old30gig
michael@UsbDrive:~/server$ 

```

I wonder why it does not work in windows

---

### Post by dmizer on 2010-02-17
Are you running Win7 in a virtual machine?

---

### Post by zonemikel on 2010-02-18
> **dmizer said:**
> Are you running Win7 in a virtual machine?

No, windows 7 is the default os on the computer (its hdd). I just have a usb drive that has ubuntu on it for when i want to use ubuntu. 

I kinda give up .... i think windows 7 just does not want to work with NFS.

---

### Post by doghousedean on 2010-03-20
I was having the same problem as this but with FreeNAS, this is a FreeBSD based NAS server.

Anyway, I solved it.

all you have to do is enable the samba service, dont create any shares with it or anything, just enable the service and it works fine.

---

### Post by doghousedean on 2010-03-20
Spoke too soon, while it adds the mounted drive it doesnt show any contents

---

### Post by buggyb on 2010-05-24
> **doghousedean said:**
> I was having the same problem as this but with FreeNAS, this is a FreeBSD based NAS server.

Anyway, I solved it.

all you have to do is enable the samba service, dont create any shares with it or anything, just enable the service and it works fine.

you are lucky then, my win7 with FreeNAS server - always works fine with NAS's samba mounts (but slow) and never show contense of the NAS's nfs export mounts! ((:

logs:

D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>showmount -e nas1
&#1057;&#1087;&#1080;&#1089;&#1082;&#1072; &#1101;&#1082;&#1089;&#1087;&#1086;&#1088;&#1090;&#1072; &#1085;&#1072; nas1:
/mnt/ide0-data/                    192.168.0.0
/mnt/ad6-data/                     192.168.0.0

D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>mount -o casesensitive=yes -u:ilya -p:xxx nas1:/mnt/ad6-data *
Z: &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085; &#1082; nas1:/mnt/ad6-data
&#1050;&#1086;&#1084;&#1072;&#1085;&#1076;&#1072; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1072;.

D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>mount -o casesensitive=yes -u:root -p:xxx nas1:/mnt/ide0-data *
Y: &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085; &#1082; nas1:/mnt/ide0-data
&#1050;&#1086;&#1084;&#1072;&#1085;&#1076;&#1072; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1072;.
D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>

D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>mount
&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;    &#1059;&#1076;&#1072;&#1083;&#1077;&#1085;&#1085;&#1099;&#1081;                                 &#1057;&#1074;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;
-------------------------------------------------------------------------
Z:       \\nas1\mnt\ad6-data                    UID=0, GID=0
                                                rsize=8192, wsize=8192
                                                mount=soft, timeout=0.8
                                                retry=3, locking=yes
                                                fileaccess=777, lang=ANSI
                                                casesensitive=no
                                                &#1089;&#1077;&#1082;.=sys
Y:       \\nas1\mnt\ide0-data                   UID=0, GID=0
                                                rsize=8192, wsize=8192
                                                mount=soft, timeout=0.8
                                                retry=3, locking=yes
                                                fileaccess=777, lang=ANSI
                                                casesensitive=no
                                                &#1089;&#1077;&#1082;.=sys
---
D:\Users\&#1040;&#1076;&#1084;&#1080;&#1085;&#1080;&#1089;&#1090;&#1088;&#1072;&#1090;&#1086;&#1088;>dir z:
 &#1058;&#1086;&#1084; &#1074; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1077; Z &#1085;&#1077; &#1080;&#1084;&#1077;&#1077;&#1090; &#1084;&#1077;&#1090;&#1082;&#1080;.
 &#1057;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#1085;&#1086;&#1084;&#1077;&#1088; &#1090;&#1086;&#1084;&#1072;: FFFF-FFFF
 &#1057;&#1086;&#1076;&#1077;&#1088;&#1078;&#1080;&#1084;&#1086;&#1077; &#1087;&#1072;&#1087;&#1082;&#1080; Z:\
&#1060;&#1072;&#1081;&#1083; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;

In explorer, Z: has 0 byte free from 0 byte NFS!
All this under local Administrator's login, no AD, only workgroup.

Seems that Win7 give _NO ACCESS RIGHTS_ to the NFS mounts and in Z: disk properties I can't change anything under NFS attributes - access denied! Any ideas?! Thanx.

---

