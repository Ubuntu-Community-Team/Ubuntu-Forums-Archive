---
title: "Configure Linux VPN Server for a Windows VPN Client"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by xbaez on 2006-04-24
I use Linux at the office, and my boss wants to have a VPN access, using Windows, from his home.

He wants to be able to access the network as if he would be here physically. He wants to access the samba shares, he wants to be able to print on a Samsung printer (works with linux) and so on.

I'll appreciate if somebody can tell me links to a relatively new HowTo (iptables) that explains me how to do this

I believe that the instructions provided here should be able to work for any distro

---

### Post by wvelez on 2006-04-24
Hi,

I´ve had great success with the same set up you´re trying to do.  You´ll need: pptpd - PoPToP Point to Point Tunneling Server
Then look at opening port 1723/tcp for accepting connections...this should get you started...

Good luck and best regards,
-will

---

### Post by xbaez on 2006-04-24
Ok, thanks for the info
Any HowTO that you know though?

---

### Post by xbaez on 2006-04-25
One question
the documentation of this package seems a little bit old, and I don't have much clues in how to configure these files.

I'm editing the following file:
**/etc/ppp/options.ppp0**
debug
**name servername**
auth
require-chap
proxyarp

I'm also editing the file **/etc/ppp/chap-secrets**
# INBOUND CONNECTIONS
#client         hostname        <password>      192.168.1.1
username    **servername**     xxx                     *

Could you please tell me, what is servername (in both files, chap-secrets and options.ppp0). Is it the servername of this machine (server) or the servername of the client?

Could you please tell me an URL were I can get beter documentation for this program?

I appreciate your support

---

### Post by mips on 2006-04-25
[http://openvpn.net/](http://openvpn.net/)
[http://openvpn.net/howto.html](http://openvpn.net/howto.html)
[http://sourceforge.net/projects/openvpn/](http://sourceforge.net/projects/openvpn/)


[http://www.ubuntuforums.org/showthread.php?t=55189](http://www.ubuntuforums.org/showthread.php?t=55189)
[http://www.ubuntuforums.org/showthread.php?t=41968](http://www.ubuntuforums.org/showthread.php?t=41968)
[http://www.ubuntuforums.org/showthread.php?t=64547](http://www.ubuntuforums.org/showthread.php?t=64547)
[http://www.ubuntuforums.org/showthread.php?t=40838](http://www.ubuntuforums.org/showthread.php?t=40838)
[http://www.ubuntuforums.org/showthread.php?t=109275](http://www.ubuntuforums.org/showthread.php?t=109275)
[http://www.ubuntuforums.org/showthread.php?t=163928](http://www.ubuntuforums.org/showthread.php?t=163928)
[http://www.linuxtoday.com/news_story.php3?ltsn=2006-04-02-007-26-OS-HL-NT](http://www.linuxtoday.com/news_story.php3?ltsn=2006-04-02-007-26-OS-HL-NT)
[http://kerneltrap.org/node/5018](http://kerneltrap.org/node/5018)

Personally I would used a more security hardened OS/Distro than Ubuntu.

---

### Post by jpkelly100 on 2008-02-12
Poptop how to
a good start is [http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/) this with some other searching got my vpn server up and running.

Install poptop

sudo apt-get update
sudo apt-get install pptpd

Type  ifconfig and inspect the "eth0" section to find out the IP address of your server [inet addr]
edit pptpd.conf
I use nano at the terminal, you may use any text editor

sudo nano /etc/pptpd.conf
 
change lines
localip 10.5.1.3  (this address should be the IP address of your server [inet addr] when you type ifconfig,
 see above )
remoteip   10.5.1.241-246 

Above allocation assigns 6 IP addresses for 6 roaming users/telecommuters to VPN into your corporate network 
simultaneously.

sudo nano /etc/ppp/options

find the line that says ms-dns, modify the IP addresses to suit your local environment.
These two IP addresses should be the IP addresses of the DNS servers provided to you by your ISP/cable/ADSL company.
Don't use other DNS servers as they may block queries that come from outside their network environment.
ms-dns  216.21.128.22 
ms-dns  216.21.129.22

sudo nano /etc/ppp/chap-secrets
    e.g.
alice pptpd a-strong-password  *
bob pptpd another-strong-password  *

The trailing * means these users are allowed to come in from any IP address, if the telecommuter or branch office has a static or fixed IP address and never roams, then you can replace the * with his/her fixed IP address (or IP address block) for increased security.

One more tweak is to instruct the Linux kernel to "forward" VPN packets

I tried with no results to change
sudo nano /etc/sysctrl.conf
find the line that says:
#net.ipv4.conf.default.forwarding=1
delete the #
save the file.
reboot
This was from the web address i gave earlier.

What worked for me was.

I made a shell file named "ipforward"
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1

Than made it executable
sudo chmod +x /etc/init.d/ipforward

Than updated rc.d

sudo update-rc.d FOO defaults

Restarted system and forwarding stuck!
This should allow you access onto your lan.

---

### Post by jpkelly100 on 2008-02-12
DOH!
on the update-rc.d
FOO should be ipforward

---

### Post by 1jackjack on 2008-03-16
Thanks for such a great quickstart guide! Found a typo in the section "One more tweak is to instruct the Linux kernel to "forward" VPN packets": there's no 'r' in /etc/sysctrl.conf. But thanks to you, i have setup a server on my ubuntu box at home, and connected to it using vista on my laptop from the university wireless! BUT...

(1) when i do connect, by the connection, it says "Access: local and internet", and if i open firefox and start browsing, i'm pretty sure it tries (SLOWLY) to use the internet of my home network...?!
EDIT: SOLVED (set the vpn connections ipv4 properties>advanced UNCHECK use default gateway)

(2)I can see all the computers on my MSHOME network at home, but can only access the files of my ubuntu server box. If i try to access any others (e.g. "PLILLSPC"), I get: "The network path was not found" and if i click diagnose: "PHILLSPC" is not a valid host name...

Thanks for any advice!
Jack

---

### Post by jpkelly100 on 2008-03-19
I noticed the routing my internet out thru home lan also when VPN'd,  but had not followed thru with finding out why. Thanks for the tip 1jackjack.

To allow network browsing, which i believe is Windows only you would have to set up a WINS server thru Samba. The other work around would be to just use the ip address.  \\ip address\the share. You can use this in  internet explorer or to map a drive. This is how i connect with shares on my home network.

And also i noticed when connecting out from our office which has a windows sbs running. That the more people on our network the more likely i will not be able to land the vpn to the house. But when i use my verizon wireless card it lands every time without fail. Not sure if the sbs is doing something or if it's just latency.
Sorry about the typo!

---

