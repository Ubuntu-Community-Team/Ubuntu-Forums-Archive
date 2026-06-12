---
title: "How to install a  program with wine and get to run"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Bigjge on 2009-05-11
I have this here as still need help.   Using ndiswrapper and info from ubuntu, I can get on line.
I now need to install a program so I can communicate with my router.   I must use wine but cannot as of yet work out what to type in terminal and what to change.
All help needed please.

---

### Post by sgosnell on 2009-05-11
You can communicate with your router through firefox.  Just put in the IP address, probably 192.168.1.1, or maybe 192.168.0.1, or some variation of the last two digits.

To install programs under wine, you can either right-click and select run with... and type in wine, or you can click on the download link and when asked whether to run or save, select run, and choose wine as the program to open it with.  Wine should install it with no problems.

I've never needed any program to communicate with a router, though.  Every brand I've ever tried can be configured through the browser, with the correct IP address.  The router manual should tell you this.

---

### Post by chili555 on 2009-05-11
Please open a terminal and navigate to the location of the file you want to run:```
cd Desktop/Linksys/
wine setup.exe
```Or maybe:```
cd /media/cdrom0/Linksys
wine setup.exe
```However, be aware that not everything runs on wine. There is a whole crazed subculture surrounding 'How do I get (insert name of software here) to run on wine?'

Also, be aware that, most of the time, you can simply connect an ethernet cable to a LAN port on your router, point your browser to the setup pages, and do anything you need to do. The owners manual should state what the default IP address is for the router. For example, let's say it's 192.168.1.1. Set your ethernet interface, generally eth0 with an address in that range:```
sudo ifconfig eth0 address 192.168.1.2 up
```Then open Firefox and type in the address bar [http://192.168.1.1](http://192.168.1.1). Press enter and you should be in.

---

### Post by Bigjge on 2009-05-11
I thank you for reply.
Firstly I live in germany and they are total data protection crazy.   One cannot get info unless they think you need to know.
One cannnot get to router as you suggest if could would not be on sale.   One has to run program which is encrypted and only fritz box can read from the computer when set-up  disk is run.
I did try the commands in terminal as suggested but not recognised.
I can get on line but have no control of the firewall in router ie will not activate unless I turn on when go on line.
My daughter can not get to box controls with wlan is not allowed.
Need help to run disk.

---

### Post by chili555 on 2009-05-11
> I did try the commands in terminal as suggested but not recognised.What command was not recognized? wine? Or...what?

---

### Post by Bigjge on 2009-05-11
The commands as stated in last post from you I think.
Trying to run cd and install and the numbers for browser do not work nor typing numbers in firefox.

---

### Post by chili555 on 2009-05-11
Where is the program you want to run in wine? On a CD? I can only guess where it is. If it's on a CD, can you see it in the file browser? Right click the CD icon and select 'Browse folder'? Is the setup.exe or whatever you want to run, there? Can you right click it and select 'Run in wine'?

---

### Post by Bigjge on 2009-05-12
I have run disk with wine and worked OK.
The next problem is to go to terminal and change internet connection settings from ethO to pppO and I do not know this one and quite where to start.   I do know when changed to pppO I can get to router tthe same as with windows.
Can one help please.

---

