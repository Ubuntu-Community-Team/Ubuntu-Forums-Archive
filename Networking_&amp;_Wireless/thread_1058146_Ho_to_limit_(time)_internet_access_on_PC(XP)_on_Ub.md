---
title: "Ho to limit (time) internet access on PC(XP) on Ubuntu LAN?"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by marcgh on 2009-02-02
Hi,

I need to limit the internet access (certain hours of the day) on a XP machine without disconnecting it from the wireless LAN.

My set-up is as follows:

**PC1**  - running exclusively Windows XP pro ( this because of some dongle issues on a RIP software), connected to a router via wireless.

**PC2**  - running exclusively Ubuntu 8.10 with latest updates and wired to the same router.

Router, TRENDNET - TEW-452BRP, connected to the internet ADSL modem.

If I use the access rights via MAC addresses it will disable browsing but also disconnect **PC1** from the LAN.

I need to preset **PC1** some hours of the day allowing internet browsing but still remaining on the LAN.
This setup need to be done from **PC2** or ones and for all in the Router.
Having a way to allow exceptional more browsing time would be a plus.

Samba shares are working between XP and Ubuntu and vice versa, so that part of the job is done!

Thanks in advance for any ideas, tips or tutorials,
Marc

---

### Post by icheyne on 2009-02-03
You can do this quite cheaply if you buy a [DD-WRT]("http://www.dd-wrt.com") compatible router and flash it's firmware to DD-WRT.

[http://www.dd-wrt.com/wiki/index.php/Access_Restrictions](http://www.dd-wrt.com/wiki/index.php/Access_Restrictions)

---

### Post by marcgh on 2009-02-03
Thanks Icheyne.

I went to the website and spend the past hour to read most about it and more specifically the WIKI.

I don't mind to change the router in, for example, a Linksys but where I get really scared is the flashing of the bios of the router.
Lucky as I am I may end up with a brand new bricked peace of scrap.

I will still google around and see if anything is available in my region with eventually the DD-WRT installed, that will suit me more.

Thanks again for the info.

---

### Post by Kebabman on 2009-02-03
I have flashed wrt54g's multiple time with the like of openwrt and it is a fairly simple process, you can just use the routers web interface to select the dd-wrt image and it sorts itself out...

---

### Post by marcgh on 2009-02-03
Now you are tempting me to really try it.
I think i'll go for it this week-end.

Thank you, Kebabman!

---

### Post by Powerman2442 on 2009-02-03
Sorry, just reread your original post, didn't see you said it was a Trendnet. Now I need to figure out if I can delete this post. :P

---

### Post by marcgh on 2009-02-03
No problem Powerman,

The Trendnet is a no go for the bios flash as suggested so I will change that one for a Linksys WRT... type. This Trendnet can be easily resold here.

So you can assume that by Saturday it will be a Linksys.

---

### Post by icheyne on 2009-02-04
It's not so hard to do.

The list of supported routers is here: [http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices).

Mine is a Buffalo WHR-HP-G54-1

If you get a router with a USB port, you can connect a printer to it and connected devices can share it.

---

### Post by marcgh on 2009-02-04
Hi Icheyne,

In this part of the world I can only have off the shelf the LINKSYS WRT54G - v5. And this is really the closest buy that I can find in the 3 main shops in our capital.

I know it is not an ideal model for what I intend to do with it but dd-wrt says it is still possible.

I understoud, an please correct me if I'm wrong, that I will be using the **Micro Generic** dd-wrt.x24 and NOT the **MINI Generic**.

My only question at this time is: will I still have the functionality to do as I need ( pls. see my first post ) or is this only possible with the mini generic?

---

### Post by icheyne on 2009-02-04
From what I can see, you will only be able to load the Micro version, as the router only has 2MB.

It looks like the Micro builds support Access Restrictions and the most important functions, so you should be OK.

[http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F#File_Versions](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F#File_Versions)

---

### Post by marcgh on 2009-02-04
Thanks again Icheyne!

I have now the router and will download the necessary files.

I like the tutorial on this site: 
[http://www.scorpiontek.org/portal/content/view/27/36](http://www.scorpiontek.org/portal/content/view/27/36)

I find it simple and comprehensive.

Tomorrow evening I will have plenty of time to start the 'operation' and surely I will let you know how it went.

---

### Post by icheyne on 2009-02-04
Good luck! I hope you don't waste your money.

I had a look at the DDWRT wiki and found this additional tutorial - [http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE](http://www.bitsum.com/openwiking/owbase/ow.asp?WRT54G5_CFE).

---

### Post by marcgh on 2009-02-04
Thanks, I'm not worried!

---

### Post by marcgh on 2009-02-04
Well I could not wait till tomorrow evening.

So I just made it a longer night as usual, copied all the settings from my former router.

Checked that I had all softs needed, read once more the various how To and decided to work with the one from scorpiotek.org.

Well, all was done in less than 15 minutes.....and all worked immediately and perfectly.

Another 30 minutes set-up and denying some user on the wireless LAN internet access during working hours and FINITO!

Many thanks to this very efficient Ubuntu forum and of coure a special thanks to icheyne !

good night to all. ( good day for the others)

I really enjoyed this.

---

### Post by icheyne on 2009-02-04
Great! :D

Sweet dreams...

---

### Post by marcgh on 2009-02-04
Forgot the proof !

:D

well, I have the screenshot 148Kb PNG
I click Avanced / Manage attahments
I selct the file / Upload / close window (when finished uploading)

save changes, and...no screenshot.
I will try again tomorrow.

---

