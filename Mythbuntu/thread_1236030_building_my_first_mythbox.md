---
title: "building my first mythbox"
date: 2009-08-09
forum: Mythbuntu
---

### Post by benlyboy on 2009-08-09
Hi all

Well I'm about to do it, Build my first myth box that is.

I wanted to get the advice of those with more experience than I. So before I buy any parts I thought I would list what I was looking at buying and see if anyone could see any reason why they wouldn't make a good system for Mythbuntu.

[HTML]Motherboard       ASUS M3N78-EM AM2+/AM2        (CAN GET A DEAL ON THIS)
CPU               AMD Athlon 64 X2 6000 
Memory            G.SKILL 4GB (2 x 2GB) 240-Pin
Harddrive          Seagate Barracuda 500GB SATA  (ALL READY HAVE THIS)
CD Drive           LG DVD burner SATA            (ALL READY HAVE THIS)
Tuner              Hauppauge WinTV-HVR-2250 
Case               nMEDIAPC 1000B Micro ATX [/HTML]
 
THANKS FOR ANY ADVICE :)

---

### Post by lionsnob on 2009-08-09
Hello -

Looks good from here!  The only thing I would change is the tuner.  Are you planning on using QAM or OTA?  I highly recommend the HDHomeRun.  I used to struggle with the PCI cards (pcHDTV 5500 and Pinnacle 800i).  It wasn't that it was hard to get them to work, just the hassle of the cards finding the signal.  It is $35 more, but well worth it IMO.  This was OTA (ATSC) by the way.  QAM may be easier to tune.

---

### Post by NautiusMaximus on 2009-08-10
You might want to consider a bigger hard disk, or a second hard disk if your case has room.

If you start recording TV programmes, you would be amazed how quickly a hard disk will fill up. I've had my Mythbuntu machine working since about January, and I think I've already used about 500 GB of disk space.

---

### Post by benlyboy on 2009-08-17
Thanks for the input 
I am worried about the HD (hard drive) not being big enough but as I already own it so I will make do for now. I may in time add a second HD or even another back end, who knows:)

As for the tuner I may have to rethink this any how, as I have been doing some research and I'm not sure that this card is supported fully in Linux. As I am quite new to both Linux and Mithtv I would like my first build to be something that will work right out of the box.

I would be interested in hearing any ideas on what tuner cards might be a good pick for this project.

I should tell you how I will be using this box, as it may help with what you think I should be using.

My plan is to hook the box directly to the cable as 70 odd channels are available as an analog signal straight off the cable. The remaining 15 or so channels of which I may watch 4 now and then are digital and I believe encrypted and would have to go through a cable box. so at least in the beginning I may not worry about hooking up to them.  

any ides...?

---

### Post by epi 1:10,000 on 2009-08-18
the HVR-2250 works you just need to install the driver yourself usin LowSky's tutorial.

