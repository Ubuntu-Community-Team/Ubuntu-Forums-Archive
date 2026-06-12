---
title: "Mobile Broadband - DNS trouble?"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by geokom on 2009-12-05
Hello!

I am running Ubuntu 9.10 on two different laptops, both show the same problem when connecting to the internet through mobile broadband with a Huawei 220 modem: the connection is established, but if I try to open a web page in firefox, it can not connect. However, the "Weather Report" panel application can update its content. Using wireshark to monitor the ppp interface, I can see the traffic for the wheater report, but no traffic at all coming from firefox - also no DNS packets. If I directly type an IP address into the firefox address line, I see outgoing but no incoming packets. The weirdest thing is that *sometimes* everything works fine! But most of the time the behaviour is as described.

I assume, something goes wrong with the DNS (nslookup does not work then) but I can not figure out what.

Can you help me?

Regards,

geokom

---

### Post by geokom on 2009-12-05
Ah, I forgot: one of the laptops has also Window XP installed - no problems there.

---

### Post by alexfish on 2009-12-05
Hi

 sounds like problem with network manager

*****from a fresh boot    otherwise the sys log is to long*****

   can you do this from the terminal and post the results 

  also did the device configure in the wizard ok



Code 

     lsusb
  

 and then 



    ls -al /dev/ttyU*

and then

tail -f /var/log/syslog

there are links on this site regarding this device  so may be able to point in right direction

---

### Post by svaens on 2010-01-13
Hi Everyone, and Alex (fish)

