---
title: "Setting up shorewall rules for network printer."
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by okos on 2011-08-14
Hello,
I setup shorewall firewall which works great.
I set it up on my Ubuntu box. Shorewall is only setup for one computer.
However, I cannot figure out how to set the rules to allow accesses to my wired network printer. The printer only works when shorewall is stopped.

Using wireshark shows the following info when printing with shorewall stopped and iptables cleared.My computer is 192.168.0.194 and the printer is 192.168.0.190> 
23591	899.331257	192.168.0.194	192.168.0.190	TCP	56191 > hp-pdl-datastr [PSH, ACK] Seq=10137 Ack=1 Win=5888 Len=742 TSV=633350 TSER=3134790955

23592	899.331894	192.168.0.190	192.168.0.194	TCP	hp-pdl-datastr > 56191 [ACK] Seq=1 Ack=10879 Win=16634 Len=0 TSV=3134790955 TSER=633350


Here are a few of the things I tried setting up the shorewall rules:
> 
ACCEPT    net       fw             tcp          22,imap2,imaps,9100,56191
ACCEPT	fw	net		tcp		9100,56191

# CUPS
#
ACCEPT		net		$FW		tcp	631
#ACCEPT		net		$FW		tcp	ssl_port
ACCEPT		net		$FW		udp	631
#

Any suggestions would be much appreciated.

---

### Post by okos on 2011-08-16
Does anyone have any suggestions?

---

### Post by okos on 2011-08-18
Bump

---

