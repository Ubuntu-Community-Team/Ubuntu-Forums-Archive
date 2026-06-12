---
title: "Wireless support.  Shows in iwconfig, but not ifconfit"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by krazyshane on 2006-06-22
Hello,

I'm new to ubunto, but i've played around in linux off and on  FC5 being my last try.

Well, I had to install from the "alternative" disk because the livecd didnt want to boot, but no worries, I'm at a desktop.  When installing, it picked up on my wireless card automatically =D> (the only other distro to ever do this was Mepis), but was unable to connect however.  

Now, I am connected via ethernet, but I still need to establish the wireless connection.  If I run 

sudo ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:0F:1F:27:E6:5B
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe27:e65b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:89100739 (84.9 MiB)  TX bytes:2467512 (2.3 MiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3147 (3.0 KiB)  TX bytes:3147 (3.0 KiB)


sudo iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Home"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:9764-4748-24   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Well, it seems that my wireless card shows up as "eth1" in iwconfig, but doesnt show up in ifconfig.

I've also tried running a scan

iwlist eth1 scan
> eth1      No scan results

I know that the wireless is functioning properly, and I can boot into windows and connect right away.  I could use a little push in the right direction.

This is a Dell Inspiron 8600 Laptop btw.

Thanks,
Shane

---

### Post by Third Thoughts on 2006-06-22
From the ifconfig manual 
> If no arguments are given, ifconfig displays the  status  of  the  currently active interfaces.

My guess is that iwconfig displays all interfaces active or not, though I didn't see one way or the other explicitly. Have you tried activating your wireless either using the network manager under System, or the command 
```
sudo ifup eth1
```
That might get things working.

~Andrew S.

---

### Post by krazyshane on 2006-06-22
Yes, I have tried that with no success.  I will go play around with it some more.  I'll disable wep and try.

Shane

---

### Post by krazyshane on 2006-06-22
Well.. it seems like I cannot activate the wireless card.  If I try to run

sudo ifup eth1
it returns "Ignoring unkown interface eth1=eth1."

Anyone know whats going on and why I cannot bring this interface up?  It never shows in ifconfig..

Shane

---

### Post by Third Thoughts on 2006-06-23
you could try to see if you could get things to work with ndiswrapper. 
Here's a how to for your card [http://www.ubuntuforums.org/showthread.php?t=189070&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=189070&highlight=broadcom)

~Andrew S.

---

### Post by Gaute65 on 2006-06-23
Read [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") wiki article. It did help me:) 


Good luck

---

### Post by cydec on 2006-06-24
Does it show in your network manager?
I had the same problem, it was simply not enabled, enabled it and it appeared in ifconfig.

---

