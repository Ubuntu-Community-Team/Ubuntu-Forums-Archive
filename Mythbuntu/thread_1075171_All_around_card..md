---
title: "All around card."
date: 2009-02-20
forum: Mythbuntu
---

### Post by Tuxaby on 2009-02-20
I find it very confusing trying to decipher which type of tuner card I need.  It would be nice if the manufacturer used laymen terms to describe a products abilities for those of us not so savvy individuals.  
It needs to be  capable of receiving signals from cable, any type satellite dish (KU, Direct, etc), and OTA HD antenna.  Preferably hardware type, and come with a remote (RF type if available).  I currently have Dish tv w/DVR and it has a RF remote which makes it very convenient when we need to control it from another room as everything is networked throughout the house. I intend to use Mythbuntu on a dedicated computer with these hardware specs,  AMD 64 bit 3800 Dual core, 2 gig ram, and ATI HDMI graphics w/minimum 512 MB memory, 300 to 500 gb hard drive, and good quality Blueray DVD Recorder.  Any way, any and all recommendations will be greatly appreciated.   Thanks in advance, Lee

---

### Post by ian dobson on 2009-02-20
Hi,

I would recommend using a NVidia graphic card, rather than ATI. The ATI linux drivers aren't that good at the moment. Maybe it'll change sometime in the future.

Blueray could be a problem due to the DRMS (Digital Rights management system) that limits what you can do with the disks that you've purchased.

With regards to tuners have a look at [www.linuxtv.org](www.linuxtv.org).


Regards
Ian Dobson

---

### Post by theophile on 2009-02-20
Here's some things to help you make a decision.
Cable signal is called QAM. In mos areas, the cable companies encrypt all the QAM data except the local network channels so you will only be able to receive unencrypted or "clear QAM" signals with a QAM tuner.

AFAIK, there's no card that will pull a signal from your satellite in the same manner as the Dish STB, but I know a lot of people have connected the s-video output from their STB to an NTSC tuner card. You can then use an ir blaster to allow MythTV to emulate the STB remote control and change the channel on the STB by itself. I seem to recall also that some satellite STBs can be controlled via serial cable.

OTA HD is called ATSC. Any ATSC tuner should be able to pick up these signals, but more than likely, anything you can get over the air is also available in clear QAM. Since you don't have to have your cable pointed in exactly the right direction, it's much less frustrating to just use cable and forget about that awful antenna. Also, even if you did want to use both, the cable and the antenna would need the same coax jack on the tuner.

