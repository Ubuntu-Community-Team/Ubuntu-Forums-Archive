---
title: "Need help with wireless issue"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by dizbah on 2006-06-10
Hello everyone.  I have a laptop with the dell 1350 built in wireless.  I follwed the driver installation instructions from [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=dell+1350+wireless](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=dell+1350+wireless) and after rebooting, my wireless light is lit on the laptop.  I am unable to connect to any wireless network. My network connection shows that eth1 (my wireless connection) is disconnected.  I tried to deactive and activate in network tools and have no luck in resolving the issue.  Before I was at least able to scan for wireless networks and now I can't even do that.  Any help would be greatly appreciated.  This wireless issue is the only thing keeping me from dumping windows and going to ubuntu full time.  ](*,)

---

### Post by evilghost on 2006-06-10
Can you try using ndiswrapper?  I've got a BCM43XX chipset on my laptop and I am using ndiswrapper with Dapper without issues.  I tried the native BCM43XX drivers without success.

I had to add bcm43xx to /etc/modprobe.d/blacklist for ndiswrapper to work successfully.

```

luser@zd7000:~$ lspci|grep -i broad
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
luser@zd7000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"GO-AWAY-11"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:06:25:49:3F:09
          Bit Rate:11 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-44 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luser@zd7000:~$

```

---

### Post by dizbah on 2006-06-10
Yes, I tried it butno go :(

root@ubuntu:~/Desktop#  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"netgear"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:3939-6D61-7869-6D61-0000-0000-00   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

