---
title: "ping &amp; communication issues between ubuntu and winxp"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by lanchong on 2009-07-22
I've got the following computers and networking setup at home(a pretty simple structrue)

1, router 192.168.0.1 (as usual it provides DHCP service), it's for all computers at home to access internet
2, ubuntu 9.0.4,latest patches installed via Update Manager. on wireless, got dynamic IP from DHCP 192.168.0.4 255.255.255.0, internet access is working. No firewall enabled(eg, firestarter etc),with samba on.
3, winxp SP2 pc1, on wireless,got dynamic IP from DHCP 192.168.0.5 255.255.255.0, internet access is working. no firewall enabled.
4, winxp SP2 pc2, on wireless,got dynamic IP from DHCP 192.168.0.6 255.255.255.0, internet access is working. no firewall enabled.

now, 3 computers in the LAN, same subnet:
-ubuntu
-win xp pc1
-win xp pc2

the symptoms are,
-can ping from ubuntu to pc1, but the 1st response is very slow, 
  from ubuntu issue ping command:laptop-ubuntu:~$ ping 192.168.0.5
                                 PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
                                 64 bytes from 192.168.0.5: icmp_seq=5 ttl=128 time=968 ms  #notice the 1st response took nearly 1sec.
                                 64 bytes from 192.168.0.5: icmp_seq=6 ttl=128 time=1.05 ms
                                 64 bytes from 192.168.0.5: icmp_seq=7 ttl=128 time=2.85 ms
                                 64 bytes from 192.168.0.5: icmp_seq=8 ttl=128 time=3.07 ms
-cannot initiate the ping from pc1 to ubuntu, but after initiated ping from ubuntu to pc1,  
  can ping through from pc1 to ubuntu, however, after communication remains idle for a while 
  the ping failed from pc1 to ubuntu again. And once the communication established, I tried to copy 
  files -- at pc1 copying a large file to a share in ubuntu(via samba), it worked for a few mins(5mins maybe?),   then drops out, due to "network is not accessable". seems there is a kind of time-out,  
  and communication has to be initiated from ubuntu.
-pc1 & pc2 can ping each others perfectly, the file sharing between them are perfect as they are all windows.
-cannot ping each other at all between ubuntu and pc2,thought might just ping blocked, tried to use ssh or samba to capture shares,all failed
  from ubuntu issue ping command:PING 192.168.0.6 (192.168.0.6) 56(84) bytes of data.
                                 From 192.168.0.4 icmp_seq=1 Destination Host Unreachable
  from pc2 issue ping command: Request timed out


btw,ping are performed using IP addresses here. so no name resolution needed.

so far what i've read over the internet all point to probable firewall or security/antivirus  
softwares. I stopped firestarter for sure in ubuntu. what I can see pc1&2 windoze firewall is 
disabled. however, the PCs are retired corporate computers, subject to a lot global policies 
or all sorts of security things before I presume. I didn't bother re-install, just disabled all anti-v  
services, ensured firewall is not on. 
 
Can anyone shed a bit light where I should start troubleshooting, ps, I don't really want to 
do re-install thing on the XPs.  
Thanks

---

### Post by Iowan on 2009-07-23
The corporate computer I use has some security (and updating) software besides just antivirus, making the machine almost unusable for 20-30 minutes after it's first booted.

---

### Post by lanchong on 2009-08-01
Got it fixed!:)

It's not any issue of Ubuntu. It is my Cisco Linksys router. There is one setting of it. Goto "Security" tab, then under tab "Firewall", untick "Block Anonymous Internet Requests ". 

lanchong

---

