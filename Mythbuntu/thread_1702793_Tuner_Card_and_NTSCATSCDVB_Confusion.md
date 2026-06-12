---
title: "Tuner Card and NTSC/ATSC/DVB Confusion"
date: 2011-03-08
forum: Mythbuntu
---

### Post by platticus on 2011-03-08
I've been a Ubuntu user for almost three years now and absolutely love it.  My current setup is a legacy Windows XP MCE 2005 setup with an ASUS PVR-416 tuner card. I tried installing Mythbuntu before, and hit too many walls that I eventually gave up and told myself that when my tuner card either died or became outdated to a point of non-usability, I was going to replace it and with something Mythbuntu friendly. With the analog to digital conversion in cable TV signal, my tuner card, which I understand to be NTSC format, no longer receives the channels I need. Because of this quandary I am to the point where replacement or workaround is necessary. I've done all sorts of reading and research and explored Google for hours, but I think my general confusion on TV Signal standards and methods of integrating the PC with that signal is causing my non-fruitful searching. First, here's the specs on the setup:

**The Computer: **
HP Media Center m7060n
Pentium 4 3.0 Ghz
4.0 GB RAM
Detailed specs [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00306958&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

**The Display:**
Vizio 37" SV370XVT
Detailed specs [here]("http://www.vizio.com/sv370xvt.html#support")

**The Remote:** StreamZap PC Remote 

**The TV Signal:** 
Digital Cable with a set-top box from Service Electric Cablevision. I live in Bloomsburg, PA (United States). My current setup had the TV Signal coming directly from the wall into the tuner card with no pass-through of the cable box.

**The Confusion:**
I have many points of confusion, so I'm just going to lay them all out and ask some patient expert to help me work through them.
[LIST=1][*]First, what kind/brand/model of tuner card is right for me? I've been looking around and it seems that the Hauppauge WinTV-HVR-1600 is a solid bet for me, since it is PCI and has Digital and Analog capabilities. Is my understanding correct here? Or do I need a digital to analog converter box, or to do a set-top box pass-through?
[*]Second, what are the differences and distinctions between NTSC/ATSC/DVB/ClearQAM etc.? As I understand it, NTSC is the older analog standard, ATSC is the newer digital standard, but I have no idea what DVB is. Is my understanding correct here? Should I contact my cable provider to find out which signal they broadcast with?[/LIST]

I'm sure I'll have more questions based on anyones answers, so any and all help in understanding this mystifying world would be appreciated.

Thanks!

---

### Post by LowSky on 2011-03-08
1. the tuner card is completely up to you, just make sure its well supported. the 1600 is a bit old but will work fine.

2. NTSC is analog for north America, ATSC is digital, DVB stand for digital video broadcasting and is used when talking about different type like terrestrial, and satellite.  QAM is how the digital TV channels are sent to your TV without a cable box. The clear portion of the name means unlocked channels, usually just the local stations like ABC, NBC, CBS, FOX.


Now here is the easy part. If your PC has Ubuntu already on it all you need to do is install MythtV, and you can forget mythbuntu.

A few things before stepping onto the mythtv bus.

1. Windows 7 media center is amazing and much easier to set up, more tuner card support, and has no other fees involved past buying a copy of Windows 7 (OEM copy is $99 on newegg and amazon). Windows media center also supports playing Netflix streaming too.. just to put it out there.

2. If you do go with MythTV, you will need a membership to shedulesdirect.org and that is $20 a year. (5 years = cost of windows 7). all it does is give channel listings.

3. You will probably run into issues using mythtv at first. and maybe break it a few times before it works perfectly... that is my own results. yours may vary.

4. HD recordings take up 4-7GB of HD space. you will fill your hard drive quickly. plan accordingly!

5. you will need a graphics card for that system being a P4 I'm not sure if its PCIe or AGP, if its the latter your going to have issues playing HD video content (nvidia VDPAU is strongly recommended). to test try playing a HD video (720P or better) yahoo movie trailers. if it plays fine, then maybe you will be ok.

6. I suggest Windows 7 because I care about user expectations.

7. If you want to get all your HD cable channels to record you ill need your cable box connected something called a Haupauge HD PVR. otherwise if you just want a simple recording analog pass-through of the cable box will work. it will just look ugly.

8. hope this helps.

---

### Post by platticus on 2011-03-08
Thank you for the quick reply, you cleared up my confusion about the broadcast standards, mostly. Also I'd prefer to stick to linux if I'm upgrading components, but I could be convinced into a Win 7 install if the features were that much better. I don't currently do anything with HD, but it's a feature I could potentially grow into.

The next point of confusion that arises for me is the need or lack of need for a digital converter box for the HTPC. For my regular television needs, I have the digital cable box that has the guide and features and such. But with a HTPC (windows or linux) I'm unclear as to what channels I will be able to watch/record from a standalone connection from the wall. With the switch to ATSC I lost the ability to watch/record all but a few channels, and I'm wondering how this affects my choice of tuner card. Do I need to be concerned with QAM encryption(s) or does it not matter? Should I look at a digital converter box to get an analog signal at the expense of quality?

---

### Post by AKADAP on 2011-03-08
> **platticus said:**
> 
The next point of confusion that arises for me is the need or lack of need for a digital converter box for the HTPC. For my regular television needs, I have the digital cable box that has the guide and features and such. But with a HTPC (windows or linux) I'm unclear as to what channels I will be able to watch/record from a standalone connection from the wall. With the switch to ATSC I lost the ability to watch/record all but a few channels, and I'm wondering how this affects my choice of tuner card. Do I need to be concerned with QAM encryption(s) or does it not matter? Should I look at a digital converter box to get an analog signal at the expense of quality?

First go here: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/) type in your zip code and select your cable company.
This should give you a good idea of what channels are available in clear QAM on your cable system.

