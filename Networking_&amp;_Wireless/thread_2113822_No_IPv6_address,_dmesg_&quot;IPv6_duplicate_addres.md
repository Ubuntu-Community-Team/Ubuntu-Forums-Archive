---
title: "No IPv6 address, dmesg: &quot;IPv6 duplicate address&quot;"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by sanderj on 2013-02-08
My ISP provides native IPv6. That used to work. But not anymore: dmesg says:

```
[51849.455380] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[52038.685221] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[52208.691846] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[52393.831468] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[52546.966404] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[52713.804952] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
```

(Note: I obfuscated my public IPv6 address by inserting the 'blalba' into the log above and below)

Googling that error message, I found [http://timesinker.blogspot.nl/2009/11/karmic-ipv6-global-address-problems.html](http://timesinker.blogspot.nl/2009/11/karmic-ipv6-global-address-problems.html) with this workaround:

```
sander@R540:~$ sudo sysctl net.ipv6.conf.eth0.accept_dad
net.ipv6.conf.eth0.accept_dad = 1

sander@R540:~$ sudo sysctl net.ipv6.conf.eth0.accept_dad=0
net.ipv6.conf.eth0.accept_dad = 0
```

That seemed to work a week ago (not 100% sure), but not anymore: dmesg now says:

```
[58037.095963] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[58037.519619] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:cdb:467c:e1e6:7532 detected!
[58038.424991] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:58eb:c65e:25e:b3c7 detected!
[58039.141499] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:a413:1a:2614:e16a detected!
[58039.141507] IPv6: ipv6_create_tempaddr: regeneration time exceeded - disabled temporary address support
```

and still no public IPv6 address on my wlan0 interface.

The command rdisc6 just shows a correct response from my modem:

```
sander@R540:~$ rdisc6 wlan0
Soliciting ff02::2 (ff02::2) on wlan0...

Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :          Yes
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :        30000 (0x00007530) milliseconds
Retransmit time           :  unspecified (0x00000000)
 Prefix                   : 2a00:cd8:blabla::/64
  Valid time              :        86400 (0x00015180) seconds
  Pref. time              :        86400 (0x00015180) seconds
 MTU                      :         1480 bytes (valid)
 Source link-layer address: 50:67:F0:D7:61:FB
 from fe80::5267:f0ff:fed7:61fb
sander@R540:~$
``` 

Ubuntu 12.10, fully updated.

Tips?

---

### Post by sanderj on 2013-02-08
I booted into Ubuntu 12.04.1 with Linux 3.2.0-25-generic, and the same problem is there.

So it is not a Linux version related problem.

---

### Post by sanderj on 2013-02-09
The 12.10 system now has an IPv6 address, but dmesg says:

```
[14790.090074] ICMPv6: NA: someone advertises our address 2a00:0cd8:blabla:1182:7070:8ebf:4fe1 on wlan0!
[14790.090228] ICMPv6: NA: someone advertises our address 2a00:0cd8:blabla:1af4:6aff:fe9c:ced4 on wlan0!
```


Tips welcome

---

### Post by prodigy_ on 2013-02-09
You should contact your ISP. Quite possibly there's indeed another host with the same IPv6.

---

### Post by sanderj on 2013-02-09
> **prodigy_ said:**
> You should contact your ISP. Quite possibly there's indeed another host with the same IPv6.

Another Ubuntu system (Ubuntu 11.10, Linux kernel 3.0.0-29-generic) is giving the same error message in dmesg. :-(

However, I tested with an Android phone and a Windows system, and they both have perfect IPv6 connectivity.

So, it is something between Ubuntu (Linux?) and the modem providing IPv6. I don't think there is a really a device with the same IPv6 address; it's Ubuntu / Linux that's thinking that ...

---

### Post by sanderj on 2013-02-09
Interesting, this seems to happen:

First I disable Wifi.
Then I enable Wifi.
I keep on 'refreshing' "ifconfig", and it shows there appears a (or two?) public IPv6 address for a second or so, and then it disappears. In my dmesg there is a line:

```
[24745.180130] IPv6: ipv6_create_tempaddr: regeneration time exceeded - disabled temporary address support
```

---

### Post by lemming465 on 2013-02-09
I agree it smells like an ubuntu and/or kernel bug.  If you don't care deeply about using RFC 4941 "privacy" addresses (62 random bits in the host part) instead of EUI-64 mapped addresses (46 bits of ethernet MAC in the host part), do you get better results with a workaround of turning off privacy addresses?```

sudo sysctl -w net.ipv6.conf.eth0.use_tempaddr=0
sudo sysctl -w net.ipv6.conf.wlan0.use_tempaddr=0
sudo service networking restart
```

---

### Post by sanderj on 2013-02-09
I tried that, but reloading the network ('sudo service networking restart') resulted in a broken GUI. So I did this:

With a 

```
sudo nano /etc/sysctl.conf
```

I put this into that file:

```
net.ipv6.conf.all.use_tempaddr=-1
```

then rebooted, and ... I have a public IPv6 address! :p

In the beginning of dmesg there is still some trouble:

```
[   94.863267] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:1af4:6aff:fe9c:ced4 detected!
[   95.486847] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:4047:1864:8b82:465 detected!
[   95.966238] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:315f:857:760b:4d6d detected!
[   97.149406] IPv6: wlan0: IPv6 duplicate address 2a00:cd8:blabla:e88d:4267:9fb6:e8b4 detected!
[   97.149412] IPv6: ipv6_create_tempaddr: regeneration time exceeded - disabled temporary address support
```

... but that doesn't seem to matter.

Oh ... and a pity I must disable privacy extensions to IPv6 working. But I'm glas I have IPv6 again.

Thank you for your help!

---

### Post by sanderj on 2013-02-09
PS: Is this is bug in Ubuntu / Linux? Or is it in the interaction with my modem doing IPv6?

---

### Post by sanderj on 2013-02-09
Update:

```
net.ipv6.conf.all.use_tempaddr=0
```

also works, although it takes about 5 minutes before a public IPv6 address appears on my wlan0

---

### Post by sanderj on 2013-02-09
Update: 

I created a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1120617](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1120617)

---

