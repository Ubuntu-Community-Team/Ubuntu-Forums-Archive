---
title: "Connecting to Wireless Printers? In Ubuntu? HP Wireless F4580 to be exact..."
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by djpurity on 2010-12-22
Hello, the basics, I have an Acer laptop I converted to Ubuntu 10.10 by replacing the harddrive and installing Ubuntu on the entire new thing. Have had a lovely time getting to know this new O/S (new to me), as I used to be a big computer geek back in my college days (what happened?!?!)

Anyway, I got a new printer, which installed surprisingly easily without any problems whatsoever (I actually expected some!). It's an HP F4580 and it's a Wireless printer. I actually got the printer BECAUSE it is Wireless. But now comes the problem... I don't know how to Make it go Wireless. 

I didn't use any of the drivers off the CD/DVD that came with the printer. I didn't really even have to download anything special. I remember just going to System->Administration->Printing and the printer just being there, and I've been able to print to it. I think it uses the HPLIP drivers (it shows HPLIP and USB as the 2 connections).

But when I go to the device under said Printing option, there is an option for Network Printer ... would I find the printer under there? Would it be under Device URI?

Seems like the logical place to find it, but I've read some mixed reviews about this particular printer online about its wireless printing not being so up to par, or easy. So thought I would check with everyone on any Ubuntu or linux forum....

Thanks!

---

### Post by nah40 on 2010-12-22
I have an HP J4680 wireless printer and I had trouble setting up the wireless.
I don't remember everything I did, but I had to assign an address to the printer on the device itself. Then the computer found it.

---

### Post by djpurity on 2010-12-23
SOLVED!

WTG reading the freaking manual! Usually I just like to figure things out the old fashioned way by tossing the instructions in the trash with everything else, but this time I looked it up on the net. Wow, so imagine this is how it worked out.

First, I do have a WPS router. I logged on to the Router and there is a way to either actually click the button on the router or click the button on the router config screen (I am using a Netgear Dualband N rated wi-fi router, btw), which is accessed through the default website: routerlogin.net

Anyway, at the same time, on the printer you can try pressing and holding the wireless button for 2 seconds until it blinks. This means it will try to connect. They should communicate.

HOWEVER, if you are like me, your luck will not go with the first easiest try. You may need to proceed to step 2.

On this printer, you hold down the SCAN button and it will print out a wireless print report. On it there will be a PIN number for the device that will be good for 5 minutes.

Now is the time to go back to the routerlogin.net page in your browser and try the alternate to the press button option, which is "enter pin" option. This allows you to enter the client's PIN number, which is the same as what the printer just printed out.

I then entered it and turned the wireless back on by turning it off and then on by holding it for 2 seconds. It began blinking but soon turned solid, as they finally connected and saw each other! It was love at second sight!

I then got a confirmation in my router configuration menu that it yes, indeed, had spotted by new printer and successfully set up a link with it. The wireless button in the printer now no longer blinks, but is a solid blue. SO it now is officially "seen" through the router.

Now what that means for me printing to it, I will have to get back to you. Right now I have just been using the HPLIB and/or USB connector to get their thing on. But now I am anxious to get rid of as many cables in this room as possible. So I will try my next print job via the wireless.

Now I went into System->Administration->Printers and went to Add new printer. Under Network Printers, there was the HP4500 series (as it is known to Ubuntu). Ah ha, now I set up the name of the printer, as it searched for the drivers next... now it is printing a test page... WIRELESSLY!

Yes, the problem has been SOLVED! So for any further questions about the HP printers and Ubuntu, I think I may have some official "experience" with it! Boo ya! And to think all I had to do was call up my router's configuration screen, configure a link to the thing, and then find it under Network printers under Ubuntu... easy! :popcorn:

---

### Post by BantamD5 on 2013-04-25
AWESOME! log onto your router (go to your wireless connection information, and the default route is what you type in your web browser's address bar) and leave it alone.
then, push the blue wireless button on the printer for about 5 seconds, wonder if it did anything.. then go to printers>add>hp f4500 series etc.
works like a charm! thanks!:D

---

### Post by wildmanne39 on 2013-04-25
Thread closed. Please do not post in old threads.

---

