---
title: "mobile broadband connection tcp not always working"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by svaens on 2010-01-12
Hi all, 

I have a strange problem with my mobile broadband connection. I hope I am not the only one (so it will be fixed), but since I haven't found any others having the same problem yet, I am not so confident.

I started using mobile broadband, via a HUAWEI E1762 HSPA USB stick since Jaunty. I've had the same problem in jaunty as I do now in Karmic. Although in Karmic, i've had additional problems (that problem i've found listed as a known bug).

The problem is that when I get my mobile broadband to connect, it is sometimes, somehow, not fully connected. 
Symptoms are as follows:

1. panel icon shows connected and good strength (good)
2. skype connects, and I can chat and voip (good)
3. ping does not work (bad)
4. http does not work, i.e. Can't browse the web (bad)

It takes a couple of reconnects (i.e. taking the stick out and putting it back in again) to get it to connect properly. 

I'm using Ubuntu Karmic koala, 9.10, up to kernel - 2.6.31-17-generic

Anyone had the same problem? 

Anyone know how to fix it?

Does it sound like a bug I should submit ? 
If so, anyone got suggestions as to what I should submit with it, to lessen the possibility of it being marked as 'invalid' or 'incomplete'. 

Kind Regards All, 

sean

---

### Post by alexfish on 2010-01-13
Hi

which version of Ubuntu are you using

---

### Post by svaens on 2010-01-13
Got ubuntu Karmic, kernel 2.6.31-17-generic

Sorry. Should have mentioned that in the first place.

---

### Post by alexfish on 2010-01-13
hi

Can't seem to find a listing for this device but we will try and find something

from the terminal try this code

lsusb

and post the results if possible

---

### Post by svaens on 2010-01-13
Hi. 

Doing that command shows that it seems that it is being treated as an E220/E270. I guess my device might be quite new. I am not sure.

sean@svUbuntuX2:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183d Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sean@svUbuntuX2:~$ 


Of course, like I said, It doesn't fail all the time. It is just interesting that when it DOES fail, it seems to get so close to normally working (i.e Skype is still working through it, but not ping or http) that I figured it is a shame not to see if someone knows something about it.

---

### Post by alexfish on 2010-01-13
For got to add these  from seperate terminals

ls -al /dev/ttyU*

tail /var/log/messages

/sbin/route -n


try these in set modes ie < when you have a connection and the browser is working
and when the browser is not working

sometimes a reboot will help with the outputs

---

### Post by svaens on 2010-01-13
Hi again. Got what you asked for (i think).

1. With working http connection
------------------------------------
```

sean@svUbuntuX2:~$ ls -al /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2010-01-14 05:23 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2010-01-14 05:23 /dev/ttyUSB1
sean@svUbuntuX2:~$ 


sean@svUbuntuX2:~$ tail /var/log/messages
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.934256] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.934268] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.934279] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.986553] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.986562] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jan 14 07:43:27 svUbuntuX2 kernel: [ 9237.986572] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jan 14 07:43:28 svUbuntuX2 kernel: [ 9239.077507] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 14 07:43:28 svUbuntuX2 kernel: [ 9239.173425] UDF-fs INFO UDF: Mounting volume 'CUCKOOS_NEST_PAL1', timestamp 1998/11/06 11:37 (1294)
Jan 14 07:49:01 svUbuntuX2 kernel: [ 9572.024509] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000
Jan 14 07:49:01 svUbuntuX2 pulseaudio[2722]: ratelimit.c: 87 events suppressed
sean@svUbuntuX2:~$ 



sean@svUbuntuX2:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
sean@svUbuntuX2:~$ 


```


2. Not working hspa connection
---------------------------------
p.s I unplugged it twice, only to have it still work. Then I clicked on the icon in the panel to get it to disconnect, then re-connect this way, and this time it doesn't working. Skype still connected, but no ping.

```

sean@svUbuntuX2:~$ ls -al /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2010-01-14 08:07 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2010-01-14 08:06 /dev/ttyUSB1
sean@svUbuntuX2:~$ 




sean@svUbuntuX2:~$ tail /var/log/messages
Jan 14 08:07:28 svUbuntuX2 pppd[16818]: Exit.
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: pppd 2.4.5 started by root, uid 0
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: Using interface ppp0
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: CHAP authentication succeeded
Jan 14 08:07:33 svUbuntuX2 pppd[17968]: CHAP authentication succeeded
Jan 14 08:07:42 svUbuntuX2 pppd[17968]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 14 08:07:42 svUbuntuX2 pppd[17968]: local  IP address 115.70.25.17
Jan 14 08:07:42 svUbuntuX2 pppd[17968]: remote IP address 10.64.64.64
sean@svUbuntuX2:~$ 



sean@svUbuntuX2:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
sean@svUbuntuX2:~$ 

```



And here is what happened in the log after I again disconnected and reconnected to successfully get it to work again)