[http://ubuntuforums.org/showpost.php?p=7429560&postcount=47](http://ubuntuforums.org/showpost.php?p=7429560&postcount=47)

The HVR-1250 is cheaper and supported in the kernel but it is only 1 tuner.  I never tried the HD Homerun but why not get both.  MythTV is all about tacking that learning curve, getting your but kicked and going back for more.  If your persistent you will beet that computer into submission and get it to do what you want it to do. Don't Tap to that 15lb hunk of junk.

---

### Post by benlyboy on 2009-08-18
My only worry with using the HVR-2250 is that the beta driver only works on the digital side of the tuner.  Though I do believe that the lower 70 channels maybe Simulcasting in digital as well as analog.  I don't know this for sure, and I don't know if they are encrypted. If they are I would have to use a cable box. 
so I am thinking I would be better off with a tuner with analog Capabilities.

---

### Post by epi 1:10,000 on 2009-08-18
My only experience w/ analog is the HVR-1600 ant that picks up all the rf interference from all the other junk in my case causing picture distortions on analog capture.  Maybe an eternal usb analog mpeg encoder would help minimize rf interference. 
HVR-1950 or some other MythTV compatible capture device?  

P.S.  Al my digital channels are encrypted on TWC except for the discovery channel SD and the local channels.

---

### Post by ahood on 2009-08-19
I have three Hauppauge analog cards (PVR 150, 250 and 500). Although no longer available in retail, OEM the PVR 150 and 500 can still be purchased. If you live in the US, I can recommend a webstore where one can be purchased. I am currently using Mythbuntu 8.04 and these cards work out of the box.

---

### Post by benlyboy on 2009-08-19
Hi 

I would be very interested in knowing where you can still buy PVR 150 and 500 cards.

I am also looking at the HVR 1600 as it looks as if this has worked for others. The only down side to this card is, that even though it is a dual tuner, one is analog and the other digital so I would most likely not use half the card most of the time. The thing is that the motherboard I'm using only has 2 pci slots this limits me to two tuner cards. Thats what first drew me to the HVR-2250. It has two tuners both of which can be analog, this would allow me to have up to four tuners in my system. but the beta drivers don't support the analog function of the card.:(

---

### Post by ahood on 2009-08-20
About two months ago, I purchased an OEM version of a Hauppauge PVR 500 (dual tuners) from [[COLOR="Blue"]**Compuvest**[/COLOR]](http://www.compuvest.com). It was shipped without a retail box, but did include a mini cd, the latter which I didn't use. The card worked as expected. If you live in the US, this might be an option.

---

### Post by benlyboy on 2009-08-22
Hi

 Thanks for the advice,have ordered a pvr 500 from Compuvest the one card will give me two tuners and if I want I still have room to add another later

---

### Post by surfzombie on 2009-08-30
O.K. now I am  a little confused as to what I need.  I to want to build an HTPC and use Linux and have been looking for a tuner card that will work in linux.  I found this thread doing a search for tuner cards.  I have an old analog tv that I want to hook it up to for now and plan on upgradeing to an hdtv/lcd monitor later down the road as funds permit.  What would be my best option?  I thank you for any light you can shed on this matter.  Also  I am confuse on the ATSC and NTSC.  Do I need both for just the Free-to-air channels in the USA?

---

### Post by larsolav on 2009-08-31
> **surfzombie said:**
> O.K. now I am  a little confused as to what I need.  I to want to build an HTPC and use Linux and have been looking for a tuner card that will work in linux.  I found this thread doing a search for tuner cards.  I have an old analog tv that I want to hook it up to for now and plan on upgradeing to an hdtv/lcd monitor later down the road as funds permit.  What would be my best option?  I thank you for any light you can shed on this matter.  Also  I am confuse on the ATSC and NTSC.  Do I need both for just the Free-to-air channels in the USA?

If you are only going to capture free over the air signals then all you need is ATSC tuner cards. It does not matter that you will be using it on an old analog TV for now, as long as your video card has an output that will work on the TV (most likely composite video depending on the age of your TV). 
Good luck!

---

### Post by surfzombie on 2009-08-31
> **larsolav said:**
> If you are only going to capture free over the air signals then all you need is ATSC tuner cards. It does not matter that you will be using it on an old analog TV for now, as long as your video card has an output that will work on the TV (most likely composite video depending on the age of your TV). 
Good luck!

Do you mean then that my video card needs to have a composite tv out or an s-video port to work with the older tv?

---

### Post by larsolav on 2009-08-31
> **surfzombie said:**
> Do you mean then that my video card needs to have a composite tv out or an s-video port to work with the older tv?

Yes. At least most likely. How old is the TV and what inputs does the TV have? It needs to have at least a composite tv input. Many video cards have S-video out, and you can always get an s-video to composite plug if your TV does not have a s-video input (my first TV I used with Mythbuntu had only composite in and my video card S-video out, I used the plug I mentioned).

---

### Post by surfzombie on 2009-08-31
> **larsolav said:**
> Yes. At least most likely. How old is the TV and what inputs does the TV have? It needs to have at least a composite tv input. Many video cards have S-video out, and you can always get an s-video to composite plug if your TV does not have a s-video input (my first TV I used with Mythbuntu had only composite in and my video card S-video out, I used the plug I mentioned).

Thanks for your help!:guitar::guitar::P:P

---

### Post by benlyboy on 2009-09-01
Hi 

Just one more question, It's about my choice of motherboard (ASUS M3N78-EM AM2+/AM2) I chose it as it had on board video with a HDMI out. It has the NVIDIA GeForce 8 series chipset, and what I want to know is should I be able you use the onboard video and its HDMI port under Mythbuntu?

---

### Post by larsolav on 2009-09-02
> **benlyboy said:**
> Hi 

Just one more question, It's about my choice of motherboard (ASUS M3N78-EM AM2+/AM2) I chose it as it had on board video with a HDMI out. It has the NVIDIA GeForce 8 series chipset, and what I want to know is should I be able you use the onboard video and its HDMI port under Mythbuntu?

Yes. And with the new Mythbuntu version 9.10 you will be able to use VDPAU with it too!

---

### Post by HobbDogg on 2009-09-02
I too am looking into building a Mythbuntu box to record TV as well as second has a media server. What I am running into in my research is that all of the tuner cards only receive unencrypted clear QAM channels, or OTA HD channels. If i have an HD tv should I even bother with building the pause/play/record functionality into the box if i run the risk of only being able to watch 3 to 4 HD channels? My ultimate goal is to be able to record off of the cable company's HD box that is provided (Charter Communications). Is there any input on this? Anything is appreciated.

---

### Post by HobbDogg on 2009-09-03
*wrong reply*

---

### Post by benlyboy on 2009-09-03
ok thanks for the info
I will go ahead and order my motherboard. I don't know to much about VDPAU, can someone give me a link or info on why I might want to use it

---

### Post by SiHa on 2009-09-04
Essentially VDPAU will enable you to playback HD video with the decoding done in hardware by the Nvidia chipset, relieving your CPU of the task.

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

---

### Post by hackmeister on 2009-09-04
> **benlyboy said:**
> ok thanks for the info
I will go ahead and order my motherboard. I don't know to much about VDPAU, can someone give me a link or info on why I might want to use it

[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

---

### Post by benlyboy on 2009-09-04
ok thanks again for all the info 

I will go ahead and order the motherboard cpu and ram to finish my mythbox.
I do have one more question, that is how far off is Mythbuntu 9.10 and should I wait for it?

---

### Post by williammanda on 2009-09-06
Mythbuntu releases are on the same schedule as ubuntu. They are released twice a year on April & October hence the version number 9.10. Where 9 is the year and 10 is the month.
Thanks

---

