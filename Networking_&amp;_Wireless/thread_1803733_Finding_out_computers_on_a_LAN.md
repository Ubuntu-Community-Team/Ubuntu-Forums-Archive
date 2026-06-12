---
title: "Finding out computers on a LAN"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by BeaverDono on 2011-07-13
I am one lazy person, I'll admit it. 

Just to gain access to one of my computer across the house I use VNC a lot but the computer changes its IP address every so often that I refuse to just get up and check it. Without giving that computer a static IP address, is there a way to hunt down the computer's IP?

---

### Post by matt_symes on 2011-07-13
Hi

Try this,

```
sudo apt-get install nmap
```Enter your password. It will not be echoed to the screen. It's not installed by default.

```
sudo nmap -sP 192.168.1.0/24
```Change 192.168.1.0/24 to match your subnet. Gives output along the lines of (redacted)
```

matthew@matthew-laptop:~/my_documents$ sudo nmap -sP 192.168.1.0/24
Starting Nmap 5.00 ( http://nmap.org ) at 2011-07-14 00:07 BST
Host xxxxxx (192.168.1.1) is up (0.0038s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Asustek Computer)
Host matthew-laptop (192.168.1.102) is up.
Host xxxxx (192.168.1.109) is up (0.013s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Intel)
Host xxxxxxxx (192.168.1.133) is up (0.012s latency).
MAC Address: xx:xx:xx:xx:xx:xx (D-Link)
Host xxxxxx (192.168.1.134) is up (0.012s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Unknown)
Host xxxxxxxxxxxx (192.168.1.142) is up (0.014s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Elitegroup Computer System Co.)
Nmap done: 256 IP addresses (6 hosts up) scanned in 3.02 seconds
matthew@matthew-laptop:~/my_documents$ 
```And don't be so lazy ;)

Kind regards

---

### Post by BeaverDono on 2011-07-13
I completely forgot about nmap! XD

You're a life saver, thank you! :D

---

