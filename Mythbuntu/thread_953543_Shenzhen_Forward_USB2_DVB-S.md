---
title: "Shenzhen Forward USB2 DVB-S"
date: 2008-10-20
forum: Mythbuntu
---

### Post by AlecJ on 2008-10-20
I just purchased a Shenzhen Forward USB2 DVB-S from Ebay, with a view to try it on Mythbuntu 0.21.20080304-1.
It don't work..
The USB box uses a Leaguer (Shenzhen) MicroElectronics Co.,Ltd. LME 2510 chip  [http://www.leaguerme.com/English/ShowArticle.asp?ArticleID=47](http://www.leaguerme.com/English/ShowArticle.asp?ArticleID=47)
Mythbuntu or V4L-DVB has no firmware for this chip (that I can find).

Dmesg gives
usb 1-2: new high speed USB device using ehci_hcd and address 6
usb 1-2: configuration #1 chosen from 1 choice

as you can guess the device does not show up in the backend setup.

I'm searching for firmware now, all help wanted.

Thanks

---

### Post by scrauny on 2008-11-17
Hey!

Has anyone out there managed to get the Shenzhen Forward USB2 DVB-S boxes working with Linux/MythTV?

I'm thinking about getting one and would be interested in your experiences.

Thanks very much :)
Shaun

---

### Post by ar-grig on 2009-05-15
Hi !

have you found the solution for LME 2510 usb chip support under linux ?
if yes, please help -- i have the same problem.
thank you

---

### Post by AlecJ on 2009-05-16
> **ar-grig said:**
> Hi !

have you found the solution for LME 2510 usb chip support under linux ?
if yes, please help -- i have the same problem.
thank you

None as yet

---

### Post by ppjsgml on 2009-06-15
Hi, I contacted Leaguerme about a bug in windows driver and also asked them about a linux driver, and the guy who answered said that they are thinking on it in the future, so, maybe you could tell them you're interested on it.

"Copy of email"

Very thanks you mail and your great suggestion.
 
If you are sure your hardware is for MV0194,please kindly try the driver in the attachment,if the driver is not ok,please kindly send mail to me,thanks.
 
About the Linux driver, we will provide it in the future.
 
 
2009-05-18
"End of email"

So, we only have to know: when will come that future?

---

### Post by AlecJ on 2009-07-02
Thank you very much for the update.

---

### Post by ppjsgml on 2010-03-31
More info of it here:
[http://www.satelliteguys.us/showthread.php?t=191998&highlight=dvb-s+usb](http://www.satelliteguys.us/showthread.php?t=191998&highlight=dvb-s+usb)

Most info is for windows, but they're talking about developing a linux driver

---

### Post by tvboxspy on 2010-07-17
I have release a patch for the 
**[FONT=Arial][SIZE=1]DM040832731 DVB-S USB BOX[/SIZE][/FONT]**

[https://patchwork.kernel.org/patch/112442/](https://patchwork.kernel.org/patch/112442/)

I have had this patch under test for a number of weeks now and would appreciate any feed back.

Please Note this is for the 
DM04 LME2510 + LG TDQY - P001F =(TDA8263 + TDA10086H) ONLY

The other variants are still being worked on over the coming months.
MVB0001F (LME2510C+LGTDQT-P001F)
MV0194 (LME2510+SHARP0194)
MVB0194 (LME2510C+SHARP0194)
MVB7395 (LME2510C+SHARP:BS2F7HZ7395)

---

### Post by tvboxspy on 2011-02-20
All DVB-S tuners are now supported with the LME2510 and LME2510C.


[http://sites.google.com/site/tvboxspy/lme2510-linux-driver](http://sites.google.com/site/tvboxspy/lme2510-linux-driver)

---

### Post by AlecJ on 2011-02-21
> **tvboxspy said:**
> All DVB-S tuners are now supported with the LME2510 and LME2510C.


[http://sites.google.com/site/tvboxspy/lme2510-linux-driver](http://sites.google.com/site/tvboxspy/lme2510-linux-driver)


I will have to dig it out of the cupboard..

Thank you

---

