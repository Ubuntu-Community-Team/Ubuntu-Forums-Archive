---
title: "Wireless connected but not working (HP pavilion)"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by uupreti on 2009-05-08
Hello all,
I must say I am kind of new to Ubuntu world. Yesterday I installed Ubuntu 9.04 dekstop ( 2.6.28-11-generic) to my laptop ( HP pavilion dv 6000) which has broadcom wireless card. Installation was smooth like butter. Everything was great and impressive. After finishing installtion, Wireless card detect my network automatically and ask for my WPA personal key and I entered. So far so good. But when I tried to browse internet, it made me sad. No internet.:(

when i do **iwlist scan**, it shows me everything it should. I can also see in **dmesg, lspci** and ip address is also getting from **DHCP**. But when I enter **ifconfig**, it gave me **eth0** (ethernet card ) and **eth1** ( wireless may be). I didn't see **wlan0** though.

But here comes interesting turn. I installed **vmware server 2.0.1** and installed **Windows XP** as a guest OS. I **bridged** wireless card to guest OS and I can browse from windows( guest OS under ubuntu) using wireless card. It means wireless card driver is already recognized by Ubuntu but why I am not able to browse from it??:(

Any suggestion from expert??

Thanks

---

### Post by superprash2003 on 2009-05-08
post output of ifconfig and iwconfig from the terminal

---

### Post by uupreti on 2009-05-09
Thanks for your reply.

You know what? I just changed **/etc/NetworkManager/nm-system-settings.conf** file to

[B][ifupdown]
managed=true[/B] ( I don't know why it was false before. any idea??I am using DHCP though. And amazing thing is I couldn't see any entry for eth0, eth1 in /etc/network/interfaces file. So where is the configuration for DHCP??)

and it starts working. But as you said when I do **iwconfig**, result looks like following.

[B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:195  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.[/B]     

I made it working but still I am confused what did I do??:P.

Thanks again.

---

