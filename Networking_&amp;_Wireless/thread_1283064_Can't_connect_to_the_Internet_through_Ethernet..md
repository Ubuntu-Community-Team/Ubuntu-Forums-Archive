---
title: "Can't connect to the Internet through Ethernet."
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by jsmithlinux on 2009-10-05
Hello everyone,
 
I know nothing about networking, so I may not even be explaining this correctly - apologies in advance for my complete lack of knowledge and general incompetence. I bought a Lenovo S10-2 Netbook, and installed Xubuntu (Hardy Heron) on it. At home I have no trouble connecting to my ADSL internet connection through the ethernet via a router.
 
Today I brought the computer to work, and connected the ethernet cable (there's a 5-port ethernet switch here). No internet. My colleagues are using XP or Vista on their laptops and can get onto the internet with no trouble. I've tried the obvious physical solutions like taking the (working) cable from a colleague's computer and putting it into my computer, but without success.
 
Any help you can give me will be much appreciated. As I said, I know nothing about networking, but will certainly have no problems working with the terminal and posting the output of any commands you can suggest.
 
Thanks,
 
jsmithlinux

---

### Post by hal10000 on 2009-10-05
You have to look to a winxp system or ask your administrator to see how your network at work is configured, e.g. the ip-address(es) of your nameserver(s), wether the network is set up via dhcp or a static ip-address, the addresses of your proxy-server (if you have one). This might be enough to get an internet connection.
If you want access to your windows domain, you'll have to know your passwords and set up samba client on your linux machine

---

### Post by jsmithlinux on 2009-10-05
Thanks, hal10000, your information was useful and put me on the right track. It turns out that the network uses DHCP, and when I disabled roaming mode and selected DHCP, that solved the problem.

---

