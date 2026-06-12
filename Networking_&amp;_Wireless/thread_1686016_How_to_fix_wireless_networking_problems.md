---
title: "How to fix wireless networking problems"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by RedDagger on 2011-02-11
This may only work if you can detect your router from your ubuntu computer.

So after trying every possible outcome to try and fix my wireless on my ubuntu computer i had an idea i basically added my mac address to my routers device list (SKY SAGEM F@st 2504) and then tried to connect it was instant.  

Tutorial below:

**1.** find your computer name mine is SERVERADMIN-PC

**2.** Find your _**WLAN MAC**_ address e.g 00:11:22:33:44:55
Its probably on the base of your computer or laptop.

**3.** go to your browser (on a different computer) and type into the address bar 192.168.0.1 this is your router ip for some people it may be 192.168.1.1

**4.** Log in to the router find your username and password e.g mine is ADMIN,SKY 

**5.** go to your setup tab in the menu then add new station manually 

**6.** just type the computer name and mac and then click add wait and then reboot the router (i did just to be safe you may not have to)
 
**7.** Give it a test run on your ubuntu based computer and it should work if not then either you did not follow my instructions or you have a different problem.

Remember i did this on a sagem f@st sky based router i am not sure of the details of other routers.

_***[COLOR="Red"]I AM NOT RESPONSIBLE FOR ANY DAMAGE YOU MAY CAUSE TO YOURSELF OR YOUR MACHINES[/COLOR]***_

Happy networking guys :)

p.s. if you guys can expand on this tutorial i will be happy to edit it. and give credit where it is due

---

### Post by grahammechanical on 2011-02-11
There are two ways to find the mac address - I think.

go to Connection Information and the Hardware Address is the MAC address - I think

Also in a terminal type nm-tool the HW Address is the MAC address - I think

But take note: wlan0 has a different hardware address to eth0, which is different again to the hardware address of eth1.

Regards.

---

