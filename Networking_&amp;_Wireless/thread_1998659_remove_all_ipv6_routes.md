---
title: "remove all ipv6 routes"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by surfer on 2012-06-07
i have the 'slow networking problem' that has been discussed in man threads. the solution usually given here is to disable ipv6 completely.

but as the ubuntu-devel mailing list seems to agree that the problem is rather a misconfigured route that the presence of ipv6 ([see this post]("http://ubuntuforums.org/showpost.php?p=478267&postcount=8")) i was wondering how i can remove all ipv6 routes.

i assume that
```
$ ip a | grep inet6
$ ip -6 route 

```
should then both be empty.

---

### Post by poolet on 2012-06-07
Let me clear something before answering your question. Networks differ!!!  Even if we compare 2 networks topology with the same computer, same os and same configurations,and we assume that the provider is the same for these two networks still the difference is huge.. 
::**Explanation**::  First of all two types of network, a) cable, b) adsl, These two networks have their own pros and cons.. I don't want to waste time to explain that, so try wiki for more information, In the meantime the biggest difference of these networks are the traffic packet..!! The first one (cable),  your connected into an mode that consists of neighbors, and includes the branching network in areas of ISP. It's the most used but not the most stable..(Through the use of a cable modem you can have a broadband Internet connection that is designed to operate over cable TV lines. ) The second one (ADSL) your connected directly into the patch panel of the ISP via the hot-line,DSL uses a sophisticated modulation scheme to pack data onto copper wires. DSL is sometimes referred to as a last-mile technology because it is used only for connections from a telephone switching station to a home or office, not used between switching stations. DSL is also called an always on connection because it uses existing 2-wire copper telephone line connected to the premise and will not tie up your phone as a dial-up connection does. this is an old method that is not to much familiar by big companies but still enough capable to rival the new one (cable)  since it more stable and more secure(nothing is secure btw just comparing the two types..)  Now, depending of your delay or traffic network, the best thing that you can do is to call your ISP and ask for help... Some times the mode/router is upgrade and need new to reconfigure or something is going on with the synchronization, with other words they explore your problem, and may are able to fixed for you, instead of searching hours without results.. 

before you continue with that make sure that you have ask your self the following questions:: 

1. What I pay for the network?? (free/monthly/yearly) 
2. What's the speed I must have ?? (1Mbps/2Mbps/5Mbps/10Mbps/20Mbps/40Mbps/etc...)
3. What's the real speed that I should take internally?  (be-careful internally manning website that are located into your areas/country)
4. What's the real speed that I take into an external traffic ?? 
5. Delay?? (internal/external) 
6. After the 5th answer if you fell that you still have right and you have really problem, call your ISP... Is your technical support  find out a problem ? (Yes/No)
7. If your ISP explore a problem they are obligated to fixed it.
8. If your ISP isn't find out any problem take a note: and simple write down the following:::: 

a) speed I should have? 
b)the speed that I have ?? 
c) ping the modem/router (what's the delay???)
d) ping the modem/router from other computer (any deference ?? ) 
e) ping yahoo.com what's the delay ?? difference between the others ping?? 
f) ping PC1 and PC2 what the respond ?? 
g) what's the TTL ?? 32/64/128?? 

if all of the above questions correctly then you need to capture your network to see whats happens.. Where my network starts ?? From which area of my ISP starts?? Is any other area that I can suggest to my ISP ?? (if is closer)
from where I pass to go to my destination.???. The number of packets that I receive/send?  Is any strange  firewall in the middle?? 

Don't thing about IPV6 (version 4 or 6) it doesn't matter if it's enable or disable... some providers are sending packets to IPV6, since is always enable,In addition it doesn't affect your real network, there are thousand of reasons. The best way to figure out is to capture your network.. Download wireshark.. set it and run it correctly as root, capture your network for 1-2 as you are connected and use your network, save the file and then go back and check the path of your network...  Probably there is something that create delay..  Also before you capture clear all your cookies and also dns cache... More details about wireshark the check the links below..

[http://wiki.wireshark.org/FrontPage](http://wiki.wireshark.org/FrontPage)
[http://wiki.wireshark.org/CaptureSetup](http://wiki.wireshark.org/CaptureSetup)

Good luck!!!

---

### Post by surfer on 2012-06-07
by the way: the slow connection problem was due to a misconfiguration, but the question remains...



@poolet

thanks for the detailed reply!

the thing is: this is an isolated network: no ISP, no connection to the internet, no DSL, i run my own network components and and servers.

---

### Post by poolet on 2012-06-07
Be more specific please and I would try to help you.. Explain how is works, and let me know exactly the topology of your network..  Very important thing, is to determine the areas of your network... what kind of component your using ?? is there any app soft that used by the network?? sharing ?? is any database involved?? Hope that,we figure out whats going on with some useful informations first..! :)

---

### Post by drdos2006 on 2012-06-07
Here is how I disabled IPv6.

From your machine, type :

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1 rather than 0.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf
From your machine, type :
sudo  gedit (or vi )  /etc/sysctl.conf

Add the following lines at the bottom of the file.
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Fo vi, Write and Save with:  Esc(cape key)  :  w  ( to write  and )	Esc(cape key)  :  q  ( to quit ).

Reboot your machine.
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns or IPv6
Change IPv6disabled to true
Restart Firefox.

regards

---

