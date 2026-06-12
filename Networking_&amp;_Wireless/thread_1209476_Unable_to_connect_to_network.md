---
title: "Unable to connect to network"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Ebbs on 2009-07-10
Hello,

I am currently running Ubuntu 8.10. I recently bought a Belkin n wireless adapter version F5D8053ed, I only realised after that it is not listed in the supported pieces, but none the less, I tried to install it. Its rather new, I believe, and I thought it was worth a shot.

I downloaded nDiswapper and used the CD to download the driver. No problems here, my PC recognizes the adapter and can even find networks.

The problem arises when I try to actually connect to a network. I click on my network, it tries to connect then after a while asks for my WEP key. Once entered it tries again to connect, and once again fails. It then asks me to enter the WEP key again, if i click on show password, the one I entered seems to have disappeared and I am shown a completely different one. I enter the real WEP key and try again...as you can imagine, the cycle continues.

I tried without WEP on, and still no luck.

Any idea?

Thank you in advance.

---

### Post by superprash2003 on 2009-07-10
did you enter the right authentication tpye like 64bit , 128bit etc.. try with all options

---

### Post by stevebratt on 2009-07-10
im having the exact same issue ive just installed a BCM4306 Broadcom Driver using Ndiswrapper and it wont authenticate either just keeps asking for my WPA-PSK Key over and over everything else seems to have gone perfectly.
 
I know the card works fine and can connect to the wifi router under XP so must be some kind of software configuration. ive actually spent a solid 8 hours trying to sort this out lol.
 
im trying to connect to a Netgear DG834GT. Does anyone have any idea what might cause this ?

---

### Post by stevebratt on 2009-07-10
i have just read on a webpage that i googled, that someone else is having the same issue and their wep key is a 10 number password just like mine, mine also starts with 0. i wondered if this could mean anything might just be coincidence though

---

### Post by bitwit on 2009-07-10
This technique should work by simply plugging into a wired router.
 
I have had this problem before with the Broadcom wireless nic. To solve it I plugged a Linksys USB wireless nic into my laptop. It was recognized immediately and gave me access to the internet.
 
The next step I took was to change my setting for downloading updates and upgrades. Be sure to check the proprietary drivers box. This will allow you to receive the proper drivers you need for the Broadcom wireless nic.
 
Now go into software updates, under administrator, and click on updates. Finish updating your computer.
 
Now go under administrator and click on Hardware Drivers. There you should see drivers for the Broadcom wireless nic and any other drivers that you might need.
 
Activate the Broadcom wireless nic. Please be patient because this takes a few minutes.
 
Once the driver is loaded, I recommend restarting the computer. When the computer is back online the Broadcom wireless nic should be working.
 
As a rule I only activate one driver at a time and test the results. Be sure to unplug from the router or modem.
 
Good Luck,
 
B

---

### Post by stevebratt on 2009-07-10
are you talking about the drivers that come with ubuntu (well are downloadable via updates?) unfortunately for this card the ones that work with ubuntu are only able to use 802.11b and the speed of that was just really awefull. it was like going back to 56k but true they did work.
 
however most websites say they this card should work using ndiswrapper with 802.11g and i know im so close as the card is recognised, the drivers install and i can scan for wireless networks im sure its probably something ive changed by accident when trying to get it to work in the first place.

---

### Post by stevebratt on 2009-07-10
to make this a little more confusing, at least to me, ive just removed WPA-PSK Security from the connecion via the router and set the Auth to open no key required and the connection has connected straight away im using it now so the driver is working at least to a point

i wonder if its the wireless manager is there another i can try?

---

### Post by bitwit on 2009-07-11
> **stevebratt said:**
> are you talking about the drivers that come with ubuntu (well are downloadable via updates?) unfortunately for this card the ones that work with ubuntu are only able to use 802.11b and the speed of that was just really awefull. it was like going back to 56k but true they did work.
 
however most websites say they this card should work using ndiswrapper with 802.11g and i know im so close as the card is recognised, the drivers install and i can scan for wireless networks im sure its probably something ive changed by accident when trying to get it to work in the first place.

stevebratt,

Although I have 10 years experience with Linux, I did not have much luck with the ndswrapper program.  That is why I downloaded the restricted drivers via the Internet.  I have no problems with speed on the Internet. I'm writing a second post that explains it better.

dr. bitwit

---

### Post by bitwit on 2009-07-11
> **stevebratt said:**
> to make this a little more confusing, at least to me, ive just removed WPA-PSK Security from the connecion via the router and set the Auth to open no key required and the connection has connected straight away im using it now so the driver is working at least to a point

i wonder if its the wireless manager is there another i can try?

It might be the wireless manager.  About a week ago I upgraded to 9.04 and the wireless manager is much easier to use.  The best success I had is with the procedure I did with the restricted drivers that don't get on the CD.  Don't be afraid of them because they are tested by Ubuntu.

Dr.b

---

### Post by bitwit on 2009-07-11
[FONT=AlBattar]This is something that I would like you to try.  At the top of Ubuntu point at System and click once on it.  Move the cursor over Administrator.  When the list box opens move your cursor down to to Hardware Drivers and click.  When the Hardware Drivers dialogue box opens, see if the proprietary Broadcom B43 wireless driver is listed.  This is the one I use with my laptop.  It has been tested by the Ubuntu developers and works very well.  If it is there, I recommend activating it.[/FONT]
 

 [FONT=AlBattar]If you don't have it, this is what you are going to have to do.  Use the same path, System>Administrator but this time go to Software Sources.  In this dialogue box put a check in the box next to “Proprietary drivers for devices (restricted)”.  These are files that are downloaded from the Internet.  After closing the box most files will download immediately.  You may see a red down arrow in the top right of the screen.  Just click on the arrow and follow the directions in the dialogue box.  Return to the Hardware Driver dialogue box and see if the driver you need is there and activate it.[/FONT]
 

 [FONT=AlBattar]I use this driver and find it is fast enough to provide excellent Internet gaming.  I hope this helps.[/FONT]
 

dr. b

---

### Post by stevebratt on 2009-07-11
hi, yes this is the driver and method i had already tried with my ubuntu installation however it was after i had tried the other method that is not ndiswrapper or the method you suggest i used the cutter? method aswell?
 
so it may be that this is causing the problem. i may do a re install of ubuntu tonight as ive now messed up my wired connection and try the ubuntu driver again as you have suggested.
 
however to be honest i went onto ebay lastnight and bought a £10 minipci intel wireless card reccomended on here that i can use in my laptop instead which im hopefully going to have a lot more luck with.
 
for £10 which is around $16 its hardly worth the fuss!
 
thanks for your help

---

