---
title: "Limited connectivity for clients"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by jclholdings on 2010-02-06
Hello,
 
I have an ubuntu 9.10 box, windows clients (xp, vista and win7 all tried) can ssh in on port 22, but can't seem to connect in on any other ports.
 
Ubuntu box:
192.168.1.101 - wmp54g - gateway 192.168.1.1 (wrt54g) - mask - 255.255.255.0 - dns - 192.168.1.1
 
From the Ubuntu box:
 
ssh to localhost (22) works,
ssh to 192.168.1.101 (22) works,
in firefox: [http://192.168.1.101:631](http://192.168.1.101:631) works (cups port)
configure firefox to connect via proxy 127.0.0.1 port 3128 (tinyproxy port) works
configure firefox to connect via proxy 192.168.1.101 port 3128 works
configure firefox to connect via proxy 127.0.0.1 port 8080 (dansguardian port) works
configure firefox to connect via proxy 192.168.1.101 port 8080 works
 
From a windows box (192.168.1.102 for example.. have tried from 4 different machines with same results):
 
ssh to 192.168.1.101 (22) works
in IE: [http://192.168.1.101:631](http://192.168.1.101:631) does *not* work
configure IE to connect via proxy 192.168.1.101 port 3128 does *not* work
configure IE to connect via proxy 192.168.1.101 port 8080 does *not* work
 
I'll post some of the things I've tried in the next reply
 
Thanks in advance!

---

### Post by jclholdings on 2010-02-06
I've tried both network manager and wicd with the same results.
 
My current routing table:
 
[EMAIL="user@host:~$"]user@host:~$[/EMAIL] netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

I ran ubuntu 8 for a long time with success, my problems started with 9 (9.04 and 9.10 both tried)... I can't seem to find an iso image for 8 to re-install and try 8 again.
 
Each time I try to connect from the windows box, an entry in syslog is produced... so it appears the ubuntu box is getting the packets, but where they go after that is a mystery to me... Is this some type of access restriction?
 
I feel like this is something simple I'm overlooking but just can't think of it... please help! I'll provide any logs needed.
 
Thanks again!

---

### Post by jclholdings on 2010-02-06
One other item to note:
 
All the failed connection scenarios seem to be browser oriented... the ssh connection that works is outside of a browser... not sure if that matters

---

### Post by jclholdings on 2010-02-07
The windows box can ping the ubuntu box, but the ubuntu box can not ping the windows box

---

### Post by jclholdings on 2010-02-07
bump

---

### Post by jclholdings on 2010-02-10
No thoughts anyone? I'll take any advice... i.e. what the problem can not be, so I can narrow down my troubleshooting...
 
On a side track, does anyone know where I can get an ubuntu 8 iso to install that and see if the problems go away?
 
Thanks!

---

### Post by jclholdings on 2010-02-11
bump

---

### Post by jclholdings on 2010-02-14
Update... Installed 8.04 and the problem went away... but it was really really slow... 
 
Moved the ubuntu box next to my wireless router and used a wire to connect it and turn the wireless interface off... speed went way up...
 
I'm going to try to install 9.10 again tomorrow to see if this is all somehow a bad combination of 9 and wireless.

---

### Post by jclholdings on 2010-02-14
Well, installed 9.10 and the problem came back without using wireless... so that suggests to me a configuration problem somewhere...
 
I'm really surprised nobody has replied to this thread... are y'all stumped?

---

### Post by Iowan on 2010-02-15
> **jclholdings said:**
> 
I'm really surprised nobody has replied to this thread... Yeah, me too... I'm not sure how I keep missing it - I "discovered" it via your [other]("http://ubuntuforums.org/showthread.php?p=8831035#post8831035") thread. Not that I have a lot of (any) useful information (wireless ain't my forte)- but you DO deserve a response...
> **jclholdings said:**
> The windows box can ping the ubuntu box, but the ubuntu box can not ping the windows boxThere's another thread around here with similar problem...
> **jclholdings said:**
> Well, installed 9.10 and the problem came back without using wireless... ?Same problem - machines can ping and SSH, but nothing else?
Have you considered installing a (secure) FTP server to see if it works?

---

### Post by ant2ne on 2010-02-15
windows wont answer the ping unless the firewall is configured. I forget the exact setting, but it is something stupid like file sharing or something. In fact, your other problems could be firewall related. I'd turn off all firewalls and see if the problem persists. If it goes away then you can start re-enabling firewall features until something breaks it. Then you've found the setting.

---

### Post by jclholdings on 2010-02-19
> **ant2ne said:**
> windows wont answer the ping unless the firewall is configured. I forget the exact setting, but it is something stupid like file sharing or something. In fact, your other problems could be firewall related. I'd turn off all firewalls and see if the problem persists. If it goes away then you can start re-enabling firewall features until something breaks it. Then you've found the setting.

Sorry guys I haven't responded... I got it working with 8 so I've kinda forgotten about this... so ubuntu 9 comes with a firewall on it where 8 didn't? If this is so, that would make sense... I figured something new happened in 9 that needed to be configured that I didn't know about.

---

### Post by jclholdings on 2010-02-19
> **Iowan said:**
> 

Have you considered installing a (secure) FTP server to see if it works?

I tried installing openssh-server so I could ssh in and that worked... but I didn't try SFTP... I would expect that they would both respond similarly since they are both SSH based.

---

