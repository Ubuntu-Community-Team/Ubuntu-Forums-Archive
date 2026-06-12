---
title: "wireless works wired doesn't"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by badnaam on 2010-05-11
I tried posting this but haven't found a solution yet, so trying again.

                 Ethernet was working just fine, until the other day I yanked it out. The wireless works just fine on the same router. If I login to a windows 7 instance on this dual boot laptop then the ehternet works just fine. So it's not a hardware, cable or router issue. The card even gets an ip, but I can't connect to the internet. 
  Here are the details from route, iptables, ifconfig, ping etc.
  Any ideas? I have been struggling with this for day, none seems to have an answer.
  [http://pastie.org/954816](http://pastie.org/954816)

---

### Post by badnaam on 2010-05-11
an interesting observation..

I added the following line to my /etc/network/interfaces 

auto eth0
iface eth0 inet dhcp

and rebooted and it didn't change aa thing. So I took the lines off and reboot again and this time..the ethernet seemed to be functioning i.e. I cold get on the intenet, but the wireless didn't even get an IP for a bit, and then finally when the wireless got an ip, I could no longer connect to internet over ehternet until I disconnected the eth0 interface.

I also see the following message when I do a dmesg | grep eth0

[  190.430050] Unknown OutputIN= OUT=eth0 SRC=192.168.2.3 DST=74.125.19.18 LEN=79 TOS=0x00 PREC=0x00 TTL=64 ID=42270 DF PROTO=TCP SPT=42260 DPT=443 WINDOW=501 RES=0x00 ACK PSH FIN URGP=0 

What's really going on here? 

I love ubuntu so far, but in order for this to be a serious primary laptop OS, the basic stuff just need to work like Windows 7, so far I hae struggled with flash not playhing, no sound, no headphone sound, slow dvd burning etc etc..it does not fuel further encouragement to adopt Ubuntu and replace Windows.

This community has been a great help and I appreciate it.

---

### Post by badnaam on 2010-05-12
Anyone?

---

