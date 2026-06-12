---
title: "ICS through WiFi"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by obscurant1st on 2010-04-21
I searched and found lots of solutions for this. But none of them worked for me.

So what I am trying to do is,
I have an iphone, I am trying to get internet connectivity to that phone through wifi.
I dont have a wifi router. But i do have a laptop with wifi card. I am connecting to internet via cable modem.

In win7 I used to create an accesspoint and do the ics from ethernet card to share via wifi card. It used to work perfectly.
Now as I am sing ubuntu, i want to do the same.
I have intalled firestarter, and shared the internet connection through wifi card(wlan0).
After this I created an accesspoint using the gnome network applet. Now i can connect my ifone to ths accesspoint. But there is no internet connectivity in my fone.
What did i do wrong, and how can i resolve it, pls reply!!!

---

### Post by 2hot6ft2 on 2010-04-21
These should help in your quest. But beyond knowing where to find the info. on them I don't know how to fix your setup.

[To create a working wireless linux access point.]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint")
and
[Internet Connection Sharing (ICS)]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

---

### Post by obscurant1st on 2010-04-23
still i cant figure out how to do it! :(

---

### Post by Iowan on 2010-04-23
[Another]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") help page. What part of the procedure is causing problems?

---

### Post by obscurant1st on 2010-05-04
actually the accesspoint is created, and i am able to connect to that accesspoint through iphone. But internet connectivity is not there in iphone.
That is the problem.
Anyway i ll try the above page and try it out.

---

### Post by obscurant1st on 2010-05-08
i tried but not working,
when i tried to ping my ipod after getting connected to the wifi accesspoint this error came.
root@obscurant1st-laptop:/home/obscurant1st# ping 192.168.0.100
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
CFrom 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable

---

### Post by Iowan on 2010-05-08
Looks like something in routing - you can check **route -n**, but I think I'm missing something...

---

### Post by obscurant1st on 2010-05-14
ok, k let me check that from my itouch.. :)

---

