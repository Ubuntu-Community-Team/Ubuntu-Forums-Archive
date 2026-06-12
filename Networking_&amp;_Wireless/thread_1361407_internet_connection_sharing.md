---
title: "internet connection sharing"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by rachmat.hidayat on 2009-12-22
Dear all, 

I have a problem with Internet connection sharing on karmic-koala. 
This is the simple topology that I use:

PC (win) [eth0] -- [eth0] laptop (ubuntu) [usb: ppp0] -- INTERNET 

note: 
- on my laptop, I use MV140B evdo wireless modem -- it's use USB type connection
- so in this case, the interface that directly connect to the Internet is ppp0 (via MV140B)
  and the interface that connected to the internal LAN is eth0
- in case, the internal subnet prefix is 192.168.0.0/24

so, how can I make my laptop as an internet gateway? 
I try to googling, found several link, and I didn't found that fit my case yet. 
here some link that I found.. 
- [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
- [http://ubuntuforums.org/showthread.php?t=431707](http://ubuntuforums.org/showthread.php?t=431707)
- etc. 

please help :(
best regard, 
~matt

---

### Post by rachmat.hidayat on 2009-12-22
is it possible to forwarding packet from ethernet to usb? 
i'm affraid it won't work because of it. 

please help :(

---

### Post by lukeiamyourfather on 2009-12-22
If you haven't yet, read this.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Not sure how the system recognizes the USB modem though. Cheers!

---

### Post by rachmat.hidayat on 2009-12-22
> **lukeiamyourfather said:**
> If you haven't yet, read this.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Not sure how the system recognizes the USB modem though. Cheers!

yeap, thanks for sharing.. 
but i have read that link.. 
still didn't work yet.. 

I follow this part:
[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables))

---

### Post by iponeverything on 2009-12-22
Add these to your /etc/rc.local:

```

iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Make sure your windows machine has the gateway machine as its default gw. And that it has vaild DNS servers:

```

8.8.8.8
8.8.4.4

```

Also make sure that there are no firewall rules in place that will prevent it from working:
```

sudo ipables -L -n

```

Also,, first things first -- can the machines ping each other?

---

### Post by Cha1ns on 2009-12-23
So I set up ICS in ubuntu 9.10 to share from my wireless to a windows machine. She was very happy; it was good. 

I lost the wireless connection and switched to another wireless network and everything broke. I had to reboot and start over ... no love... why the heck doesn't 9.10 just use ipmasq.

I got the wireless back, got ping to work... was pinging from windows to google.com, and I even pinged facebook.com.

But websites still won't load. Then I loaded [www.google.com](www.google.com)... google WORKED. In fact, all Google websites work on the Windows machine. Blogger,gmail,reader u name it! Nothing on the Internet will load other than Google...

Now can some one please tell me how the heck that's possible? Some guesses after staring at wireshark: "Destination unreachable fragmentation needed"

---

### Post by iponeverything on 2009-12-23
try changing your mtu.

---

