---
title: "Wireless network connection not working"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by falcon1 on 2006-06-09
Hi everyone. I should start this off by saying I am kind of new to linux and ubuntu, so be gentle ;) I recently setup a dual windows xp/ubuntu install, and it is pretty neat. Everything seems to be working fine, except for wireless networking (as you probably guessed by now). 

I tried two different guides that I found on these forums. The first one was using fwcutter, and that didnt work. Next I tried the gui version of ndiswrapper, and when I installed the driver, it said the hardware was found. Now I get a green bar in the taskbar that says eth0, and when I click on it, it brings up a window that shows I have a full signal to (what I assume to be) the wireless network. It sends packets fine, but it recieves 0.

I am using a dell Inspiron 9100, with a Dell Wireless WLAN 1350 WLAN Mini-PCI Card (in windows i ran the systeminfo command, and that is what it spit back at me).

I have tried all sorts of commands that I have found throughout the forum, and none seem to be working. I was hoping someone would be able to help me out. Thanks a lot!

---

### Post by Patsoe on 2006-06-10
Doesn't it tell you the name of the access point you're connecting to? By default, the system will never connect to an AP without your consent, I think - security reasons ofcourse. So if you didn't specify any, it's not associated with an AP yet.

---

### Post by falcon1 on 2006-06-10
Ah - yes, it does tell me the name. I just typed it in at first, but when I click on the drop down menu, I see the name, and a little wireless symbol next to it. Still recieving zero packets, though.

---

### Post by Patsoe on 2006-06-11
Complicated stuff...

What are you using to configure the connection? Do you use the default installed Network Administration Tool, or Network Manager, or did you just type it in the conf files?

Personally, I'm really rather impressed by this new Network Manager tool, which gives a very WinXP-like feel to the configuration. Fill in the blanks, click OK... :) But I must add, it doesn't work for everyone yet (which is why, I suppose, it's not the default tool in Ubuntu yet). You might want to give it a try.

wiki.ubuntu.com/NetworkManager :)

---

