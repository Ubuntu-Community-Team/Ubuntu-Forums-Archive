---
title: "Need help Billion router"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by slyblade900 on 2010-03-24
Hi, i'm running ubuntu 9.10 (karmic koala) i cant get it to connect to the internet .
i'm using Billion router adsl , bipac 5200s
new to ubuntu , new to setting up anything in the internet 
any help ?

---

### Post by ajgreeny on 2010-03-24
Wired or wireless?  Usually a wired system just picks up the router signal without a problem, but wireless will depend more on the wireless adapter in your computer than the router.  In a terminal run ```
sudo lshw -C network
```and report the output back here.

---

### Post by TBABill on 2010-03-24
Do you mean your router will not connect or your machine will not connect to your router? ADSL modems normally have a solid sync light when they sync with the central office (or remote terminal if you are on a digital loop system to carry your dialtone).
 
If you mean your machine to your router, are you trying to go wireless or hard wired? You'll need to post the terminal output (cut/paste the results) from typing lspci in the terminal if you need help with your specific wireless adapter. For my Broadcom adapter I had to connect to my router hard-wired so I could then download the proprietary driver...easy for you to try if you are near the router and have an ethernet cord handy.

---

### Post by cascade9 on 2010-03-24
Sorry, not beign nasty ajgreeny, but sometimes I find this whole 'open a console and show us what it says' thing amusing. Its not going to help in this instance I think (but hey, I've been wrong before)


1st off, make sure that you've got your hardware setup right- LAN cable in the right port, pluged into the LAN port on your computer, etc. This guide shows you how it should be setup (you should have got this in your router box, if you bought it new, but I'm just putting it in here in case you got it 2nd hand or someoen forgot it at the factory LOL)-

[http://support.billion.com/_Internet/qsg/BIPAC5200series_%20QSGEN.pdf]("http://support.billion.com/_Internet/qsg/BIPAC5200series_%20QSGEN.pdf")

When you plug he phone line in, you should have the 'adsl' LED light up. If it doesnt light up, either your hardware setup is wrong, somehow, or your phone line hasnt been activated. 

I cant be sure for other countries, but I'm 99% sure its the same everywhere (I'm in .au) for ADSL, you'll need your username/password from your ISP. You will also need the PPPoE package (should be installed by default on almost every linux distro). (edit- you actually dont need PPPoE, firefox can remember the pasword for you, but its a lot easier to do things with PPPoE installed)

Open firefox (or whatever browser your using) and then enter- 

192.168.1.254

That will take you to the router login screen. Enter these- 

Username- admin
Password- admin

That will take you into the router. Now click on the 'quick setup setup' tab, and follow the dirctions, putting in your ISP supplied username and password. 

That should take a minute or 2, but then the 'PPPoE' light should go on, and you've got your internets all nice and working. 

Hopefully that helps ;)

Edit- if you are trying to get wireless going, its always easier to statr of using a LAN cable, make sure you'ev got the internet working fine, then move onto the fun + games of wireless. I should remember to say that, but seeing how I think wireless is more trouble than its worth and never use it, hopefully I'm forgiven for my minor oversight LOL

---

