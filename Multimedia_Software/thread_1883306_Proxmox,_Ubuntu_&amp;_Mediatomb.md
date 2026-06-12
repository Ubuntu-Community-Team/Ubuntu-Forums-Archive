---
title: "Proxmox, Ubuntu &amp; Mediatomb"
date: 2011-11-18
forum: Multimedia Software
---

### Post by zaazz on 2011-11-18
I've been playing with Proxmox for the last week or so. I really like throwing up virtual servers and playing around with them. I've hit a wall here with this setup and Mediatomb. It doesn't seem to be broadcasting to my network.

I installed this version of ubuntu:
ubuntu-10.04-standard_10.04-4_i386.tar.gz

I statically gave the server 192.168.88.144. It has a working network connection. I can VNC into it and go out to any websites, etc. (these static servers don't show up in my DHCP tables but they still get online)

I was playing around with my firewall and put this in just because I wasn't sure.

chain=input action=accept protocol=igmp src-address=192.168.88.0/24 dst-address=192.168.88.0/24

Here's my ifconfig

root@Ubuntu:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3022 (3.0 KB)  TX bytes:3022 (3.0 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:808 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:87115 (87.1 KB)  TX bytes:142078 (142.0 KB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.88.144  P-t-P:192.168.88.144  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


When I run mediatomb I see this:


root@Ubuntu:~# mediatomb

MediaTomb UPnP Server version 0.12.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2011-11-19 06:29:09    INFO: Loading configuration from: /root/.mediatomb/config.xml
2011-11-19 06:29:09    INFO: Checking configuration...
2011-11-19 06:29:09    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2011-11-19 06:29:09    INFO: Setting metadata import charset to ANSI_X3.4-1968
2011-11-19 06:29:09    INFO: Setting playlist charset to ANSI_X3.4-1968
2011-11-19 06:29:09    INFO: Configuration check succeeded.
2011-11-19 06:29:09    INFO: Initialized port: 49153
2011-11-19 06:29:09    INFO: Server bound to: 127.0.0.2
2011-11-19 06:29:09    INFO: Adding HTTP header "X-User-Agent: redsonic"
2011-11-19 06:29:10    INFO: MediaTomb Web UI can be reached by following this link:
2011-11-19 06:29:10    INFO: [http://127.0.0.2:49153/](http://127.0.0.2:49153/)


Is it not broadcasting out to the network at all? It seems like it may be a problem with how mediatomb is configured by it's defaults but I can't find anything in the config files to suggest there's something I could edit to use a different IP send that traffic out on.

Even without running it manually I can get to the web-interface via: [http://192.168.88.144:49152/](http://192.168.88.144:49152/)

Still it doesn't show up on windows 7 media player or my PS3.

Any suggestions or help would be much appreciated.

---

### Post by zaazz on 2011-11-19
Still stuck here. :)

---

### Post by cbowman57 on 2011-11-19
Can't help you with those but when I wanted to connect a PS3 here the other night I ended up using Rygel.  

You may want to check it out, it's in the repositories.

---

### Post by zaazz on 2011-11-20
cbowman57,

I installed it but I still need to take a look. Thanks for the suggestion. I was looking over the server and this one wasn't a fully virtualized server, it was a container (openVM), and for some reason the networking is a bit different because of that. My VoIP server has normal eth0 and lo interfaces and its on the same box but that's fully virtualized so I'm trying another install of ubuntu server to see if i can get this working. I'm going to play around with Rygel as well tomorrow. Thanks!

---