If any of the channels you want to watch/record do not show up on this list, you will need either an HDPVR + cable box, or the HDHomeRun Prime with cable card when it becomes available.

Otherwise pretty much any tuner card, USB tuner, or network tuner will work as long as it is capable of clear QAM.

A bit of clarification here: ATSC is a data format. 8VSB and QAM are modulation methods. 8VSB is used for all over the air broadcasts, and rarely a few stations on cable. QAM is used only on cable. Both 8VSB and QAM use ATSC formated data. (QAM is also used by your cable modem).

Windows Media Center is an appliance, MythTV is a hobby. With Windows Media Center, you are stuck with what Microsoft allows you to do. With MythTV, you have full control, but that means you must control everything yourself. You will not believe how much time you spend fiddling with MythTV. MythTV is not for every one, but neither is Windows Media Center.

---

### Post by platticus on 2011-03-08
Thank you very much for your informational reply. It also cleared up a lot of confusion for me, and the link you provided was something I never would have found on my own.

It seems my cable company transmits in QAM256. Does this mean that the channels are encrypted and not clear? If so, would a simple digital to analog converter box do the trick instead of replacing the card? If the digital to analog converter wouldn't do the trick, are capture cards capable of QAM256 going to be able to decrypt the signal and do everything I need to do?

---

### Post by newlinux on 2011-03-08
> **platticus said:**
> Thank you very much for your informational reply. It also cleared up a lot of confusion for me, and the link you provided was something I never would have found on my own.

It seems my cable company transmits in QAM256. Does this mean that the channels are encrypted and not clear? If so, would a simple digital to analog converter box do the trick instead of replacing the card? If the digital to analog converter wouldn't do the trick, are capture cards capable of QAM256 going to be able to decrypt the signal and do everything I need to do?

QAM256 is what most companies in the US use (some use QAM64 for some stations - my area does). It doesn't have any bearing on whether or not the station is encrypted. Best to check the silicondust link above to see what is free and clear in your area. No cards are going to decrypt the QAM signal. You'd need to investigate firewire with a cable box (not likely to work for everything or even anything in some place) or use the HD-PVR for Hidef. If you want SD recordings only, you could use an analog card to capture the input from one of the cable company's digital to analog boxes, but you'd need an IR blaster to change the channels on the box for scheduled recordings.

One more clarification - DVB is also a driver used by digital cards (ATSC/QAM) cards in addition to a format tv signals are broadcast in.

---

### Post by platticus on 2011-03-09
Again, thank you so much for the information. All of your replies are really clearing up a whole lot of confusion for me that Google searching didn't turn up because I had no idea where to start.

I did a little more digging and I came up with an article by my cable company, [this link]("http://readingeagle.com/article.aspx?id=160464"), that seems like they offer the converter box that I need. It seems I should contact them today to find out more. Perhaps this is what I need for recording SD analog channels?

I am very confused with all this IR blaster/IR transmitter etc stuff though. My cable box does have a jack for IR in, but I'm not sure how it works with the tuner card (my current tuner card doesn't have that functionality). How exactly does this IR blaster connect/function? Does it have any effect on the idea that I have a digital cable box that provides an onscreen guide and such?

---

### Post by newlinux on 2011-03-09
Your tuner card doesn't have to have IR blaster functionality, you can buy an IR blaster separately. Basically it sends and IR signal to your box to change channels, just like a remote control would. But you can configure mythtv to send the channel change command for when it needs to make sure the cable box is on the right channel to record. 

[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV)

---

### Post by rhpot1991 on 2011-03-09
If you mirror something similar to my setup it should work for you, hopefully all the links aren't too out of date:  [http://www.baablogic.net/drupal/node/13](http://www.baablogic.net/drupal/node/13)

I have Comcast cable, which won't be far off from your cable.  The combination of a HDHR + HDPVR will pick up all of your channels.  You use the HDHR for your locals, and it will give 2-5 tuners using multirec.  Then you use the HDPVR to record all the non local channels, you can either use your existing cable box or get a dedicated one to use.  While the HDPVR is using the cable box you will not be able to use it, so plan accordingly.  You could add more than one HDPVR if needed, but I would try to hold out with one until the CableCard tuners are readily available and have a look at them then.

---

