---
title: "Can't connect wirelessly since replacing Westell router"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by tdurhm on 2011-11-23
Hi Ubuntu people,

I have os ubuntu 10.4 on a dell xps m140 laptop. Since having my Westell router replaced I have been unable to connect my wifi. No problem at cafes and other people's houses, just not at my own home... so I assume my driver is working with my wireless card. I have an intel 2200BG [calexico2]. I can see my connection and when I turn my computer on it attempts to connect, asks for my password, but then never completes the connection. Not sure how to manually configure wireless settings. My new router is a Westell model 327W. Once this was installed, Zoomtown had me name the connection and select a password. Haven't been able to connect wifi since. Thank you for any help.
T

---

### Post by lswb on 2011-11-23
Zoomtown is your ISP, correct? I'm guessing you are able to connect OK via ethernet on your 327W. Without knowing more information, I suspect that the password that Zoomtown asked you for is for access to their network. In general, this will be different than the password used to access your router settings. Check your documentation for the factory or default router password. Most commonly, (but not always) these routers will configure themselves to used the IP address 192.168.1.1. With your computer plugged into an ethernet port on the router, type that into a web browser address bar, hit enter and see if you go to a router setup or info screen. There will be a reasonably navigable menu or tab system of some kind. It will prompt you for a login and password when you attempt to make changes or access certain settings. If you don't have router documentation, maybe Zoomtown can tell you, and many westell routers used default (factory) login/password of admin/admin or admin/password (with variations on capitalization) You can also find lists of default login/passwords for many routers by googling. Once you've logged in to the router setup successfully, you will be able to set up your wifi network and security system including a WPA (recommended) or WEP (easily crackable) passkey. Again, this will also be different from the router setup password and your ISP network access password.

---

### Post by coldraven on 2011-11-23
Are you sure that the wi-fi key is not printed on a label on your router?

---

### Post by tdurhm on 2011-11-24
Hi, yes, Zoomtown is my ip.. I've been to the 192.168.200.1 site that you spoke of. The wireless security is listed as WEP... not sure what I need to look for or change once I'm there. When I spoke to zoomtown they had me configure some things... selecting channel 11, making sure the "key 1" has my password, etc. They refused to help me further once I said the word Linux. Most of what I am familiar with on the Westell site is listed under configuration - basic - security. So what exactly do I need to change? Or what should I be looking for?
Thank you so much
T

---

### Post by lswb on 2011-11-24
I'm assuming your running more or less standard gnome2 panel on 10.4 here.

While connected via ethernet, open a web browser & login to the router configuration server app at the 192.168... address. On the wifi security settings page, make a note of your wifi network name (sometimes called essid) and your WEP password. You can change it here if you want to. logout and close the browser and disconnect the cable. Make sure your laptop wifi adapter is turned on. Right click on the network manager applet icon, usually at the right on the top panel near the speaker and email icons in the indicator area. Make sure "Enable Wireless" is checked. Close that menu. If after a minute or so the laptop does not try to automatically connect and prompt you for the password, left click on the network manager icon, and select your network name. Enter your password and if all is well it should connect in a minute or less. Once connected the NM applet icon will change (depending on your desktop theme) to indicate you are connected, usually with a signal strength indicator style icon of some kind. HTH.

---

### Post by tdurhm on 2011-11-24
The issue is I can't connect to my wifi. I know the name of my connection, I've double checked my password, but my computer will not connect... it just keeps asking me what my password is, but never fully connects (indicated by 2 green dots)... it only gets one of the green dots. Am I suppose to change something on that 192.168... page? Like renaming my connection? I gave it a name when I got the new router. Should I be looking for something on the router itself to input in one of those fields on the Westell page? Should it be WEP 64 bit? Perhaps my ssid is not the same in all places? I'm quite new at troubleshooting on my own, as I've never had a problem up until now.
Thank you
T

---

### Post by lswb on 2011-11-26
I'm at a loss as to what the problem might be, especially since you mentioned that you connect OK elsewhere. The only thing I can think of is that something in your router wifi settings does not match your computer settings. I'm hesitant to suggest any changes without being able to see the effects myself. Try this, disable wireless through the NM applet (right click, uncheck "Enable Wireless." Open a terminal and run this command "tail -F /var/log/syslog" Reenable wireless and watch for error messages in the terminal window. Maybe you'll see something giving an indication where the breakdown is. 

The other thing possibly worth trying is to just start over on your local network, i.e. give it a new name and password and select whatever security setting you want. Then your system will see it as a new connection and you can try entering the new password and so forth.

---

### Post by tdurhm on 2011-11-26
I'll give that a try thank you. However, when I turned my computer on this morning my wifi automatically connected! Very strange. It has not worked in about a month and suddenly without doing anything to it, it started working. Is this an indication of what could have been the problem?? 
Thanks again,
T

---

### Post by lswb on 2011-11-26
Glad that things are working for you. It may be one of life's mysteries why you had problems for a month. You might find a clue by looking at the log files from the time when you had trouble. Try /var/log/syslog or /var/log/messages.

---

