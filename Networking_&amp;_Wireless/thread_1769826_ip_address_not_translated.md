---
title: "ip address not translated"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by akukol on 2011-05-28
Hello,

I am using xubuntu 11.04 and XFCE from a USB stick. After two days of no problems using Firefox, I could not access web-pages anymore and received the 'page not found' error. It works only, if I type in the numerical IP address. The same happens with the command line. So the internet access works fine, but IP addresses are not translated. Everything works on Windows Xp with the same Netgear WLAN router.

I had the same problem previously with Xubuntu 10.02, but it took a month to appear.

The info below might be helpful:
--------------------
output of ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:35:6b:ed  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe35:6bed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4707 (4.7 KB)  TX bytes:8954 (8.9 KB)

output of iwconfig:
wlan0     IEEE 802.11abg  ESSID:"admin"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:B2:40:D0   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:0

output of: route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

Maybe also interesting:
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
------------

I would be grateful for any help.
akukol

---

### Post by Lupajz on 2011-05-28
Have you tried changing DNS server ? I use those two IP addresses for DNS

```
8.8.8.8
8.8.4.4
```

Those are google public DNS servers and they work really fast for me ;)

---

### Post by Toz on 2011-05-28
> **akukol said:**
> Maybe also interesting:
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
Yikes! Looks like filesystem/directory corruption/damage. Best to check the drive for errors. ([http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)).

[edit]
/etc/resolv.conf is required to map ip addresses to names
[/edit]

---

### Post by akukol on 2011-05-28
Thanks Lupajz, but the DNS servers which are automatically assigned to the router/cable modem are fine. The internet works under Windows with the same DNS servers.

---

### Post by akukol on 2011-05-28
Thanks Toz,
I tried to check the drive for errors by following the instructions on the link, i.e. touch /forcefsck and then reboot the system. There was, however, no message or indication that anything happened during reboot.

The boot menu of the USB stick also provides the option to check file integrity, which I tried without any error messages.

However, it may be a faulty USB stick, which explains that the same problem that previously appeared after two months came up after two days with the new linux installation.

---

### Post by chili555 on 2011-05-28
> Thanks Lupajz, but the DNS servers which are automatically assigned to the router/cable modem are fine.However, they are not stored in your system, at least in any readable and usable way:> ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output errorPlease post:```
ls /etc | grep resolv
ls -al /etc/resolv.conf
```I agree with a previous post; you may have a disk read problem. If the file was empty, contained jibberish or was not accessible by other than root, there would be entirely different messages and the problem would be apparent.

---

### Post by Lupajz on 2011-05-28
> **akukol said:**
> Thanks Lupajz, but the DNS servers which are automatically assigned to the router/cable modem are fine. The internet works under Windows with the same DNS servers.

Yes U are right, automatically assigned DNS servers from router work fine under windows, but under linux they didn't worked for me :P I was able to connect to a webpage by typing address but the delays I was getting while loading page vere almost 1200ms :P

---