### Post by newlinux on 2011-03-09
> **rhpot1991 said:**
> If you mirror something similar to my setup it should work for you, hopefully all the links aren't too out of date:  [http://www.baablogic.net/drupal/node/13](http://www.baablogic.net/drupal/node/13)

I have Comcast cable, which won't be far off from your cable.  The combination of a HDHR + HDPVR will pick up all of your channels.  You use the HDHR for your locals, and it will give 2-5 tuners using multirec.  Then you use the HDPVR to record all the non local channels, you can either use your existing cable box or get a dedicated one to use.  While the HDPVR is using the cable box you will not be able to use it, so plan accordingly.  You could add more than one HDPVR if needed, but I would try to hold out with one until the CableCard tuners are readily available and have a look at them then.

If he is planning on getting a cable company's basic digital to analog box, most likely it won't have component out for use with the HDPVR. The ones they give out here only have RF (coaxial) out. If he's not interested in HD, HD-PVR probably isn't the right solution.

That said, my setup is similar to yours. I have an HD-PVR connected to one set top box for premium and encrypted channels and use QAM tuners for all other recordings.

---

### Post by platticus on 2011-03-10
> **rhpot1991 said:**
> If you mirror something similar to my setup it should work for you, hopefully all the links aren't too out of date:  [http://www.baablogic.net/drupal/node/13](http://www.baablogic.net/drupal/node/13)

I have Comcast cable, which won't be far off from your cable.  The combination of a HDHR + HDPVR will pick up all of your channels.  You use the HDHR for your locals, and it will give 2-5 tuners using multirec.  Then you use the HDPVR to record all the non local channels, you can either use your existing cable box or get a dedicated one to use.  While the HDPVR is using the cable box you will not be able to use it, so plan accordingly.  You could add more than one HDPVR if needed, but I would try to hold out with one until the CableCard tuners are readily available and have a look at them then.

wow, that is one awesome looking setup!

Thank you both for the input, you've all helped tremendously in furthering my understanding of what all these things mean and the distinctions between them. In it's eventuality, I would like to build a setup similar to what rhpot1991 and newlinux are showing, but right now money is too tight for that, unfortunately. 

It sounds like a standard, and free mind you, digital to analog converter from my cable company will work with my current setup while I save the money to build a much more expansive and beautiful system like the ones you describe. Is my logic sound, and with the converter, it should work?

---

### Post by klc5555 on 2011-03-10
> **platticus said:**
> wow, that is one awesome looking setup!

Thank you both for the input, you've all helped tremendously in furthering my understanding of what all these things mean and the distinctions between them. In it's eventuality, I would like to build a setup similar to what rhpot1991 and newlinux are showing, but right now money is too tight for that, unfortunately. 

It sounds like a standard, and free mind you, digital to analog converter from my cable company will work with my current setup while I save the money to build a much more expansive and beautiful system like the ones you describe. Is my logic sound, and with the converter, it should work?

It will work fine. The only trick will be to get a serial or USB IR blaster that works on your machine, and configure LIRC so that mythtv will be able to change the channels on your digital to analog converter box.

---

### Post by rhpot1991 on 2011-03-10
> **platticus said:**
> wow, that is one awesome looking setup!

Thank you both for the input, you've all helped tremendously in furthering my understanding of what all these things mean and the distinctions between them. In it's eventuality, I would like to build a setup similar to what rhpot1991 and newlinux are showing, but right now money is too tight for that, unfortunately. 

Best way to go about it is one step at a time.  Add individual pieces as you have the time/money and you can expand into a nice setup without dropping so much cash all at once.  I'd recommend looking at the [HDHR]("http://www.amazon.com/gp/product/B004HO58SO/ref=as_li_ss_tl?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B004HO58SO") when you have a chance, its very cheap cost per tuner and should cover all your local channel recordings all by itself.

P.S. note that its cheaper from amazon directly but is apparently on a 1-3 week backorder, so that link is currently displaying a more expensive 3rd party that has it in stock.

---

### Post by newlinux on 2011-03-10
> **rhpot1991 said:**
> Best way to go about it is one step at a time.  Add individual pieces as you have the time/money and you can expand into a nice setup without dropping so much cash all at once.  I'd recommend looking at the [HDHR]("http://www.amazon.com/gp/product/B004HO58SO/ref=as_li_ss_tl?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B004HO58SO") when you have a chance, its very cheap cost per tuner and should cover all your local channel recordings all by itself.

P.S. note that its cheaper from amazon directly but is apparently on a 1-3 week backorder, so that link is currently displaying a more expensive 3rd party that has it in stock.

yeah, I started off with one computer and one tuner. Then, through my used PC parts store nearby, ebay, some new parts here and there, castoffs from friends, I eventually built the behomoth that is in my "My Hardware" link in my sig. This is all probably over the course of about 5 years. Basically with Linux older hardware just seems to keep on ticking just fine for years if it doesn't fail.

---

### Post by platticus on 2011-03-11
Thank you all again for the replies, I now understand a great deal more and all my queries are answered.

---

