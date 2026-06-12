---
title: "ndis or cutter for 4306 rev3"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2009-01-03
How can I tell which is running? If both are what happens? To run only is removal in package manager enough, or do I have to edit something? I have an emachine with a 4306 rev3, and no connectivity to a gateway with wpa. If I enter two different sets of commands I can 'sometimes' connect, but I think it is just luck. I have tried everybody's guides and troubleshooting tips. Ayuthia and Kevdog have gotten me the farthest. I am using the disk I was mailed. What else can I do. I do have a copy of Windows7 ready to install if no progress comes soon, but then I'll have to scraper the Ubuntu bumper sticker off my suv. Heeeeeelp, Dale.

---

### Post by melojo on 2009-01-03
Both of them can give very reliable info to you, if they are not able to help you then I doubt any one else can.  

Linux works well when you have linux compatible hardware or atleast have hardware manufactures make linux drivers just like they do for windows, but that usually is not the case.

You must use the Operating system that works for you.

---

### Post by Ayuthia on 2009-01-03
Wow!  To be mentioned with kevdog is quite a compliment!  You should be able to tell if which module is being used by checking:
```
lsmod|grep -e b43 -e ssb -e ndiswrapper
```
and
```
lshw -C network
```If both are running, lshw should be able to tell you which one is being used I would think.

The trick with ndiswrapper is to make sure that wpa is able to be used with it.  The way to figure this out is by using:
```
sudo iwlist auth
```Sometimes you will need to include the network card (wlan0 or eth1) at the end of the iwlist line.  It will tell you if the driver can use WPA.  Kevdog and I have tested some of the ndiswrapper drivers for the 4306 rev 03 card and I have been able to connect with WPA ( have not tested WPA2 yet) but kevdog has not.  This is because of the card rather than knowledge.  I am using a Dell Inspiron laptop that came with the 4306 rev 03 card installed and I think that kevdog is using a Linksys WMP300 pcmcia card if I recall correctly.

The 4306 rev 03 card has been pretty difficult for more people in the forums lately and I have not seen the reason why.  Hopefully ndiswrapper is able to find a solution for you, but if not, hopefully Windows 7 will do the trick and maybe you can still use Ubuntu through some VM or maybe use it in the future when improvements are made with the b43 module for your card.

---

### Post by DaleFarrell on 2009-01-04
Hey Thanks.I'm not sure what to do next. I don't need the laptop, as I have several others. I have been trying to get the wireless going since Gutsy Gibbon, as it did work in Feisty. I guess if I can eliminate all references to fwcutter, and just use Ndiswrapper it might work. Well my Windows7 image finished burning so I'll wave that at the laptop and see if that scares the Ibex into working. Thanks for all your help. Dale.

---

