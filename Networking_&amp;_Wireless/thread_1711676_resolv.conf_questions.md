---
title: "resolv.conf questions"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by colio on 2011-03-21
I posted a question over the weekend about my inability to connect to a wired network.  Someone suggested I check the contents of the resolv.conf file and noted that it should not be empty.  Well it is empty and now I have more questions:

1.  what should be in it?
2.  it seems to be read-only, how do I change this contents if that's the case?
3.  I can briefly connnect to a wireless network but the connection gets dropped after a couple of minutes.  During that time the resolv.conf file does have contents.  After the connection drops, the contents disappear.

Really struggling with this issue and I think if I can better understand this file and its contents I might be able to fix the problem, only I can't find a good explanation of this file and how it works and more importantly, how to edit the contents of mine or replace the file with one that works.

thanks for any help-

---

### Post by conneco on 2011-03-21
resolv.conf conatains the IP address of your DNS servers, it basically tells linux where to lookup names such as [www.google.co.uk](www.google.co.uk), if you use a network manager for you connections and DHCP then you dont really ever need to edit the file as Linux will do it for you

to edit the file you'd need to use the terminal and do it as root, so open a terminal and type 

sudo gedit /etc/reslov.conf 
to open it in gedit (ubuntu) else you can open it in vim (terminal text editor (harder to use))

sudo vim /etc/resolv.conf

as for you losing connection, what kind of environment are you in, is it a home network? what kind of router do you have. are you far away etc....

---

### Post by colio on 2011-03-21
home network, brand new Cisco Linksys e1000 router.  Works fine in Windows, no dropped connections (wireless, haven't tried a Windows wired connection).  Connection drops if I'm 3ft from the router so I don't think it's a strength of signal issue.

Should I try to manually enter the DNS addresses in resolv.conf or should I do it through network connections and set them up manually?  Is there a good step-by-step guide somewhere for setting up a new wired connection in network connections?  I just want to make sure I'm entering the info that's needed correctly and not entering or adjusting anything I don't need.

---

### Post by tgm4883 on 2011-03-21
> **colio said:**
> home network, brand new Cisco Linksys e1000 router.  Works fine in Windows, no dropped connections (wireless, haven't tried a Windows wired connection).  Connection drops if I'm 3ft from the router so I don't think it's a strength of signal issue.

Should I try to manually enter the DNS addresses in resolv.conf or should I do it through network connections and set them up manually?  Is there a good step-by-step guide somewhere for setting up a new wired connection in network connections?  I just want to make sure I'm entering the info that's needed correctly and not entering or adjusting anything I don't need.

It's not necessary to edit that file. I don't see why that would cause you to be disconnected from your network.

---

### Post by conneco on 2011-03-21
If your using bog standard ubuntu desktop an your linksys router has a dhcp server then you don't need to edit connections  atall or ur resolv.conf, delete any connections you have setup in the network manager and just plug the Ethernet cable in ubuntu should automatically grab all the info it needs from the routers dhcp server 

You really only need to edit connections if you havnt got a dhcp server or you want your pc to use a certain ip address both are not usually the case in a home network.

---

### Post by colio on 2011-03-21
DHCP is set up on the router and all connections are deleted, but wired network still isn't working.  The system says it's connected to the wired network but there's no internet, can't ping anything, no web sites are found, etc.

If it's not the resolv.conf file, where would the problem lie?

---

### Post by colio on 2011-03-21
It will connect wirelessly, but after a few minutes the connection drops, the contents of the resolv.conf file evaporate, and I get a screen asking me to re-connect to the wireless network using the password.  I click connect and it just searches and searches for the wireless network, never finding it.  Only way to get it to reconnect is to reboot the system and then it works again for a few minutes before dropping.

---

### Post by colio on 2011-03-21
OK, it looks like I stumbled upon a solution.  On the wired side, for some reason the MAC address was missing.  I found this by typing ifconfig and looking under the eth0 heading, then manually entered it on the wired connection tab of network manager.

The wireless problem appears to have been a driver issue.  I switch from the Broadcom B43 to the STA driver, something that wasn't possible until I got the wired connection working again.

thanks to all for pointing me away from a dead end-

---

