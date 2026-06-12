---
title: "ra0 and X11 arguing with each other?"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by kg6gfq on 2006-01-15
Ok, I've been working for the past two years to find some way of getting Linux to let me use one of my Linksys wireless cards without paying for something like driverwrapper that I can't even install on my amd64 system.  At first it was Fedora vs. the WUSB11, based on a prism chipset (I believe).  Now Ubuntu is getting very close to recognizing an RT2500 based WMP54G.  I've managed to, from the shell, run ifdown eth0 (eth0 = my wired nic) and ifup ra0 (ra0 = the wireless).  This is without X running.  I then proceed to start up gdm, which promptly (well, within 5 minutes) freezes and makes me do a hard reboot.  This evening I finally managed to keep them both up for a few moments, and discovered that something was trying to send packets from 192.168.1.101, the IP of the wired nic.  I'm not sure about this, but that's what I got from the following output:  

[ 445.062192] Unknown Output IN= OUT=ra0 SRC=192.168.1.101 DST=216.155.193.164 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=16305 DF PROTO=TCP SPT=57237 DPT=5050 WINDOW=7007 RES=0x00 ACK PSH URGP=0

About half of that is nonsense to me, but I'm guessing it's a summary of an IP packet that was trying to be sent from the address of the wired nic through the wireless card.  It is apparently an ACK packet, so I figure there must have been a SYN somewhere from what little I know.  This was merely the last in a long line of similar messages which cut off immediately when I brought down ra0 again.  

So, is X11 trying to send this, maybe?  I did a bit of work trying to figure out what was at 216.155.193.164 to no avail.  Does anybody know what this could be or why it was happening?  

AdvaThanksance!!!!

---