```
Jan 14 08:11:37 svUbuntuX2 pppd[17968]: Modem hangup
Jan 14 08:11:37 svUbuntuX2 kernel: [10928.691494] usb 2-2: USB disconnect, address 12
Jan 14 08:11:37 svUbuntuX2 kernel: [10928.691889] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 14 08:11:37 svUbuntuX2 kernel: [10928.691901] option 2-2:1.0: device disconnected
Jan 14 08:11:37 svUbuntuX2 kernel: [10928.692029] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 14 08:11:37 svUbuntuX2 kernel: [10928.692045] option 2-2:1.1: device disconnected
Jan 14 08:11:37 svUbuntuX2 pppd[17968]: Connect time 4.0 minutes.
Jan 14 08:11:37 svUbuntuX2 pppd[17968]: Sent 61905 bytes, received 62072 bytes.
Jan 14 08:11:38 svUbuntuX2 pppd[17968]: Connection terminated.
Jan 14 08:11:38 svUbuntuX2 pppd[17968]: Exit.
Jan 14 08:11:45 svUbuntuX2 kernel: [10936.687092] usb 2-2: new high speed USB device using ehci_hcd and address 13
Jan 14 08:11:46 svUbuntuX2 kernel: [10936.818741] usb 2-2: configuration #1 chosen from 1 choice
Jan 14 08:11:46 svUbuntuX2 kernel: [10936.820848] scsi33 : SCSI emulation for USB Mass Storage devices
Jan 14 08:11:46 svUbuntuX2 kernel: [10936.829288] scsi34 : SCSI emulation for USB Mass Storage devices
Jan 14 08:11:46 svUbuntuX2 kernel: [10936.835051] usb 2-2: USB disconnect, address 13
Jan 14 08:11:50 svUbuntuX2 kernel: [10941.700526] usb 2-2: new high speed USB device using ehci_hcd and address 14
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.844076] usb 2-2: configuration #1 chosen from 1 choice
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.846055] option 2-2:1.0: GSM modem (1-port) converter detected
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.846131] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.846295] option 2-2:1.1: GSM modem (1-port) converter detected
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.846337] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.846728] scsi37 : SCSI emulation for USB Mass Storage devices
Jan 14 08:11:51 svUbuntuX2 kernel: [10941.847240] scsi38 : SCSI emulation for USB Mass Storage devices
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.851741] scsi 37:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.852839] scsi 38:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.867132] sr1: scsi-1 drive
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.867305] sr 37:0:0:0: Attached scsi generic sg2 type 5
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.867434] sd 38:0:0:0: Attached scsi generic sg3 type 0
Jan 14 08:11:56 svUbuntuX2 kernel: [10946.876616] sd 38:0:0:0: [sdb] Attached SCSI removable disk
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: pppd 2.4.5 started by root, uid 0
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: Using interface ppp0
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: CHAP authentication succeeded
Jan 14 08:11:56 svUbuntuX2 pppd[25289]: CHAP authentication succeeded
Jan 14 08:12:07 svUbuntuX2 pppd[25289]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 14 08:12:07 svUbuntuX2 pppd[25289]: local  IP address 115.70.25.17
Jan 14 08:12:07 svUbuntuX2 pppd[25289]: remote IP address 10.64.64.64
Jan 14 08:12:07 svUbuntuX2 pppd[25289]: primary   DNS address 220.233.0.3
Jan 14 08:12:07 svUbuntuX2 pppd[25289]: secondary DNS address 220.233.0.4
Jan 14 08:13:24 svUbuntuX2 pppd[25289]: Protocol-Reject for unsupported protocol 0xfac5
sean@svUbuntuX2:~$ 

```

