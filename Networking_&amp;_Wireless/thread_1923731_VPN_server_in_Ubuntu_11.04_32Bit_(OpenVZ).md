---
title: "VPN server in Ubuntu 11.04 32Bit (OpenVZ)"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by chrisnouser on 2012-02-11
Hi guys! I have a vps and i want to install a vpn service so i can  connect from both my linux and windows computers.. so what i did..after a  clean install:
-sudo apt-get update
-sudo apt-get install pptpd
-sudo vi /etc/pptpd.conf and i removed the # from local and remote ip. i  read that it doesnt matter what i will enter there because its my  server's job to assing new IPs.
-sudo vi /etc/ppp/chap-secrets and i added user1 pptpd pass1 *
-sudo /etc/init.d/pptpd restart

the output of netstat -an | grep LISTEN is:
> 
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:[COLOR=Blue]**_1723_**[/COLOR]            0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     279138631 @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     279142360 /var/run/sendmail/mta/smcontrol

my ifconfig is:
> 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:17112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10274276 (10.2 MB)  TX bytes:1979802 (1.9 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:mad:xx.xxx.xxx.xxx  P-t-P:mad:xx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


when i try to connect from my windows xp laptop i get an error  721...firstly it stays for long time in verifying username and password  and then it gives me that error...thanks

PS where xxx.xxx.xxx.xxx is the same ip..my external ip of my vps thanks
PS2 i put in blue color the port so you can see ithe service is running..
PS3 i heard something about forwarding and someonthing about  pptpproxy??is that my problem? or that i left local ip and remote ip in  the config file the defaults?(i just removed the 2 # infront of localip  and remoteip)thanks
PS4 i also tried localip my vps ip but still didnt work..

---

### Post by cmeacham98 on 2012-03-29
I have the exact same problem and setup to the dot. Please help me. Thanks + Bump! :p

---

### Post by temp3 on 2012-10-06
I've same problem on Ubuntu 10.04.
Followed: [http://www.64bit.co.uk/index.php/archives/223](http://www.64bit.co.uk/index.php/archives/223)
Any solution?

---

### Post by Lars Noodén on 2012-10-06
Not really a solution but you may want to reconsider trying to use PPTP and choose IPSec instead.  PPTP is not really known for security and recent events have shown that to be an unfixable condition:
[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

---

