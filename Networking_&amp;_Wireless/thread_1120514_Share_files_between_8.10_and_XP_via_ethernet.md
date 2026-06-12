---
title: "Share files between 8.10 and XP via ethernet"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by eliwis on 2009-04-09
Hi, I am trying to move some files from my xp machine to my Ubuntu 8.10 laptop. i am trying to use an ethernet cable to connect between them but for some reason nothing shows up under the Network menu in the file browser.
is there something I am doing wrong? because when I connect a Mac to the xp machine it seems to work.

any help is greatly appreciated.

thanks

---

### Post by superprash2003 on 2009-04-09
you could try accessing the shares this way . [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html) .. but are the two machines able to ping each other?

---

### Post by eliwis on 2009-04-09
> **superprash2003 said:**
> you could try accessing the shares this way . [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html) .. but are the two machines able to ping each other?

thanks for the reply.
the how-to in the link doesn't work. when I try to connect it i get an error message "Error: Failed to retrieve share list from server. Please select another viewer and try again". and when I try to ping to the windows machine I get this:

PING 169.254.38.31 (169.254.38.31) 56(84) bytes of data.
From 10.0.0.5 icmp_seq=2 Destination Host Unreachable
From 10.0.0.5 icmp_seq=3 Destination Host Unreachable
From 10.0.0.5 icmp_seq=4 Destination Host Unreachable
From 10.0.0.5 icmp_seq=6 Destination Host Unreachable
From 10.0.0.5 icmp_seq=7 Destination Host Unreachable
From 10.0.0.5 icmp_seq=8 Destination Host Unreachable
From 10.0.0.5 icmp_seq=10 Destination Host Unreachable
From 10.0.0.5 icmp_seq=11 Destination Host Unreachable
From 10.0.0.5 icmp_seq=12 Destination Host Unreachable
From 10.0.0.5 icmp_seq=14 Destination Host Unreachable
From 10.0.0.5 icmp_seq=15 Destination Host Unreachable
From 10.0.0.5 icmp_seq=16 Destination Host Unreachable
From 10.0.0.5 icmp_seq=18 Destination Host Unreachable
From 10.0.0.5 icmp_seq=19 Destination Host Unreachable
From 10.0.0.5 icmp_seq=20 Destination Host Unreachable
From 10.0.0.5 icmp_seq=22 Destination Host Unreachable
From 10.0.0.5 icmp_seq=23 Destination Host Unreachable
From 10.0.0.5 icmp_seq=24 Destination Host Unreachable
From 10.0.0.5 icmp_seq=26 Destination Host Unreachable
From 10.0.0.5 icmp_seq=27 Destination Host Unreachable
From 10.0.0.5 icmp_seq=28 Destination Host Unreachable
From 10.0.0.5 icmp_seq=30 Destination Host Unreachable
From 10.0.0.5 icmp_seq=31 Destination Host Unreachable
From 10.0.0.5 icmp_seq=32 Destination Host Unreachable
From 10.0.0.5 icmp_seq=34 Destination Host Unreachable
From 10.0.0.5 icmp_seq=35 Destination Host Unreachable
From 10.0.0.5 icmp_seq=36 Destination Host Unreachable
From 10.0.0.5 icmp_seq=38 Destination Host Unreachable
From 10.0.0.5 icmp_seq=39 Destination Host Unreachable
From 10.0.0.5 icmp_seq=40 Destination Host Unreachable
From 10.0.0.5 icmp_seq=42 Destination Host Unreachable
From 10.0.0.5 icmp_seq=43 Destination Host Unreachable
From 10.0.0.5 icmp_seq=44 Destination Host Unreachable
From 10.0.0.5 icmp_seq=46 Destination Host Unreachable
From 10.0.0.5 icmp_seq=47 Destination Host Unreachable
From 10.0.0.5 icmp_seq=48 Destination Host Unreachable
From 10.0.0.5 icmp_seq=50 Destination Host Unreachable
From 10.0.0.5 icmp_seq=51 Destination Host Unreachable
From 10.0.0.5 icmp_seq=52 Destination Host Unreachable
From 10.0.0.5 icmp_seq=54 Destination Host Unreachable
From 10.0.0.5 icmp_seq=55 Destination Host Unreachable
From 10.0.0.5 icmp_seq=56 Destination Host Unreachable
From 10.0.0.5 icmp_seq=58 Destination Host Unreachable
From 10.0.0.5 icmp_seq=59 Destination Host Unreachable
From 10.0.0.5 icmp_seq=60 Destination Host Unreachable
From 10.0.0.5 icmp_seq=62 Destination Host Unreachable
From 10.0.0.5 icmp_seq=63 Destination Host Unreachable
From 10.0.0.5 icmp_seq=64 Destination Host Unreachable
From 10.0.0.5 icmp_seq=66 Destination Host Unreachable
From 10.0.0.5 icmp_seq=67 Destination Host Unreachable
From 10.0.0.5 icmp_seq=68 Destination Host Unreachable
From 10.0.0.5 icmp_seq=70 Destination Host Unreachable
From 10.0.0.5 icmp_seq=71 Destination Host Unreachable
From 10.0.0.5 icmp_seq=72 Destination Host Unreachable
From 10.0.0.5 icmp_seq=74 Destination Host Unreachable
From 10.0.0.5 icmp_seq=75 Destination Host Unreachable
From 10.0.0.5 icmp_seq=76 Destination Host Unreachable
From 10.0.0.5 icmp_seq=78 Destination Host Unreachable
From 10.0.0.5 icmp_seq=79 Destination Host Unreachable
From 10.0.0.5 icmp_seq=80 Destination Host Unreachable
From 10.0.0.5 icmp_seq=82 Destination Host Unreachable
From 10.0.0.5 icmp_seq=83 Destination Host Unreachable
From 10.0.0.5 icmp_seq=84 Destination Host Unreachable
From 10.0.0.5 icmp_seq=87 Destination Host Unreachable
From 10.0.0.5 icmp_seq=88 Destination Host Unreachable
From 10.0.0.5 icmp_seq=90 Destination Host Unreachable
From 10.0.0.5 icmp_seq=91 Destination Host Unreachable
From 10.0.0.5 icmp_seq=93 Destination Host Unreachable
From 10.0.0.5 icmp_seq=94 Destination Host Unreachable
From 10.0.0.5 icmp_seq=95 Destination Host Unreachable
From 10.0.0.5 icmp_seq=97 Destination Host Unreachable
From 10.0.0.5 icmp_seq=98 Destination Host Unreachable
From 10.0.0.5 icmp_seq=99 Destination Host Unreachable
From 10.0.0.5 icmp_seq=101 Destination Host Unreachable
From 10.0.0.5 icmp_seq=102 Destination Host Unreachable
From 10.0.0.5 icmp_seq=103 Destination Host Unreachable
From 10.0.0.5 icmp_seq=105 Destination Host Unreachable
From 10.0.0.5 icmp_seq=106 Destination Host Unreachable
From 10.0.0.5 icmp_seq=107 Destination Host Unreachable
From 10.0.0.5 icmp_seq=109 Destination Host Unreachable
From 10.0.0.5 icmp_seq=110 Destination Host Unreachable
From 10.0.0.5 icmp_seq=111 Destination Host Unreachable
From 10.0.0.5 icmp_seq=113 Destination Host Unreachable
From 10.0.0.5 icmp_seq=114 Destination Host Unreachable
From 10.0.0.5 icmp_seq=115 Destination Host Unreachable
From 10.0.0.5 icmp_seq=117 Destination Host Unreachable
From 10.0.0.5 icmp_seq=118 Destination Host Unreachable
From 10.0.0.5 icmp_seq=119 Destination Host Unreachable
From 10.0.0.5 icmp_seq=121 Destination Host Unreachable
From 10.0.0.5 icmp_seq=122 Destination Host Unreachable
From 10.0.0.5 icmp_seq=123 Destination Host Unreachable
From 10.0.0.5 icmp_seq=125 Destination Host Unreachable
From 10.0.0.5 icmp_seq=126 Destination Host Unreachable
From 10.0.0.5 icmp_seq=127 Destination Host Unreachable
From 10.0.0.5 icmp_seq=129 Destination Host Unreachable
From 10.0.0.5 icmp_seq=130 Destination Host Unreachable
From 10.0.0.5 icmp_seq=131 Destination Host Unreachable
From 10.0.0.5 icmp_seq=133 Destination Host Unreachable
From 10.0.0.5 icmp_seq=134 Destination Host Unreachable
From 10.0.0.5 icmp_seq=135 Destination Host Unreachable
From 10.0.0.5 icmp_seq=137 Destination Host Unreachable
From 10.0.0.5 icmp_seq=138 Destination Host Unreachable
From 10.0.0.5 icmp_seq=139 Destination Host Unreachable
From 10.0.0.5 icmp_seq=141 Destination Host Unreachable
From 10.0.0.5 icmp_seq=142 Destination Host Unreachable
From 10.0.0.5 icmp_seq=143 Destination Host Unreachable
From 10.0.0.5 icmp_seq=145 Destination Host Unreachable
From 10.0.0.5 icmp_seq=146 Destination Host Unreachable
From 10.0.0.5 icmp_seq=147 Destination Host Unreachable
From 10.0.0.5 icmp_seq=149 Destination Host Unreachable
From 10.0.0.5 icmp_seq=150 Destination Host Unreachable
From 10.0.0.5 icmp_seq=151 Destination Host Unreachable
From 10.0.0.5 icmp_seq=153 Destination Host Unreachable
From 10.0.0.5 icmp_seq=154 Destination Host Unreachable
From 10.0.0.5 icmp_seq=155 Destination Host Unreachable
From 10.0.0.5 icmp_seq=157 Destination Host Unreachable
From 10.0.0.5 icmp_seq=158 Destination Host Unreachable
From 10.0.0.5 icmp_seq=159 Destination Host Unreachable
From 10.0.0.5 icmp_seq=161 Destination Host Unreachable
From 10.0.0.5 icmp_seq=162 Destination Host Unreachable
From 10.0.0.5 icmp_seq=163 Destination Host Unreachable
From 10.0.0.5 icmp_seq=165 Destination Host Unreachable
From 10.0.0.5 icmp_seq=166 Destination Host Unreachable
From 10.0.0.5 icmp_seq=167 Destination Host Unreachable
From 10.0.0.5 icmp_seq=169 Destination Host Unreachable
From 10.0.0.5 icmp_seq=170 Destination Host Unreachable
From 10.0.0.5 icmp_seq=171 Destination Host Unreachable
From 10.0.0.5 icmp_seq=173 Destination Host Unreachable
From 10.0.0.5 icmp_seq=174 Destination Host Unreachable
From 10.0.0.5 icmp_seq=175 Destination Host Unreachable
From 10.0.0.5 icmp_seq=177 Destination Host Unreachable
From 10.0.0.5 icmp_seq=178 Destination Host Unreachable
From 10.0.0.5 icmp_seq=179 Destination Host Unreachable
From 10.0.0.5 icmp_seq=181 Destination Host Unreachable
From 10.0.0.5 icmp_seq=182 Destination Host Unreachable
From 10.0.0.5 icmp_seq=183 Destination Host Unreachable
From 10.0.0.5 icmp_seq=185 Destination Host Unreachable
From 10.0.0.5 icmp_seq=186 Destination Host Unreachable
From 10.0.0.5 icmp_seq=187 Destination Host Unreachable
From 10.0.0.5 icmp_seq=189 Destination Host Unreachable
From 10.0.0.5 icmp_seq=190 Destination Host Unreachable
From 10.0.0.5 icmp_seq=191 Destination Host Unreachable
From 10.0.0.5 icmp_seq=193 Destination Host Unreachable
From 10.0.0.5 icmp_seq=194 Destination Host Unreachable
From 10.0.0.5 icmp_seq=195 Destination Host Unreachable
From 10.0.0.5 icmp_seq=196 Destination Host Unreachable
From 10.0.0.5 icmp_seq=197 Destination Host Unreachable
From 10.0.0.5 icmp_seq=198 Destination Host Unreachable
^C
--- 169.254.38.31 ping statistics ---
200 packets transmitted, 0 received, +148 errors, 100% packet loss, time 199203ms
, pipe 3


I guess this says that it fails to ping :)

---

### Post by Iowan on 2009-04-09
Looks like there may be an addressing problem - 169.254.X.X is avahi (zero-conf). I generally don't have much luck pinging outside my subnet (maybe if my gateway is playing nice). Are the aforementioned machines all supposed to be in same (10.0.0.X) subnet?

---

### Post by The_Original_Modifier on 2009-04-09
Is this via a router? Or just straight computer to computer? And if straight computer to computer would a crossover cable work?


Mod

---

### Post by eliwis on 2009-04-10
The connection is computer to computer via an ethernet cable. no routers.
I will try to change the cable. but i think it probably wont help, because I have osx leopard dual booting on the ubuntu machine  (for testing only:)) and when i boot into Leopard and connect it to the windows machine it shows up flawlessly and i can transfer files without any problem.

---

### Post by superprash2003 on 2009-04-10
you would have to setup static ip.. check under system->preferences->network configuration->WIRED

---

### Post by eliwis on 2009-04-10
> **superprash2003 said:**
> you would have to setup static ip.. check under system->preferences->network configuration->WIRED

I'm sorry, I don't see any option there for a static IP.
I am new to this, excuse me:tongue:

---

### Post by superprash2003 on 2009-04-11
try this [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

