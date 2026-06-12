---
title: "Wireless Card deteched, but not the networks"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by theyain on 2009-05-24
Okay, I'm using a gateway with a broadcom wireless card. I have followed these instructions to try and get it working, but no dice.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

the pci id of the card is 14e4:4318

ifconfig gives me

```

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:99:dd:74  
          inet6 addr: fe80::2e0:b8ff:fe99:dd74/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24519 (24.5 KB)  TX bytes:10225 (10.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:41:dc:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-41-DC-E6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

While lspci -vnn | grep 14e4 gives me

```

06:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Broadcom Corporation Device [14e4:0449]

```

I'm stuck and have no idea what to do.  Any thoughts?

---

### Post by rudy.b on 2009-05-24
Does the following wireless scan give you anything?

```
sudo iwlist wlan0 scan
```

---

### Post by theyain on 2009-05-29
I get ```

wlan0     No scan result

```

edit:  Aww, great, my ctrl key died on me :D

---

### Post by theyain on 2009-05-29
Bump

---

### Post by rootkowski on 2009-05-29
I've had the same problem on an old Acer Aspire 5000 with Broadcom BCM4318 (REV 02). Now, the "solution" will hardly be helpful and it is the weirdest thing ever. While I was looking for a solution and running commands from this thread the thing just started working! Just like that! I didn't do anything. Just all of the sudden it started showing available networks. Now you perhaps understand why this "solution" is not helpful. Connecting wasn't a problem at all. Now it just works.

BTW, I run Linux Mint 7 Gloria (based on Ubuntu 9.04).

Hope someone will find a logical solution! Cheers!

---

### Post by superprash2003 on 2009-05-30
most wireless cards( in laptops ) have a switch for its funtionality , ensure that the switch of your wifi card is set to ON

---

### Post by theyain on 2009-05-31
Already thought of that.  No help :(

---

### Post by theyain on 2009-06-02
Interestingly enough, I can now join the local wireless networks again.  I had done so many things before hand that I now have no idea what worked.

---

### Post by Chris The Ninja Pirate on 2009-06-05
Same card, tried the same way of installing the firmware and same initial result - na da!

Hope that I too will come across this magic bullet for fixing this.

EDIT - Hhmmm. Got bored of this and switched to Mandriva. Same problem cropped up but was solved by toggling the wireless radio on (Fn + F2). This shortcut did not work in Ubuntu but perhaps if I had figured out how to turn the wireless radio on/off I could have got it working.

---

### Post by reboskyz24 on 2009-06-08
> **rootkowski said:**
> I've had the same problem on an old Acer Aspire 5000 with Broadcom BCM4318 (REV 02). Now, the "solution" will hardly be helpful and it is the weirdest thing ever. While I was looking for a solution and running commands from this thread the thing just started working! Just like that! I didn't do anything. Just all of the sudden it started showing available networks. Now you perhaps understand why this "solution" is not helpful. Connecting wasn't a problem at all. Now it just works.

BTW, I run Linux Mint 7 Gloria (based on Ubuntu 9.04).

Hope someone will find a logical solution! Cheers!
Do you have any idea what you were running through when it started working?  I'm on a 5000 as well.  My wireless is now enabled, but I cannot connect to my WPA2 hidden network.

---

### Post by rootkowski on 2009-07-12
Hi reboskyz24!

sorry for not answering for such a long time, I just completely gave up on this thread since the laptop I then worked with wasn't mine. My sister-in-law got tired of all windows security issues and asked me to install linux for her. So I did. Though there were some problems with sis graphics and the mistery with wifi card. The wifi sometimes would work, sometimes it wouldn't. Just completely random. Sometimes just after some minutes after logging in the network manager would start showing available networks, sometimes it wouldn't. A thing that made it more difficult to know what was happening was that the wifi indicator on the laptop didn't work either. It just wouldn't flash, on or off. 

I don't know much about the network we were using since it was out neighbour's. Once the network manager would view available networks it worked to log in with default settings. 

Now, since I meet my sister-in-law like twice a year (live in different countries) I don't think I can be of much help on this topic. Anyway, I'll keep in mind to ask her about it next time we talk (but she uses her computer really rarely). 

Good luck anyway! Cheers

---