Long story short, any QAM/ATSC/NTSC card that is supported in Linux should do the trick for you, and there are plenty. See a list here:
[http://www.mythtv.org/wiki/Video_capture_card#ATSC_Cards_.28only_in_US.2FCanada_.29](http://www.mythtv.org/wiki/Video_capture_card#ATSC_Cards_.28only_in_US.2FCanada_.29)

There are a lot more too. If you see a card you like and you know it works in Linux, 95% of the time it will work in MythTV fine.

And I second the nVidia recommendation.

---

### Post by Tuxaby on 2009-02-20
Thanks ian dobson and theophile for the excellent information.   Been with ATI since I began computing since they are local to the Austin, Tx area I live near.  I believe in supporting the local economy.  Been wanting to try the Nvidia, so I will and  and see how it goes.  I can always swap cards if I see a need.     Blueray, I wasn't thrilled about it anyway.    Think I will stick with what I know works.   Many thanks, this is a great beginning.   Will keep progress posted.      Lee

---

### Post by newlinux on 2009-02-20
I will third nvidia and get a VDPAU capable card if you are buying new.
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

One more point about unencrypted QAM - sometimes you can get more than just the locals. I now get my HD locals plus all the same channels I would get with basic cable plus a few extras - including my digital music stations. This varies from provider to provider (and even from region to region with the same provider). I agree that all you should expect are your HD locals - which would be the same channels as you can get OTC ATSC - but I just thought you might want to know there is the possibility of getting more than just the HD locals via unencrypted QAM.

A place to check what is available via unencrypted QAM is AVSforum (look for a local forum for your cable provider) or if you have an HDTV with a QAM capable tuner, you can just do a scan and see what digital stations you get, or you can try:

[http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels)


Also, for satellite capture, you can also look into the Hauppage HD-PVR, but the drivers are still new... - but this allows for HD quality capture from a satellite set top box.

---

### Post by Tuxaby on 2009-02-24
Thanks newlinux,   More good and needed info.  I glanced over the Wiki which raised a question.  I intend to use Mythbuntu, does it have VDPAU built in , or should I just compile MythTV on a Ubuntu installation.  I haven't decided on hardware yet but will soon.  Thanks Lee

---

### Post by newlinux on 2009-02-24
> **Tuxaby said:**
> Thanks newlinux,   More good and needed info.  I glanced over the Wiki which raised a question.  I intend to use Mythbuntu, does it have VDPAU built in , or should I just compile MythTV on a Ubuntu installation.  I haven't decided on hardware yet but will soon.  Thanks Lee

No, VDPAU won't be officially supported until myth .22 comes out, so mythbuntu doesn't come with the version of myth with VDPAU support. However, you don't have to compile your own either. Stable VDPAU enabled .21 myth packages exist in a 3rd party repo:

This post is by the creator of those packages and explains all about how to install them:

[http://ubuntuforums.org/showpost.php?p=6743278&postcount=14](http://ubuntuforums.org/showpost.php?p=6743278&postcount=14)

You'll also have to install the latest (or a very late) version of the nvidia drivers.

---

### Post by Tuxaby on 2009-03-27
Still gathering information and have a new question. I keep reading about a cards ability to read only unencrypted satellite signals.  Not sure I understand the concept.   Does this mean that taking the output from the subscribed satellite receiver does not allow you to record any channel received only  channels such as your local TV channels can be recorded?  Or are you able to receive and record all channels received on a subscribed satellite receiver?  Will start to obtain hardware soon and want to try to prevent any or at least as few surprises as possible.  Thanks again,  Lee

---

### Post by newlinux on 2009-03-27
> **Tuxaby said:**
> Still gathering information and have a new question. I keep reading about a cards ability to read only unencrypted satellite signals.  Not sure I understand the concept.   Does this mean that taking the output from the subscribed satellite receiver does not allow you to record any channel received only  channels such as your local TV channels can be recorded?  Or are you able to receive and record all channels received on a subscribed satellite receiver?  Will start to obtain hardware soon and want to try to prevent any or at least as few surprises as possible.  Thanks again,  Lee

I don't know of any tuner cards that pull encrypted or unencrypted signal from satellites. Unless you hack the satellite box, you will have to capture from one of the video outputs of the satellite box (most likely the component with the Hauppage HD-PVR if you want true HD quality, or S-video for SD quality - many cards can capture from S-video). So if you  capture from the satellite (or any set top) box output, you can capture  every station your satellite box can tune, but you'll need to Hauppage HD-PVR (and the drivers are still under development, but can be made to work if you want to deal with that for now) to capture in HD quality.

With digital cable (unencrypted QAM) you will only be able to get whatever the cable company sends over the wire unencrypted digitally - and that varies widely. what I've seen mostly is that people get the locals (in HD as well) and a smattering of other channels. I personally (for now it has changed a couple of times) get all those stations and all expanded basic stations as well (basically 1-99) via unencrypted QAM. If you are going the unencrypted QAM route, you will want to verify what stations your cable company (in your area - they vary from area to area) makes available via unencrypted QAM. Any stations they don't will require a set top box to capture the signal, just like with the satellite box.

---

### Post by Tuxaby on 2009-04-10
Ikeep coming up with new questions.  The terms "front end and back end".  I assume back end is the tuner card and the front end is the video card.  Also, do I need two video cards to be able to use the lcd monitor and send signal to the television without having to swap everything each time?  Or, since I have a Diamond 3450 card with HDMI, DVI, and VGA outputs can I just use these for both.  DVI for monitor and HDMI for TV.   Im going to order a Nvidia video card to solve the driver problems and will duplicate these outputs if this will work. I also want to thank newlinux for all your help.   Lee

---

### Post by AboveTheLogic on 2009-04-10
> **Tuxaby said:**
> Still gathering information and have a new question. I keep reading about a cards ability to read only unencrypted satellite signals.  Not sure I understand the concept.   Does this mean that taking the output from the subscribed satellite receiver does not allow you to record any channel received only  channels such as your local TV channels can be recorded?  Or are you able to receive and record all channels received on a subscribed satellite receiver?  Will start to obtain hardware soon and want to try to prevent any or at least as few surprises as possible.  Thanks again,  Lee

> **newlinux said:**
> I don't know of any tuner cards that pull encrypted or unencrypted signal from satellites.

Oh, they exist! DVB-S tuners.

There are ways to use the card you get from your provider (I don't know if it works for DirecTV but heard it does from Dish Network and Bell in canada) in your PC to decrypt the signal with a PC. I haven't done it myself but have read about many people who have. It can be done with a networked dreambox which I believe is supported by mythtv.

---

### Post by newlinux on 2009-04-10
> **Tuxaby said:**
> Ikeep coming up with new questions.  The terms "front end and back end".  I assume back end is the tuner card and the front end is the video card.  Also, do I need two video cards to be able to use the lcd monitor and send signal to the television without having to swap everything each time?  Or, since I have a Diamond 3450 card with HDMI, DVI, and VGA outputs can I just use these for both.  DVI for monitor and HDMI for TV.   Im going to order a Nvidia video card to solve the driver problems and will duplicate these outputs if this will work. I also want to thank newlinux for all your help.   Lee

Back end machines usually (but not always) contain tuner cards. They handle recording, serving up recordings to frontend machines, job processing (such as commercial flagging and transcoding), etc. Frontends (which can be on the same machine as backends) connect to a master backend and allow the user to view recordings (including liveTV) from any of the master and slave backends as well as viewing pictures, weather, videos, music, etc... They also allow you schedule recordings and do other configuration.

[http://www.mythtv.org/wiki/User_Manual:Introduction#MythTV_Configurations](http://www.mythtv.org/wiki/User_Manual:Introduction#MythTV_Configurations)

May help.

You don't necessarily need two video cards to have a dual-headed output. Most cards to can do this. I have this setup (one card connected to CRT monitor and TV) going on one of my machines, using one X server and 2 displays (not using twinview or xinerama). More info:

[http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed](http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed)

> Oh, they exist! DVB-S tuners.
I didn't realize those cards worked with US Satellite companies. I wonder how much of pain (and how legal) it is to get them working... I may look into it.

---

### Post by AboveTheLogic on 2009-04-10
Yeah, Dish Network uses the DVB standard, same as they use in Europe. DirecTV uses DSS, and there are a few cards out there that will handle those as well.

---

### Post by Tuxaby on 2009-04-14
I've decided to build upon the computer I list in my signature to save time and money.    I want to use the  Hauppauge WinTV-HVR 1800 MCE Kit ([http://www.newegg.com/Product/Product.aspx?Item=N82E16815116015](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116015)) I chose this card because as I understand it can use the signal from either a  DishTV or DirecTV  receiver via the s-video input.  If so this is a all around card.      Also need to choose the best Nvidia video card from those I have narrowed it down to .  I found these cards have the hookups I require, Gigabyte GV-N95TOC-1GI GeForce9500 GT ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814125261](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125261)), the Jaton Video-PX9400GT-EX Geforce 9400 GT ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814139039](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139039)), or the EVGA 512-P2-N738-LR GeForce 8400 GS ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130313](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130313)). My choice is the Gigabyte.   I believe all are  VDPAU capable.  If any or all these are bad choices, let me know.  Also will I have any problems because the motherboard is ATI based?

I Also don't know which packages (preferably Mythbuntu) to install from Synaptic, so a little guidance will be very appreciated.   And, since I will have a lot to learn and set up I will leave VDPAU until it comes out in the official release package.
   If I am sucessful with this unit, I will then set  up my network with a backend server.  
   But for now, baby steps.   Any additional advice that will simplify this process will be appreciated.

---

### Post by newlinux on 2009-04-15
You shouldn't have problems using the nvidia card on an ATI IGP board (do you have an ATI video card in there or is it an IGP?). You may need to disable to onboard video to get the nvidia card working. If it is an ATI video card in there, there shouldn't be a problem switching. The 8400GS are popular and inexpensive, but you might want to look into a fanless one for noise reasons. Also make sure it is g98.

A number of ways to install mythtv in ubuntu. One way is just install the mythbuntu-control-centre and then run it and configure everything from there. Another way is to install the mythbuntu-desktop package. You could still use MCC to configure things.

---

### Post by Tuxaby on 2009-04-15
Good morning newlinux.  I knew you would get back to me. I found this card, Sparkle SPFX 95GT1024U2H GeForce 9500 GT **(**http://www.newegg.com/Product/Product.aspx?Item=N82E16814187034>).    Do you see any problems with it? Don't know how to identify  what a g98 is.   The ATI card is on board and  the PCIe  ATI card will be replaced with the Nvidia.  Thought I would use the onboard for the monitor if there was no conflict.   Can run without it as long as the Nvidia can run both monitor and TV simultaneously.   
    Does the mythbuntu-desktop package come with MCC or will I need to install it separately?  And shouldn't I wait to install the software until after all hardware is installed?   
   Your help is very much appreciated.  You make doing this much easier than it would have been on my own.   Many thanks, Lee

---

### Post by newlinux on 2009-04-15
Honestly the only vid cards I know a bit about are the 8400GS, because I was looking into buying them myself. (My most up to date card is a 7100!!!). But, that 9500 GT. It uses GDDR2 RAM, at that price range you might want to look for GDDR3 RAM. There have got to be a lot more people here who know tons more about the newer vid cards than I do...

If the ATI works you can stick with it, but the Linux drivers aren't as good for ATI (don't have nearly the same support for hardware acceleration) and myth typically struggles with ATI. 

mythbuntu-desktop does install MCC. I would wait for the hardware before installing.

---

### Post by Tuxaby on 2009-04-15
Appreciate the info.  Will research the vid card a little more.   Thanks again newlinux,  Lee

---

### Post by newlinux on 2009-04-15
Good luck. Wish I knew more to help with the vid cards. Let us know how it goes...

BTW, which build are you going to go with for mythbuntu? 8.04, 8.10, or 9.04? Just curious. Most of my machines are 8.04, but a couple are 8.10. I like the long term support since I don't plan on fiddling with my backends much until myth .22 comes out... but for some hardware you may need newer kernels (all my hardware is old).

---

### Post by nickrout on 2009-04-15
> **Tuxaby said:**
> 
I Also don't know which packages (preferably Mythbuntu) to install from Synaptic, so a little guidance will be very appreciated.   And, since I will have a lot to learn and set up I will leave VDPAU until it comes out in the official release package.
   If I am sucessful with this unit, I will then set  up my network with a backend server.  
   But for now, baby steps.   Any additional advice that will simplify this process will be appreciated.

First preference is to do a fresh install from the mythbuntu live cd, but you may not want to trash the present system. It will however give you a neat and tidy system.

second choice, on an existing ubuntu system, install the mythbuntu-desktop package:

```
sudo aptitude install mythbuntu-desktop
```

That will drag in all the rest of what you want.

After that go through the instal  instructions and get it all set up and working.

Lastly you want to update to the latest 0.21-fixes so you get all thats been fixed since ubuntu last released. You have two choices:

1. if you want vdpau, go to [http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html) and follow the instructions.

2. However if you don't want vdpau you want to update from the weekly 0.21-fixes builds which are usually accessible from [http://www.mythbuntu.org](http://www.mythbuntu.org). (but the site is largely down at the moment, so wait a day or 2)

---

### Post by Tuxaby on 2009-04-21
Installed a Hauppauge WINTV HVR-1800 and replaced the ATI video card with a EVGA e-GeForce 9500 GT w 1 gig memory.  Installed Mythbuntu 8.1 and I'm now looking for a setup how to for the Hauppauge.   Will post the results.
        [COLOR=Blue] I foung out that 9.04 comes ready for my TV card.  So, today I downloaded it and installed it and am waiting on it to finish updating before starting setup.  More Later.[/COLOR]

---

