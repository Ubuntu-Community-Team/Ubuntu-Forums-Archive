---
title: "*-network DISABLED"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by jpaytoncfd on 2009-05-17
Im using an acer laptop and trying to get the onboard ethernet to work.

lshw shows "*-network:0 disabled" which is the wlan0 and I tried sudo ifup eth0 and it responded "ignoring unknown interface eth0-eth0". the lshw does show the ethernet hardware, its a SIS900 PCI fast Ethernet.

I'm using kubuntu 9.04 and its a fresh install not an update.

Thanks in advance,
~Joe

---

### Post by jpaytoncfd on 2009-05-18
ok ive gotten somewhere, The adapter is enabled and when i try to run (sudo /etc/init.d/networking restart) it does a bunch of stuff then trys to connect to the DHCP and I get this (DHCPDISCOVER oe eth0 to 255.255.255.255 port 67 interval x) 6 times with a different interval everytime. then no DHCPOFFERS recieved. My subnet mask is 255.255.255.0 and I cant change it to 255.255.255.255

---

### Post by superprash2003 on 2009-05-18
try setting up static ip

---

### Post by s1500 on 2009-05-18
> **jpaytoncfd said:**
> ok ive gotten somewhere, The adapter is enabled and when i try to run (sudo /etc/init.d/networking restart) it does a bunch of stuff then trys to connect to the DHCP and I get this (DHCPDISCOVER oe eth0 to 255.255.255.255 port 67 interval x) 6 times with a different interval everytime. then no DHCPOFFERS recieved. My subnet mask is 255.255.255.0 and I cant change it to 255.255.255.255

That was exactly the same problem I had yesterday. I was trying to fix a networked printer problem, and lo and behold, all net access to my server just stopped outright. This was shortly after some updates relevant to 9.04 occurred. NetworkManager in all its buginess was of zero help.

Long story short, right now my server at home cannot see the outside world. I have my wireless router set to give my server a static IP of .0.199. I had it set wrong on the server side, thinking I was still using .100.186. 

Is there any reason why avahi is just randomly deciding on a 169.x address when all else fails? There seems to be no way to choose the IP it chooses.

---

### Post by jpaytoncfd on 2009-05-18
I would like to do a static IP but my router dosent have that option. I have wireless too but I havent messed with it, what do I edit to get it to connect to my wireless router? It has WPA security.

---

### Post by superprash2003 on 2009-05-18
setup static ip in ubuntu, not router

---

### Post by Iowan on 2009-05-18
Not sure about Kubuntu, but the Network Manager Applet on Ubuntu calls it a Manual configuration.


But first, try [this]("http://ubuntuforums.org/showthread.php?p=7280398#post7280398").
I was having same problem on my laptop.

---

### Post by jpaytoncfd on 2009-05-18
ok I set up a static IP restarted the network and tried restarting the computer, still nothing, I can pint the local host but not the router

---

### Post by Iowan on 2009-05-18
You can probably ping localhost even with cable disconnected.
Post results of **ifconfig -a**. 
(Did you try removing the rfc3442 stuff?)

---

### Post by t0mppa on 2009-05-18
@s1500: I actually had a similar-ish issue with a Kubuntu 9.04 laptop yesterday. In the middle of some other work, the wired connection just stopped working out of the blue.

Turned out that it had lost the default route to the router for some reason and refused to accept it back even with a 'route add default gw <ip address>', nor did any of the other things (like rebooting) I tried work. End result was that before I plugged the computer into another network, couldn't get the wired connection working.

---

### Post by s1500 on 2009-05-18
> **t0mppa said:**
> @s1500: I actually had a similar-ish issue with a Kubuntu 9.04 laptop yesterday. In the middle of some other work, the wired connection just stopped working out of the blue.

Turned out that it had lost the default route to the router for some reason and refused to accept it back even with a 'route add default gw <ip address>', nor did any of the other things (like rebooting) I tried work. End result was that before I plugged the computer into another network, couldn't get the wired connection working.


I changed the IP to what the router assigned for it, and it still doesn't work. This is really getting to be much more complicated than it should be.

wicd just gave me a python path error when I installed from .DEB. I can't believe that.

Is there a way I can jjust run a recovery CD to have it re-setup networking for me? I'm at the giving up point here.

---

### Post by s1500 on 2009-05-19
I made some headway last night, but not by much. I got the networkManager applet to show up again after some elbow work.

I hooked up a wireless dongle I had laying around. Somehow I got that to play nice with NetworkManager. I put in my credentials, and I can connect just fine to the interwebs through that. However, I really want to go back to where Ethernet works again.  It's not perfect, as I can't get samba to work, probably due to the fact the machine name can't be resolved by my Windows machines. 

NetworkManager shows "never" for my eth0 connection. When I get home I'll post all the info I can scrounge together. Would it be possible just to reboot to an earlier kernel(I see it in webmin's grub menu) and leave it at that? Looking at the bug reports for NetworkManager, it might be a new bug introduced in the later kernels where certain Ethernet cards get skipped entirely.

---

### Post by s1500 on 2009-05-20
Think I may have found the ultimate problem. The 8-port switch failed, completely. I think it may have even fried my ethernet jack on my laptop while testing it out. Main desktop gave me the dreaded "limited or no network connectivity". Replaced the switch, and I'm golden. Naturally, samba failed again(set it back to "SHARE" and it's good again) and I can't resolve the hostname in a web browser, but it works again.

---