---

### Post by alexfish on 2010-01-13
ok need one more test

when working

code

[COLOR=Navy][COLOR=Black]ping -c 5 custard.bris.ac.uk

then when not working  ie skype same code


[/COLOR][/COLOR]

---

### Post by darknoobie on 2010-01-13
I had the exact same problem. Went into altell and had it replaced and i haven't had a problem since.

---

### Post by svaens on 2010-01-13
Ok. Making some progress actually. 

That's a test I should have done to begin with:


1. Test with a working web connection
```

sean@svUbuntuX2:~$ ping -c 5 custard.bris.ac.uk
PING custard.bris.ac.uk (137.222.253.92) 56(84) bytes of data.
64 bytes from custard.bris.ac.uk (137.222.253.92): icmp_seq=1 ttl=43 time=699 ms
64 bytes from custard.bris.ac.uk (137.222.253.92): icmp_seq=2 ttl=43 time=386 ms
64 bytes from custard.bris.ac.uk (137.222.253.92): icmp_seq=3 ttl=43 time=366 ms
64 bytes from custard.bris.ac.uk (137.222.253.92): icmp_seq=4 ttl=43 time=385 ms
64 bytes from custard.bris.ac.uk (137.222.253.92): icmp_seq=5 ttl=43 time=403 ms

--- custard.bris.ac.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4984ms
rtt min/avg/max/mdev = 366.789/448.290/699.347/126.059 ms
```


disconnect it. It is not working (but skype still does)

2. Test with no working web

```
sean@svUbuntuX2:~$ ping -c 5 custard.bris.ac.uk
ping: unknown host custard.bris.ac.uk

```


At this stage, I wondered (although disbelievingly) if it would ping when using pure ip address (skip the name resolving)


3. With working web

```

sean@svUbuntuX2:~$ ping -c 5 137.222.253.92
PING 137.222.253.92 (137.222.253.92) 56(84) bytes of data.
64 bytes from 137.222.253.92: icmp_seq=1 ttl=43 time=978 ms
64 bytes from 137.222.253.92: icmp_seq=2 ttl=43 time=696 ms
64 bytes from 137.222.253.92: icmp_seq=3 ttl=43 time=642 ms
64 bytes from 137.222.253.92: icmp_seq=4 ttl=43 time=661 ms

--- 137.222.253.92 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4017ms
rtt min/avg/max/mdev = 642.845/745.057/978.865/136.384 ms

```


4. With web not working (but skype still working)

```
sean@svUbuntuX2:~$ ping -c 5 137.222.253.92
PING 137.222.253.92 (137.222.253.92) 56(84) bytes of data.
64 bytes from 137.222.253.92: icmp_seq=1 ttl=43 time=386 ms
64 bytes from 137.222.253.92: icmp_seq=2 ttl=43 time=378 ms
64 bytes from 137.222.253.92: icmp_seq=3 ttl=43 time=377 ms
64 bytes from 137.222.253.92: icmp_seq=4 ttl=43 time=377 ms
64 bytes from 137.222.253.92: icmp_seq=5 ttl=43 time=379 ms

--- 137.222.253.92 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4013ms
rtt min/avg/max/mdev = 377.082/379.820/386.344/3.403 ms

```


ah ha! So, then this, i'm almost sure, indicates more precisely where the problem lies. But I am still not so sure. Is it with my provider? Although I do not think this problem occurs on windows when my girlfriend is using the usb modem....  

How does the modem setup a connection with the DNS ??

---

### Post by svaens on 2010-01-13
Ok. Since I know more about this bug i've found a new post (to which you've replied, Alex), and also a bug report. 

I will link the better worded ubuntu forum item here (which also mentions the bug)

[http://ubuntuforums.org/showthread.php?t=1346481](http://ubuntuforums.org/showthread.php?t=1346481)

---

