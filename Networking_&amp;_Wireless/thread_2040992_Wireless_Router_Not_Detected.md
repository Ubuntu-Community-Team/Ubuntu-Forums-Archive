---
title: "Wireless Router Not Detected"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by pjs100 on 2012-08-11
I am trying to hook up an Asus RT-N12/b wireless router to my home pc running Ubuntu 10.04.  My system seems to be not detecting the device.  When I ping the device through firefox, I get the message "network is unreachable".  iwconfig results in "no wireless extensions".  ifconfig gives data for eth0, lo, and ppp0 when the device is not attached.  When the device is attached, I get the same data except that ppp0 is gone.

I am using a speedstream 5100 dsl modem, and the network connection setting for IPv4 is set to "Automatic PPPoE".

Any advice would be greatly appreciated.

---

### Post by pjs100 on 2012-08-11
Correction on above post.  I meant when I ping the device using a terminal.

---

### Post by bakegoodz on 2012-08-12
Are you using the USB interface on the DSL or did you have some type of mobile broadband or dial-up setup on Ubuntu? Having a ppp0 interface is unusual. Try cleaning out configurations in Network Manger and make sure there is a Automatic (DHCP) setting for wired and try it again. Sorry for a basic question, but did you also make sure the Ethernet on the DSL modem is plugged into the WAN port on the Router and the Computer plugged into one of the LAN ports on the router?

---

### Post by pjs100 on 2012-08-12
Thanks for the reply.

Not sure what you mean by "usb interface".  The speedstream 5100 modem I'm using is very old and only has the phone jack coming in and the ethernet cable going out - to the correct port on the wireless router (always good to triple check the simple things-thanks), which then, through one of the 4 LAN ports is connected via ethernet cable to PC.  

You say having a ppp0 interface is unusual.  What would a more "usual" interface look like?  In "cleaning out" the configurations in Network Manager, I'm not sure which fields you're referring to.  At the "Network Connections" box I have 5 top options: Wired, Wireless, Mobile Broadband, VPN, DSL.  The first four are all blank.  The DSL option has one named field (DSL connection 1).  When I go to "edit" this field, I see "Wired" (MAC address:blank, MTU: automatic), IPv4 Settings (Method: Automatic PPPoE), DSL (my correct username and password), PPP Settings (BSD data and TCP header compression checked, PPP echo packets checked).

I have never installed a wireless router on this PC, but about a year ago I had a houseguest who did install her router on this box, and then removed it when she left.  Hmmm?

Thanks for trying to help me solve this by first using the Gnome GUI rather than jumping to a command line solution. I can go there if need be, but at this point in the evolution of this distribution, I like to think that basic functionality can be had by using the built in menu tools.

---

### Post by pjs100 on 2012-08-12
.

---

### Post by bakegoodz on 2012-08-12
I won't pretend to know every DSL modem and ISP configuration, but I setup several DSL modems and I yet seen one that uses PPP on the computer. I believe the DSL configuration tab is for DSL link other than Ethernet, like via USB. Try clearing out the DSL config and have it set to Wired instead.

---

### Post by pjs100 on 2012-08-12
Talked to ATT cust support, and PPPoE is the correct set up for their DSL.  Again, the core problem here is I can't ping the router from a terminal command line, or access the router through the browser using the router's address. Even when I search for it using lshw at command line, it's not there.  My modem doesn't store username or password- that's now handled by the tabs in NetworkManager configuration (the Wired tab doesn't have that option).

---

### Post by steeldriver on 2012-08-12
If you were connecting WITHOUT a router before i.e. direct from your  computer to the modem then yes you would use a PPP / DSL connection - but not now that you are adding a router to the mix, IT will store your PPP credentials and handle the DSL login stuff that your PPP connection used to do

Basically you need to connect to the router using a **wired **DHCP connection and set up the 'WAN' or 'Internet' properties of that (whatever ASUS calls them) via the web interface with the PPP username and password given to you by your ISP - after that all your hosts on the LAN should connect either via the same DHCP pool (typically 192.168.x.y) or with any static IPs you specify (or reserve via the router's LAN side setup)

---

### Post by pjs100 on 2012-08-13
Yes, that worked.  Such a simple thing as setting up a wired connection with DHCP and applying it (in NetworkManager) was what let me connect to the router.

I don't have time or energy left tonight to configure the router, but tomorrow night, when I work with this more I will mark the thread solved.  Thank you bakegoodz and steeldriver for your help.

P.

---

### Post by bakegoodz on 2012-08-13
Interesting, I have always done the PPPoE config on the modem its self. I see that the Routers support PPPoE login too.
[IMG]http://i48.tinypic.com/1hqfc2.png[/IMG]
[IMG]http://i48.tinypic.com/2558lkm.png[/IMG]

---

### Post by pjs100 on 2012-08-13
Wireless network is up and running.  

System -> Preferences -> Network Connections -> Wired (click tab) -> Add -> in box "Editing Wired connection" (choose) Method: Automatic (DHCP), check boxes for "connect automatically", and "available to all users" (this may not be appropriate for all) -> Apply.

Power down all components.  After installing wireless router between modem and computer, power up in this sequence: Modem (wait 1 minute), Router (wait 1 minute), computer.  After Ubuntu booted up, I opened Firefox and the Asus install screen came right up.

Thanks again to bakegoodz and steeldriver.  Believe it or not I really did spend about an hour looking through Ubuntu documentation sites, and then another hour and a half reading posts on this part of the site before posting my question.  All the Best to you.

---

### Post by steeldriver on 2012-08-13
Glad you got it working :D

---

### Post by bakegoodz on 2012-08-14
Great job seeing the problem through. I've gained my skills not by having above average intellect, but by keeping at a problem until I figure it out.

---

