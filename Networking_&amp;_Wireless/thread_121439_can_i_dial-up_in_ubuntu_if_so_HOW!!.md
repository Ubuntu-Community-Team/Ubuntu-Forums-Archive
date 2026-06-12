---
title: "can i dial-up in ubuntu? if so HOW!!"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by markcaetano@gmail.com on 2006-01-25
i have been looking for 20 mins on my other linux pc (i am using my win pc)for a way to dial my dial-up connection my pc is plugged in to the line and it has a dial tone but i cant find a way to dial-up and use mozilla
i need any help as its a very desperate situation PLEASE HELP!

---

### Post by Who on 2006-01-25
Hi,

In short - yes you can, but it may not be easy!

How easy it is all depends on whether you have a hardware or software modem - software modems use the OS to do a lot of the work, so you need special drivers for them - most manufacturers of these cards don't make these drivers for Linux, so you have to use some that have been reverse engineered, or use Linuxant's - which I have found to be ideal at just $20.

If your modem in windows is an HCF or and HSF modem then you are may have hassle on your hands (I.E it is a software modem or a controllerless modem)

If you are feeling luck, go to 'System-->Admistration-->Networking' and select 'Modem Connection'. Configure that and then try to connect. If that doesn't work, then you need to find out how to get the drivers for your modem. 

Google is your friend here, find out the make and model number of the modem (either in Windows or using System-->Administration-->Device Manager  (it may not be called that, but by default it has a grey and green icon - I'm not on ubuntu at the moment). So, if you have a connexant, you're in luckISH - a driver is available but not free...

I guess once you know this information then you can come back here and we can help you further - there is a 'winmodem' howto in the forums that can be found by a search for winmodem.

If you feel like going it alone, I would just reccomend wvdial - in NZ on my Aunt's PC it was the only one that worked ymmv...

Good Luck

Who

---

### Post by markcaetano@gmail.com on 2006-01-26
well i guess im in luck cause it is a conexant modem from bout 2000ish:p 

another question:does ubuntu not sopport dial-up:confused: 
also i dont have $20 to spare of have a credit card
thanks for the offer anyways
if it can pleeeeeeeeeeeeease tell me how to connect[-o< 

any help most appreciated little or small

---

### Post by Zalbor on 2006-01-26
When I had dialup, I used "sudo pppconfig" to make the connection and "pon <connection name>" to dial, "poff" to close it. But the menu item Who told you about could work too.

---

### Post by Who on 2006-01-28
Hi,
What Zalbor says is true - sudo ppconfig would do the job nicely, ONCE you had the modem drivers.
IF it is an HSF or HCF modem (winmodem!) then you will need some drivers. If it is a 'real' modem then you should be able to autodetect it using the Gnome networking app I described in my earlier post. 
If you _really_ don't have $20 then you could try your luck with this:
[http://hsf.szm.sk/english.htm](http://hsf.szm.sk/english.htm) looks to be free, but if you go with the Linuxant one you get good support. 
Linuxant make a free driver that is limited to 14.4 kbps which you can use to test their driver, which can be found in the download section of their website. 

I can give you more help when you post:
Whether the modem is HSF or HCF, whether you have tried to use the Netorking Admin screen in System-->Administration-->Networking (select the 'modem connection') and then click configure. There is a 'Device' tab (or similar, the middle tab, anyway). Select that and try autodetection.

The Linuxant drivers have very good instructions about how to use them, and a SPECIFIC UBUNTU ONE, which you should take care to get - make sure it is right for your kernel.

Good luck!
The more info you give us the more help we can give you!

Who

Ps: Linux supports dial up just fine with REAL modems and any modem there is a driver for, just like Windows. Only, because Windows is bigger the manufacturers make the drivers for that platform. Drivers for linux are made by other people/companies that have to survive somehow!

---

### Post by MacV on 2006-01-28
[QUOTE=markcaetano@gmail.com]well i guess im in luck cause it is a conexant modem from bout 2000ish:p 

another question:does ubuntu not sopport dial-up:confused: 
also i dont have $20 to spare of have a credit card
thanks for the offer anyways
if it can pleeeeeeeeeeeeease tell me how to connect[-o< 

any help most appreciated little or small[/QUOTE]

Most of the distros I tried do support dial up. Like others said, it all depends on if you have a software based modem or hardware based. You have a software modem, so it will be a PITA to get it working. When I was using dial up, I gave in and just brought an external dial up modem. Those almost always work with no hassle.

---

### Post by Who on 2006-01-29
My experience with a conexant winmodems is that it is very simple provided you pay for the drivers. You can decide whether you want to pay for a new modem or for the drivers...

---

### Post by markcaetano@gmail.com on 2006-01-29
helooooooooo anyone on this forum hear me!!!
IM DESPERATE

---

### Post by Dragonbite on 2006-01-29
Did you try  as suggested by Who?> use the Netorking Admin screen in System-->Administration-->Networking (select the 'modem connection') and then click configure. There is a 'Device' tab (or similar, the middle tab, anyway). Select that and try autodetection.

---

### Post by markcaetano@gmail.com on 2006-01-31
yeah i tried it but it didnt :cry: work my sudo has gone cooky lately:cry: :cry:

---

### Post by Who on 2006-01-31
If you want help it is really important that you report back to the forum with informative feedback about what you have done! I was waiting to see whether the simple solution worked:
I will give you more help when I know:

Are you prepared to spend $20 on the Linuxant Driver?
Have you got the time to mess around trying to make the free driver work?

What do you get at the terminal when you type uname -r

What do you mean when you say sudo has gone cooky? Can you remember what happened to stop it working?

Speak soon,

Who

---

