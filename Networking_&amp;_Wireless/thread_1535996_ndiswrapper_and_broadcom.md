---
title: "ndiswrapper and broadcom"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2010-07-21
I followed the ndiswrapper install instructions online and everything installed correctly.  But my network manager isnt showing a wireless connection

```

kclark@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 70:1a:04:a0:8d:4b  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fea0:8d4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1799 errors:0 dropped:0 overruns:0 frame:4601
          TX packets:1409 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:954654 (954.6 KB)  TX bytes:243127 (243.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6689 (6.6 KB)  TX bytes:6689 (6.6 KB)

```

```

kclark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:182  Noise level:171
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

what do I do?!?

---

### Post by snowpine on 2010-07-21
eth1 is your wireless.

Is there a reason you're using ndiswrapper?? Broadcom provides native Linux drivers that work very well.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by kr651129 on 2010-07-21
Because the native drivers are slow slow slow, I just got it working. I know that eth1 was my wifi but that was my STA drivers from the repos.

What I had to do was add the following to blacklist.conf

```

blacklist wl1
blacklist bcm43xx
blacklist b43
blacklist b44

```

b44 and wl1 were not on ubuntu's instructions, also this did not work until I ran the following command

```

sudo update-initramfs -k all -u
sudo reboot

```

and BAM my connection speed has doubled

---

### Post by snowpine on 2010-07-21
That is cool, did not realize there will be a performance boost. Will have to give it a try! :)

---

### Post by kr651129 on 2010-07-21
Yeah, it's made a major difference.  The internet speed and netflix are the only two reasons I dual boot Microsoft anymore and now that I've got netflix working via virtual box and the same performance on my wifi as windows I think it's time to free up the dead weight on my hdd.

---

