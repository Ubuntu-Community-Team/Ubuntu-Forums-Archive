---
title: "unable to connect wireless network"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by aquarius18 on 2009-12-28
Hi, newbee here

successfully installed 9.04 Jaunty on my spare HDD.

My wireless network connection works a treat in WIN XP SP3 but does not respond in the 9.04 install.

I am using a new ASUS Wireless N Router RT-N13U (802.11 b/g/n) and ASUS Wireless N USB Adapter USB-N11.

Also tried to connect my PC directly to modem via wired LAN - to no avail.

Read through pytheas22 post at [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) and did the recommended search for ndiswrapper. Appears to be non-existent or at least was not found.

Any help is appreciated.

Frank

---

### Post by griffinjones on 2009-12-28
I guess try this first:
```
sudo apt-get install wireless-tools
```

Set the wlan to auto on all that, then I suggest attempting a restart.

---

### Post by aquarius18 on 2009-12-28
thanks, that was quick.

shall try this when I get back in an hour

Frank

---

### Post by aquarius18 on 2009-12-28
> **griffinjones said:**
> I guess try this first:
```
sudo apt-get install wireless-tools
```Set the wlan to auto on all that, then I suggest attempting a restart.

I did the install - it tells me that the latest version is already installed.

Where do I set the wlan to auto pls?

Thanks

---

### Post by aquarius18 on 2009-12-28
Last steps undertaken:

1. checked all cables - OK
2. rebooted router
3. ran ifconfig with this output:

	> [FONT=Arial, sans-serif]eth0      Link encap:Ethernet  HWaddr 00:24:8c:8c:f5:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:252 

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
 

I am stumped - can anyone help a newbie who desperately needs a cup of Ubuntu?

Thanks / Frank

---

### Post by Project PWNED on 2009-12-29
[http://ubuntuforums.org/showthread.php?t=1079015](http://ubuntuforums.org/showthread.php?t=1079015)

This might help you. From your ifconfig, it's not even listed. This isn't good..

---

### Post by aquarius18 on 2009-12-29
> **Project PWNED said:**
> [http://ubuntuforums.org/showthread.php?t=1079015](http://ubuntuforums.org/showthread.php?t=1079015)

This might help you. From your ifconfig, it's not even listed. This isn't good..

Thanks - Looks like the thread for me, I'll give this a go

---

### Post by aquarius18 on 2009-12-29
Gave it a try last night but was stumped by installing the "patch" as mentioned in the tutorial. Gave up at the end and connected my machine to the router via ethernet cable. Restarted and bingo .... I was online and flying. :guitar:

Since our router sits right next to my machine I can't be bothered configuring the ASUS USB adapter.

Thanks again heaps for your support

Frank

---

