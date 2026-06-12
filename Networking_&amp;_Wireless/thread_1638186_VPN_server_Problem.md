---
title: "VPN server Problem"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Illusion989 on 2010-12-05
Hi all,

I am trying to learn a bit about networking and hence I want to set up a VPN pptp server on my Ubuntu 10.04 desktop. My desktop is connected behind a D-Link router. I would be accessing my server from a windows 7 machine outside of my local area network or router. My windows machine is behind another router (not the same D-Link one)

I have tried various sites to configure my vpn and seek help but I cant seem to get it to work. I have also tried to analyse my syslog files to see the error. But, my server is not detecting any incoming connection from the client.

Let me explain the problem a bit more in detail.

According to ifconfig, I have got the following details:
inet addr:192.168.1.3  
Bcast:192.168.1.255  
Mask:255.255.255.0
Router ip address: 192.168.1.1


I first configured my pptpd.conf. In that file,  I configured my localip of the server and remote ip of the server:
ppp /usr/sbin/pppd
option /etc/ppp/pptpd-options
logwtmp
localip 192.168.1.3
remoteip 10.168.1.241-246 - randomly picked

In my chap secrets file, I also added a username and password, which the client would use.

Then, in "pptpd-options" file. The settings are as follows:
name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 208.67.222.222
ms-dns 208.67.220.220
nodefaultroute
lock
nobsdcomp 
auth
require-mppe

Moreover, I am using D-link router 2640 router. I have set up the port forwarding as well in the following manner:
Private ip: 192.168.1.3 - (local machine ip)
Protocol type: TCP
Public start port: 1723
Public end port: 1723
Connection: PVC0

Then, I went to my Microsoft windows 7 pc. And tried to connect my server using default vpn client:
I used the following settings:
ip address: 192.168.1.3
username: pptpd/username
password: *******

Following that, I get an error on windows machine, "Error 807: The connection between the server and the client has been interrupted". Noting appears in the log files on my linux machine. This suggests to me that there is something wrong on my server setup, maybe ip settings etc.

I would be eternally grateful, if you can help me out on this. I am planning to make a howto as soon as I get this up and running. Because, I could not find anything like that on the web. Apologies for the long email. Thank you for your considerations and hope to hear from you soon,


Best regards,
Musabbir

---

### Post by Jimmypooh on 2011-02-11
I am also having problems with this.  I do see one problem in your post above.  When connecting from outside your network you cannot use 192.168.1.3.  That is only the IP address inside your network.

---

### Post by Jimmypooh on 2011-02-11
These are the instructions I used, but couldn't get it working.  I'm new to Linux and Ubuntu but am eager to learn.  All the searches I've found have turned up problems  but no solutions.  Anyone have any help?
 
BTW: I have been able to set this up on my PC so I know my router is not the problem.  Since then I have redirected my router to port to the Linux box.
 
 
[[COLOR=#1c51a8]http://forums.bit-tech.net/showthread.php?t=132029[/COLOR]]("http://forums.bit-tech.net/showthread.php?t=132029")
 
**VPN Server on Ubuntu Tutorial** 
We use Ubuntu here on our internal development servers (apt-get love ) and this morning I needed to setup a VPN server so that I can access some tools that run here from home. I came across a bunch of hurdles and thought i'd document them here for anyone who needs to do the same.

This will allow MS clients and probably Apple too.

Firstly install pptpd

Code:
sudo apt-get install pptpd
Now edit pptpd's config (/etc/pptpd.conf). At the bottom you'll find settings for localip and remoteip. Here's what mine looks like:

Code:
localip 172.198.1.4remoteip 172.198.2.50-51
localip is the IP of an adapter in the server (yours might be 192.168.0.10 for example)
remoteip: the IPs that clients are allowed to use (i allowed mine to use 172.198.2.50 through 172.198.2.51)

Now we'll set up some users, so edit the chap-config config file(/etc/ppp/chap-secrets). I want to allow two users, so my chap-secrets file looks like this:

Code:
# client        server  secret                  IP addressesrich             pptpd   apassword                [[COLOR=#1c51a8]80.40.0.0/13[/COLOR]]("http://80.40.0.0/13")geoff             pptpd   apassword                [[COLOR=#1c51a8]212.219.0.0/14[/COLOR]]("http://212.219.0.0/14")
... which allows users rich and geoff, with the passwords 'apassword' to be accepted from those IP subnets. * can be used to allow all IPs. [[COLOR=#1c51a8]see pppd/chap-secrets man page for more info[/COLOR]]("http://www.die.net/doc/linux/man/man8/pppd.8.html")

You *may* be good to go at this point. Restart pptpd (sudo /etc/init.d/pptpd restart) and attempt to connect. If it doesn't work, check /var/log/messages for a notice that looks a bit like this:

Code:
Apr 10 09:49:42 beryllium pppd[9619]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.3, this is 2.4.4
If you see that, then we need to change pptpd-logwtmp's version number.

This info kindly lifted from [[COLOR=#1c51a8]CyberAngel[/COLOR]]("http://ubuntuforums.org/member.php?u=56029") at the Ubuntuforums.

We now need a few more things:

Code:
sudo apt-get install libwrap0-dev debhelpersudo apt-get source pptpdcd pptpd-1.3.0/pluginssudo vim patchlevel.h
Change:
Code:
#define VERSION         "2.4.3"
To:
Code:
#define VERSION         "2.4.4"
Save the file and now do:

Code:
cd ../..sudo apt-get -b source pptpdsudo dpkg -i pptpd_1.3.0-1ubuntu1_i386.debsudo dpkg -i bcrelay_1.3.0-1ubuntu1_i386.deb
Done! Now restart pptpd:

Code:
sudo /etc/init.d/pptpd restart
And you should be good to go!

All you need to do now is add a VPN network connection and connect with the username/password that you set up. Don't forget to hit the IPv4 TCP/IP settings on your client machines for the VPN connection and to untick "Use default gateway on remote network" if you need to (you probably will).

You will also need to change some security settings ([[COLOR=#1c51a8]image[/COLOR]]("http://staff.bit-tech.net/rich/vpnubuntu.jpg")):

VPN Connection > Properties > [Security Tab] -> Advanced

Allow these protocols: (tick) Microsoft CHAP Version2

---

