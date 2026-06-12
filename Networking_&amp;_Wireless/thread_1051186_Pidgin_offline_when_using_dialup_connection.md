---
title: "Pidgin offline when using dialup connection"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by mtapman on 2009-01-26
I'm looking for some insight into a problem I have with Pidgin (or Empathy) not connecting when I'm using a diakup connection (Blackberry over Verizon Wireless, "sudo pon barry-verizon").

Browsing from a browser works fine. OpenVPN tunnel works well. Ping works...basically everything is fine except Pidgin/Empathy IM connections.

I believe the problem is caused by the integration of Pidgin/Empathy into Gnome because Network Manager shows no active connections when this situation occurs (i.e., it doesn't register the dialup connection as active). So my thought is that Pidgin/Empathy has a logic check that says "Connected to the Internet?" and that Gnome's Network Manager is responding with a "No". Pidgin/Empathy then stop trying to connect, never even attempting to verify connectivity themselves.

**Background info below:**
2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

 network-manager                           0.7~~svn20081018t105859-0ubuntu1.8.10.1

 network-manager-gnome                     0.7~~svn20081020t000444-0ubuntu1.8.10.1

**Routing table (some info replaced with Xs):**
XXXXX:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
X.8.1.9        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
X.174.112.192  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
X.16.65.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
X.8.1.0        X.8.1.9        255.255.255.0   UG    0      0        0 tun0
X.16.170.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

**barry-verizon script:**
#
# This file contains options for Verizon Blackberries
#
# It is based on a file reported to work, but edited for Barry.
#

connect "/usr/sbin/chat -f /etc/chatscripts/barry-verizon.chat"

noauth
user ""
password ""

defaultroute
usepeerdns

noipdefault
nodetach
novj
#nodeflate
#nobsdcomp
#noaccomp
#default-asyncmap
nocrtscts
#nopcomp
#nomagic

#passive

nomultilink
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
# added so not to disconnect after a few minutes
lcp-echo-interval 0
lcp-echo-failure 999

mtu 1492

debug
#debug debug debug

pty "/usr/sbin/pppob"

#115200
#modem

---

### Post by outer_space on 2009-05-09
Me too. Pidgin worked before I 'upgraded' to jaunty, and now it thinks it is offline whenever I use dialup.  

What a crappy thing to do making everything rely on nm-applet which does not work with dialup when everything worked fine before.

---

### Post by khc on 2009-05-09
If you turn off NetworkManager, then pidgin will not check with it before signing on

---

### Post by Larry64 on 2009-07-20
Turning off NM is not convenient as I use the laptop at wifi points most of the time but also via bluetooth modem.

Disabling and re-enabling the account in Pidgin is the work arround but it is very annoying.

Firefox which also annoyingly starts in off-line mode when no NM link has an option to disable the checking.  Is there one tucked away somewhere for Pidgin?

---

### Post by immux on 2010-09-04
i run pidgin with -f parameter.
now everything is OK :D

#pidgin -f

---

### Post by aliirani on 2010-09-19
> **immux said:**
> i run pidgin with -f parameter.
now everything is OK :D

#pidgin -f
 
Tanx this is work for me.:)

But I most run terminal and type pidgin -f always???
This is snail!:mad::mad::mad::mad:

Here isn't any way???:confused::confused:

---

