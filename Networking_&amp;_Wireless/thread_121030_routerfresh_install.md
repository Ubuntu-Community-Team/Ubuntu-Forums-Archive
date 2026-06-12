---
title: "router/fresh install"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by xstation on 2006-01-24
I need some help first with my router which set up at the moment via
DHCP.

in the last few days have a static ip address which has reverse
dns ie ip address resolves to domain name and domain name resoves to ip address.

IF i go to my domin for examlpe [http://abc.net](http://abc.net) then on this page I see
the log in page for my router (when I first installed my router the log in page was [http://192.168.1.1](http://192.168.1.1)

My question is do I need to reset my router and since I am about to install
A FRESH install of bb 5-10 from cd rom what you I place in the network /
connection page.

I only have one computr at the moment which is dual boot.

xstation:eek:

---

### Post by mips on 2006-01-24
I don't quite follow your explanation, probably just me.

What you can however do is try the ubuntu install and when it gets to the networking section it will say could not obtain IP via dhcp or something like that, you will then have the option to configure the IP Adress, Gateway, Netmask & DNS manually.

Alternatively set your router up for DHCP and once your installation is completed you can revert back to your original settings.

---

### Post by xstation on 2006-01-25
did fresh install detected DHCP no problem biut cannot connect to internet.


connection
Internet protocol (IPv4)
address 192.168.1.2
broadcast 192.168.1.255
subnet 255.255.255.0

any suggestions

xstation:eek:

---

### Post by xstation on 2006-01-25
even stranger no google at firefox browser BUT in terminal apt-get update
worked ok?

what do I not understand.

xstation:o :o

---

### Post by mips on 2006-01-25
Disable IPv6 and see what happens.

---

### Post by xstation on 2006-01-25
what is the comand to disableIPv6 please   

;) xstation

---

### Post by mips on 2006-01-25
You really should try the search function, it works really well.
Also the very first post in this forum is a sticky dealing with troubleshooting covering most common things including IPv6.
Sticky Thread  Sticky: Wired Ethernet Troubleshooting Process;  [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

or alternatively

In the firefox address/URL space type "about:config" , scroll down to **network.dns.disableIPV6 = false** ,double click this line to change it to **true**.
In the above do NOT type in any quotes.
 
 The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:
 
 Open a terminal and enter:
 **sudo gedit /etc/modprobe.d/aliases**
 
 Look for the line that reads:
 **alias net-pf-10 ipv6**
 
 Change it to:
 **alias net-pf-10 off #ipv6**
 
 Save and reboot your PC.

---

### Post by xstation on 2006-01-26
many thanks for your post.

The about:config in Firefox worked fine

xstation:) :)

---

