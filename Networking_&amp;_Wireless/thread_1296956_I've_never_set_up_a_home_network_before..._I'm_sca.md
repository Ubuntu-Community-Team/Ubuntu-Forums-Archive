---
title: "I've never set up a home network before... I'm scared!"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by the8thstar on 2009-10-21
Hello,

I want to set a home network between my two computers but I need help because I don't know what to do. Here is some technical info:

My desktop computer is a P4 with Ubuntu 9.04 installed, formatted to ext4 and linked to an external hard disk through a USB cable. That external disk is where I want to access the files remotely. In addition, a cable modem is connected to the computer through its ethernet port.

That modem has wifi capabilties and this is how I connect to the internet with my laptop computer (specs in sig).

The question is: how can I access my external hard disk remotely with my laptop computer? The external hard disk is a Western Digital with two firewire ports, one eSATA and one USB.

Thanks again for your help.

---

### Post by doas777 on 2009-10-21
well, for starters, go to both of the PCs while they are connected wirelessly, and run 
```
sudo ifconfig
``` from a terminal, and post the output. if they are on the same network, then you are golden. if not, some configuration (and possibly your own wifi router) will be required.

the first step is to get them to ping each other. 
then, once the network is established, you need to configure samba to share the hdd. 
after that, it's all about configuring your client to connect.

---

### Post by the8thstar on 2009-10-21
Here is the laptop output (connection through wlan0 I presume) :

> the8thstar@the8thstar-laptop:~$ sudo ifconfig
[sudo] password for the8thstar: 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:19:89:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30032 (30.0 KB)  TX bytes:30032 (30.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:c5:bc:09  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fec5:bc09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2413782 (2.4 MB)  TX bytes:447809 (447.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-C5-BC-09-63-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by the8thstar on 2009-10-21
And here is the output from the desktop (eth2):

> the8thstar@the8thstar-desktop:~$ sudo ifconfig
[sudo] password for the8thstar: 
eth2      Link encap:Ethernet  HWaddr 00:20:ed:95:b6:a0  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe95:b6a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30093077 (30.0 MB)  TX bytes:2798232 (2.7 MB)
          Interrupt:17 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1688 (1.6 KB)  TX bytes:1688 (1.6 KB)

---

### Post by doas777 on 2009-10-21
edit: you beat me to it. now try to ping back and forth. see below.

ok, so your laptop IP is 192.168.1.101, which bodes well for this experiment. 
now repeat the same command on your desktop, to find it's IP address as well.
(it'll be under "Inet Addr:" for eth0).

after that, make sure both pcs can ping eachother. 
 From desktop:
```
sudo ping 192.168.1.101 
```and from laptop:
```
sudo ping <IP address of desktop>
```make a mental note of each IP. you will need to know them before you're done.

let us know if the ping works, and then it is on to samba.

---

### Post by doas777 on 2009-10-21
next step is to install samba on your desktop
```
sudo apt-get install samba
```

then configure it within /etc/samba/smb.conf

this guide will help you with some of the configuration.
I would caution you to just configure the conf file rather than trying to share items from the GUI. never works right for me, and mixing the traditional methods with the ne wGUI stuff seems to cause some serious problems.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

now, will you be accessing shares while there is no user logged into the desktop?
if so, then you will need to reconfigure your IP settings on teh desktop:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
so that your network is online at the time samba tries to start.

---

### Post by the8thstar on 2009-10-21
OK, that works. They both ping and pull data from each other. Awaiting instructions! :)

---

### Post by the8thstar on 2009-10-21
bump

---

### Post by doas777 on 2009-10-21
after you install samba, in the "SettingUpSamba" link above, skip down to "Manual Server Configuration" for instructions on configuring the smb.conf file.

have you reconfigured your interfaces file on the server, or are you satisfied with the limitations of using network manager (that someone must always be logged into the desktop on the server before you can access any shares from a client)?

---

### Post by the8thstar on 2009-10-21
I get this strange issue when I want to select the folders I want to share (see attached). I added the line to samba.conf, to no avail. Any ideas?

---

### Post by the8thstar on 2009-10-22
bump

---

### Post by the8thstar on 2009-10-22
My Westell has some weird permissions problems which prevent file sharing.

---

### Post by doas777 on 2009-10-22
no idea what a westell is, but as I said previously, don't use teh GUI to share folders if you perform any part of the install manually. the reason a manual install is recomended, is that you must be interactively logged in on the server before remote clients can access GUI-shared folders. the user-space/system-space distinction is a real mess where samba is concerned.

also per forum guidelines, please bump only once per day.

---

### Post by the8thstar on 2009-10-22
This is too hard for me... the configuration work is too demanding and the way the external hard drive (Westell) behaves on the Firewire port is giving me headaches.

So no home network for now. I guess I'll wait for a fully stable GUI solution if it's ever released.

Anyway, thanks for your help and advice, **doas777**. I'm pretty sure other users will read this thread and succeed where I didn't.

---