I am having the same problem. 
I was posting my troubleshooting results here:
[http://ubuntuforums.org/showthread.php?t=1379736](http://ubuntuforums.org/showthread.php?t=1379736)
Alex was helping out. 
It took me a while to realise that it was a problem in using the DNS. 

I wonder where to go now?

By the way, I found a bug listed now:

[https://bugs.launchpad.net/ubuntu/+source/mobile-broadband-provider-info/+bug/498110](https://bugs.launchpad.net/ubuntu/+source/mobile-broadband-provider-info/+bug/498110)

Its status is currently (thankfully) confirmed.

---

### Post by alexfish on 2010-01-14
hi 

had to do some reading re all these post like this above re: network manager

for the time been;

I am placing here a very useful link regarding the PPP

the link will take you to a specific page .. 

don't forget to read the previous pages

Because This Concerns the Network Manager

I think posting here about this subject would be welcome by All members
" what ever their means of connection happens to be " 

the ppp link

[http://tldp.org/HOWTO/PPP-HOWTO/c1337.html](http://tldp.org/HOWTO/PPP-HOWTO/c1337.html)

---

### Post by alexfish on 2010-01-14
**[SIZE=2]Linux: Setup as DNS Client / Name Server IP Address[/SIZE]**


Many new Linux user finds it difficult to setup / modify new name server address (NS1 / NS2). 
 Local name resolution is done via /etc/hosts file. If you have small network, use /etc/hosts file. DNS (domain name service is accountable for associating domain names with ip address, for example domain yahoo.com is easy to remember than IP address 202.66.66.12) provides better name resolution. To configure Linux as DNS client you need to edit or modify /etc/resolv.conf file. This file defines which name servers to use. You want to setup Linux to browse net or run network services like www or smtp; then you need to point out to correct ISP DNS servers:

 **/etc/resolv.conf file**

if using Ubuntu  ppp then try using the **/etc/ppp/resolv.conf file**

 In Linux and Unix like computer operating systems, the /etc/resolv.conf configuration file contains information that allows a computer connected to the Internet to convert alpha-numeric names into the numeric IP addresses that are required for access to external network resources on the Internet. The process of converting domain names to IP addresses is called "resolving."
 The resolv.conf file typically contains the IP addresses of nameservers (DNS name resolvers) that attempt to translate names into addresses for any node available on the network.

 **Setup DNS Name resolution**

 Steps to configure Linux as DNS client, first login as a root user (use sudo su command):

 **Step # 1: ** Open /etc/resolv.conf file:

 vi /etc/resolv.conf  [B]; or gedit

Step #2: [/B] Add your ISP nameserver as follows: Example

 search isp.com
nameserver 202.54.1.110
nameserver 202.54.1.112
nameserver 202.54.1.115 

Note Max. three nameserver can be used/defined at a time.

 **Step # 3:**Test setup nslookup or dig command:

d*ig  "name*"  IE: dig [COLOR=Navy][COLOR=Black] custard.bris.ac.uk[/COLOR][/COLOR]  ;  dig myAPN

nslookup "name"

...................................................................................................

---

### Post by alexfish on 2010-01-14
Hi

If you have followed the above the                            inevitable  seems to happen again "nothing in the/etc/resolv.conf " 

this what I Have done 

1. installed Ubuntu Tweak for here

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)





2. From the Menus in Ubuntu Tweak There is a Package cleaner. came up with this, screen shot below

look up on the web here 

[http://live.gnome.org/PolicyKit](http://live.gnome.org/PolicyKit)

**PolicyKit** is a framework for defining policy for system-wide components and for desktop pieces to configure it. It is currently used by several components of the GNOME desktop, among which GConf, [NetworkManager]("http://live.gnome.org/NetworkManager"), the gnome-system-tools. GNOME does not depend on [PolicyKit1]("http://live.gnome.org/PolicyKit1") itself, but on polkit-gtk-1. Please note that version 1 is not compatible with its predecessors (versions below 0.92). 

Yep, I cleaned up the System step by step from the menus in Ubuntu Tweak

From the Menu Package Cleaner Here are the options

Clean Package

Clean Cache

Clean Config

Clean Kernel

Can't say if it is a solution , but I have done a fresh install of Ubuntu 9.10  and have used this after every upgrade or update and have had good success with the network manager (the fresh install was a while back)

---

### Post by pdc on 2010-01-14
thanks Alex; a bit of homework for us all 

we appreciate all your very diligent research; great work

---

### Post by alexfish on 2010-01-15
> **pdc said:**
> thanks Alex; a bit of homework for us all 

we appreciate all your very diligent research; great work

and more Sorry

[http://live.gnome.org/NetworkManager/MobileBroadband](http://live.gnome.org/NetworkManager/MobileBroadband)

[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

[http://live.gnome.org/NetworkManager/Debugging](http://live.gnome.org/NetworkManager/Debugging)

---

### Post by piq on 2010-01-18
Does anyone know if the problem still exists with ubuntu 10.04?

---

### Post by alexfish on 2010-01-26
hi all

been doing a post : re icon 515

Installing " resolvconf " seems to have help with the Network Manager DNS problems

May be worth a try

---

### Post by elangos on 2010-02-14
Hi,

This does not work for me. I have added 3 nameservers with respective IPs in resolve.conf. My system works in 2 different network (office & home). When at home, I want the system to use my office DNS for all official sites and ISP DNS for the rest of the sites. But somehow I am not able to make this work. 

I also checked this forum which pretty talks about my exact problem
[http://ubuntuforums.org/showthread.php?t=645879](http://ubuntuforums.org/showthread.php?t=645879)
As mentioned here, I also suspect that if the server returns NOT FOUND, the next server will not be queried, it will only do so if it times out. 

Is this true? Is there anyway possible to get this work as per my requirement? Also, please let me know if I should be looking any other places.

---

### Post by alexfish on 2010-02-15
> **elangos said:**
> Hi,

This does not work for me. I have added 3 nameservers with respective IPs in resolve.conf. My system works in 2 different network (office & home). When at home, I want the system to use my office DNS for all official sites and ISP DNS for the rest of the sites. But somehow I am not able to make this work. 

I also checked this forum which pretty talks about my exact problem
[http://ubuntuforums.org/showthread.php?t=645879](http://ubuntuforums.org/showthread.php?t=645879)
As mentioned here, I also suspect that if the server returns NOT FOUND, the next server will not be queried, it will only do so if it times out. 

Is this true? Is there anyway possible to get this work as per my requirement? Also, please let me know if I should be looking any other places.
                                  

 On the Ubuntu system there should be two files &#8220;serviceproviders.2.dtd&#8221; and &#8220;serviceproviders.xml&#8221;


The &#8220;serviceproviders.xml&#8221; is the actual database used by the NM
 

  The numerical addresses {NS1 NS2} for your service provider can be found in this file, if it is not listed ask your service provider
 

  This info can be used by setting the Ipv4 to Automatic (PPP) address only in Network Manager  
 

    in my case I have used the secondary address ( it always connects to this one ? ) it works every time , but you could enter both. This rule can be applied to nearly all settings in the Network Manager.
 

 use the resolvconf as a last resort , as this will impact on other parts of the system
 

  you can update &#8220;serviceproviders.xml&#8221;  to suit your requirements : see post # 21
 

 [http://ubuntuforums.org/showthread.php?t=1331660](http://ubuntuforums.org/showthread.php?t=1331660)

If you are Using Beta Versions or Development Versions of Ubuntu Consider Using NM Daily { Use at your Own Risk } , not advisable if you use LTS

details
  	 	 	 	 	 	  
[LIST]
[*][SIZE=2]NM daily Trunk PPA { 	Please read in detail }: 
[/SIZE]
[/LIST]
 
[LIST]
[*][SIZE=2]http://www.asoftsite.org/s9y/[/SIZE]
[/LIST]

---

