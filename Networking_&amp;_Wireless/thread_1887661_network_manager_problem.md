---
title: "network manager problem"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by einstenian on 2011-11-27
Hi guys. I'm writing from ubuntu maverick. When I am connected via ethernet cable to my router, if I deadlift  the cable , network-manager does not automatically reconnect. Do you ou know how I can  fix this?

---

### Post by bluexrider on 2011-11-27
First thing that comes to mind is DON'T DEADLIFT THE CABLE.



What is "deadlift the cable" terminology? (geek speak)

---

### Post by einstenian on 2011-11-27
I meant that when refitting the cable,  NetworkManager does not reconnect
Do You know how I can fix it?

---

### Post by bluexrider on 2011-11-27
Fairly simple:

Main menu> Preferences> Network Connections> Under Wired tab, Auto eth0, click edit.

Make sure Connect Automatically is checked. Then click saved. It will prompt for admin password. 

You should see it restart.

---

### Post by einstenian on 2011-11-27
didn't work..

---

### Post by bluexrider on 2011-11-27
it may not be your machine....check your cable

---

### Post by einstenian on 2011-11-27
the cable is ok, because when i boot in windows ther is not problem whit the replug problem. But i noticed a strange thing: if i plug the cable in another routher ethernet port the  problem disappears

---

### Post by bluexrider on 2011-11-27
so its not a Ubuntu issue after all

glad its working


SOLVED

---

### Post by einstenian on 2011-11-27
the problem IS UBUNTU because  DOE'S NOT OCCOUR with windows. If i replug the cable to the same port  IN WINDOWS all it's ok..

---

### Post by bluexrider on 2011-11-27
> **einstenian said:**
> the cable is ok, because when i boot in windows ther is not problem whit the replug problem. [COLOR=Red]But i noticed a strange thing: if i plug the cable in another routher ethernet port the  problem disappears[/COLOR]


then what was this to mean? :confused:

---

### Post by einstenian on 2011-11-27
The router has 4 ethernet lan ports. When i unplug the cable from one port  and reconnect the cable to the same port the pc does not reconnect. If i use another port all is fine and the connection is restord

---

### Post by bluexrider on 2011-11-27
ok, ubuntu doesn't know that you disconnected it and reconnected it if you use say NIC1 but if you disconnect it from NIC1 and connect it to NIC2 it reestablishes connection. YES?

---

### Post by bluexrider on 2011-11-27
we discussed this earlier:

go to your "Editing Auto Eth0", remember how to get their? under IPv4 Settings make sure your Method is Automatic (DHCP)

I have seen situations as such and have done a workaround.  

Under your Wired tab copy and record your Device MAC address example:XX:13:V7:E9:8D:4B your going to need it.


Ready, pain in the butt. 

access your router and under reserve MAC address use YOUR address from your machine.

Restart the router. DO NOT HARD RESET it. Restart your machine. Now check it out!

LAST OPTION or opinion. May be a broken driver. 

Good Luck

---

### Post by vasa1 on 2011-11-27
Hey BlueX [could you take a look over here]("http://ubuntuforums.org/showthread.php?t=1873217") when you're done? Please?

---

### Post by einstenian on 2011-11-28
> **bluexrider said:**
> we discussed this earlier:

go to your "Editing Auto Eth0", remember how to get their? under IPv4 Settings make sure your Method is Automatic (DHCP)

I have seen situations as such and have done a workaround.  

Under your Wired tab copy and record your Device MAC address example:XX:13:V7:E9:8D:4B your going to need it.


Ready, pain in the butt. 

access your router and under reserve MAC address use YOUR address from your machine.

Restart the router. DO NOT HARD RESET it. Restart your machine. Now check it out!

LAST OPTION or opinion. May be a broken driver. 

Good Luck


Thanks. I combed through the options of the router but there is no option to set the MAC Address

---

### Post by Neill_R on 2011-11-28
My apologies some people seem not to be able to understand fellow user's concerns. Why they feel obliged to give unhelpful answers I do not know.  I am assuming that in Network Manager you had or now have connect automatically and Available to All user both checked and it is not working if you disconnect and reconnect the cable? If you reconnect to another port the router most likely issues another IP-Address to your network card. Sadly I am on wireless Internet here either from Orange ICON 225 USB dongle or BT Openzone via a Linksys WUSB54GS usb wireless network adapter. Allow time for it to happen networking configuration can be slow.

I would recommend you look ad the command ifup for behind the scene information.

---

### Post by einstenian on 2011-11-29
> **Neill_R said:**
> My apologies some people seem not to be able to understand fellow user's concerns. Why they feel obliged to give unhelpful answers I do not know.  I am assuming that in Network Manager you had or now have connect automatically and Available to All user both checked and it is not working if you disconnect and reconnect the cable? If you reconnect to another port the router most likely issues another IP-Address to your network card. Sadly I am on wireless Internet here either from Orange ICON 225 USB dongle or BT Openzone via a Linksys WUSB54GS usb wireless network adapter. Allow time for it to happen networking configuration can be slow.

I would recommend you look ad the command ifup for behind the scene information.
Yes neither me understend why thei give such answers...I have already set  up  network manager as you said but nothing has changed. Strangely,  if I use ifconfig , the output shows that the card has an ip address! The problem  must be somehow connected to the mac address but I do not know more

---

### Post by einstenian on 2011-11-30
> **bluexrider said:**
> ok, ubuntu doesn't know that you disconnected it and reconnected it if you use say NIC1 but if you disconnect it from NIC1 and connect it to NIC2 it reestablishes connection. YES?
In fact i have wireless nic end ethrnet nic but i don't know if this is i the problem

---

### Post by einstenian on 2011-12-10
This problem seems a linux problem. I have tried many live distros and network-manager on my machine does not correctly manage router reboot when a cable connection is used. On windows the problem does not occur. Instead the nm has not this problem with the wireless !!

---

