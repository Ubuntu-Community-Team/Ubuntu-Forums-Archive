---
title: "PXE-E32: TFTP open timeout"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Ashdev on 2010-09-16
Hi,

I've been trying to set up a netboot server using dhcp3-server, TFTP-HPA and xinetd.
However, I get an error when I boot with my client and I don't figure out why it doesn't work.

Here is the following error I get when I boot:
[B]
PXE-E32: TFTP open timeout[/B]

It seems that my TFTP server does not reply but I don't understand what's wrong.

I hope someone could help me solve that annoying issue, :D

Regards,
Ashdev

---

### Post by UnhappyGhost on 2012-09-23
It was working fine for me till Edubuntu 12.04 but as i upgrade it to Edubuntu 12.04.1 the same error started with me now!!! 
Have googled it, post the query in many problem and found these tips
1. TFTP Server many not be running.
2. TFTP configuration may have a problem.
3. If TFTP server is running then firewall is blocking the access to it
4. IP TABLES may be causing the problem

but i have checked all of the above and the problem still persists. 

Am locally able to access and connect to TFTP server on the Server and GET the file, but when i connect it from outside, the TFTP server doesnt respond. 
I have checked it many times, TFTP daemonn is also running properly!!

Please team, help us out!!

---

### Post by UnhappyGhost on 2012-09-23
> **Ashdev said:**
> Hi,

I've been trying to set up a netboot server using dhcp3-server, TFTP-HPA and xinetd.
However, I get an error when I boot with my client and I don't figure out why it doesn't work.

Here is the following error I get when I boot:
[B]
PXE-E32: TFTP open timeout[/B]

It seems that my TFTP server does not reply but I don't understand what's wrong.

I hope someone could help me solve that annoying issue, :D

Regards,
Ashdev
I just found a solution to this problem. 
Its the ufw firewall thats blocking all the incoming connections.

try to execute the following commands 
unhappyghost@tnl:/$ sudo ufw enable     [this will enable the ufw firewall]
unhappyghost@tnl:/$ sudo ufw default allow  [this will allow all the incoming connections to the server]

At this point the TFTP should start responding!!

But its a bad idea to leave the firewall open for all the incoming connections to every port. So, the best way to implement it is

unhappyghost@tnl:/$ sudo ufw enable
unhappyghost@tnl:/$ sudo ufw default deny
unhappyghost@tnl:/$ sudo ufw allow 69/udp

That will let you permit incoming connections on the  server to port 69 (TFTP) and your config must work!!!

---

### Post by UnhappyGhost on 2012-09-24
There is another thing that i have noticed. 
When i installed Edubuntu with all the complete packages on the DVD then i have problem with the TFTP Server.

This time i freshly installed Edubuntu 12.04.1 again and i just made sure to uncheck all the educational packs included in Edubuntu and everything seems to be working great now. 

Am not really sure which package was hindering the smooth functionality of xine TFTP server, but it works great as of now!!!

Will keep you informed as soon as i find anything new!!

---

### Post by kimalasi on 2013-03-03
> **UnhappyGhost said:**
> I just found a solution to this problem. 
Its the ufw firewall thats blocking all the incoming connections.

try to execute the following commands 
unhappyghost@tnl:/$ sudo ufw enable     [this will enable the ufw firewall]
unhappyghost@tnl:/$ sudo ufw default allow  [this will allow all the incoming connections to the server]

At this point the TFTP should start responding!!

But its a bad idea to leave the firewall open for all the incoming connections to every port. So, the best way to implement it is

unhappyghost@tnl:/$ sudo ufw enable
unhappyghost@tnl:/$ sudo ufw default deny
unhappyghost@tnl:/$ sudo ufw allow 69/udp

That will let you permit incoming connections on the  server to port 69 (TFTP) and your config must work!!!

I implemented the firewall this way and is working like charm with my gns3 cisco virtualizations: I have a phisical linux dns server with the tftp where I have all my cisco routers config backup including the os. I used atftpd for this is very charm and easy to use:
the config file is this one THE FILE RESIDES IN: /etc/defalut/atftpd
======================================================
USE_INETD=false #when the program is installed this was change from true to false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /srv/tftp"
======================================================
If you see the port that is open is the 1758. And because I have my ufw by default deny. I just opened this entries:

ufw allow 1758
ufw allow 1758/udp

Now all my Cisco Labs have access to the Server and I can backup all my labs. I implement this in the company I am working on we have about 2 Cisco Catalyst 2811 Routers, 5 Cisco
Catalyst 2950, 1 Cisco Catalyst 3550, and 8 Cisco Catalyst 3560 POE.

Hope this can solve your problems with tftpd.

---

