---
title: "Tethering with iPhone via PDANet"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by gqstatus05 on 2009-01-06
Using Ubuntu 8.04 trying to tether with my iPhone. 

I followed these steps: 

Step 1: Go to the Terminal(Applications->Accessories->Terminal) and type the following.
Step 2 : If you are planning to setup a wireless adhoc network then you first need to know which interface of yours is wireless.For this in the terminal type iwconfig and the interface which does NOT say "No wireless extensions" is the interface you need to you.Otherwise just choose your wired interface.In this example let it be eth1
Step 3 : Now you need to stop network manager and bring eth1 down by typing sudo /etc/dbus-1/event.d/25NetworkManager stop and sudo ifconfig eth1 down 
Step 4 : Now you need to setup eth1 to adhoc mode for this type sudo iwconfig eth1 mode ad-hoc
Step 5 : Now enter in the channel you want to use.for example 6.for this type sudo iwconfig eth1 channel 6
Step 6 : Now enter in the name of the adhoc wifi network you want to create/join by typing sudo iwconfig eth1 essid 'anynameyouwish' 
Step 7 : Its always better you secure your adhoc network with a password(in this case 12345) therefore you can create one by typing sudo iwconfig eth1 key 12345
Step 8 : Now bring back eth1 by typing **sudo ifconfig eth1 up**
Step 9 : And give it an ip address(for example 192.168.0.1) by typing sudo ifconfig eth1 192.168.0.1
Step 10 : Thats it, your done

My problem is that I can't bring back eth1 using: sudo **ifconfig eth1 up** I tried other variations that I found online and no luck. It's annoying because it's like my terminal is not registering or something.

---

### Post by gqstatus05 on 2009-01-06
Here's a screenshot when I type in **ifconfig** in the terminal:  It shows that everything is setup for ad-hoc network: 
[IMG]http://img.photobucket.com/albums/v687/BadBoyDiddy/terminal.png[/IMG]

Now I rebooted the laptop and my ad-hoc network gq appears on the list of available networks but i'm unable to connect: 

[IMG]http://img.photobucket.com/albums/v687/BadBoyDiddy/Screenshot-1-1.png[/IMG]

---

### Post by gqstatus05 on 2009-01-06
When I click on gq it cycles and then bounces back to my default home wireless connection. On the iPhone I no longer see an option to connect to gq. I've been trying to get this working so I can post it on ModMyI.com for others to hopefully use. I would appreciate any help on this issue. Thanks

***Edit, BTW gq is no longer an option for available networks on the laptop now, it just disappeared. ***

---

