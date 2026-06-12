---
title: "Tuner that will recieve cable IRC analog?"
date: 2011-11-06
forum: Mythbuntu
---

### Post by sbrown7792 on 2011-11-06
i recently bought a Hauppauge 1250 for my media server box, and after running mythtv setup, could not get all of the channels that the tv would get. I emailed the campus techs and they say their system is "an IRC analog system" and that they do not encrypt anything. Since I've heard the 1250 doe not support analog, I assume this is why I cannot receive these channels. I cannot find any documentation on any tuner that will receive this using linux, i only get stuff like it supports analog (ntsc), but makes no mention of analog cable (unless in my noobishness i don't know that they are the same thing). SO my question is is if there is a tuner that will pick up ntsc signals on linux, will it pick up the analog irc cable? If so, any recommendations (the cheaper the better)? 
Thanks so much and sorry for my noobishity.

this is on ubuntu 10.04 LTS with mythtv running as a backend and frontend

---

### Post by klc5555 on 2011-11-07
> **sbrown7792 said:**
> i recently bought a Hauppauge 1250 for my media server box, and after running mythtv setup, could not get all of the channels that the tv would get. I emailed the campus techs and they say their system is "an IRC analog system" and that they do not encrypt anything. Since I've heard the 1250 doe not support analog, I assume this is why I cannot receive these channels. I cannot find any documentation on any tuner that will receive this using linux, i only get stuff like it supports analog (ntsc), but makes no mention of analog cable (unless in my noobishness i don't know that they are the same thing). SO my question is is if there is a tuner that will pick up ntsc signals on linux, will it pick up the analog irc cable? If so, any recommendations (the cheaper the better)? 
Thanks so much and sorry for my noobishity.

this is on ubuntu 10.04 LTS with mythtv running as a backend and frontend

According to the Mythtv/LinuxTv wiki (and the Hauppauge product page), the 1250 does support analog: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)  using the standard cx18 driver (already in your kernel).

You might wish to try setting up a second Video Source in your backend setup for the analog channels, and setting up the analog half of your card (which the backend should locate at /dev/video0) as an MPEG encoder (not "V4l analog") in the Capture Card setup. Then binding your new analog Video Source to this analog tuner at /dev/video0 in Input Connections, and scanning (or adding analog channels to this Video Source manually in Channel Editor) should get things operating. The digital input and the analog input should likely be associated into a single recording group, since the card can't record from both digital and analog simultaneously through it's single cable input.

No additional hardware necessary. Can't get much cheaper than that.

---

### Post by poe503 on 2011-11-08
> According to the Mythtv/LinuxTv wiki (and the Hauppauge product page), the 1250 does support analog: [http://linuxtv.org/wiki/index.php/Ha...WinTV-HVR-1250](http://linuxtv.org/wiki/index.php/Ha...WinTV-HVR-1250) using the standard cx18 driver (already in your kernel).

You must be thinking of a different tv card.  You do give a link to the 1250 page but it says right at the outset: "(Note: Analog support is not implemented yet)".  Farther down the page: "? (tuner for analog ... likely a NXP/Philips TDA18271)".  The page has been like this for several years.


Linux support for the 1250 does not include analog in my Mythtv setups.

---

### Post by klc5555 on 2011-11-08
> **poe503 said:**
> You must be thinking of a different tv card.  You do give a link to the 1250 page but it says right at the outset: "(Note: Analog support is not implemented yet)".  Farther down the page: "? (tuner for analog ... likely a NXP/Philips TDA18271)".  The page has been like this for several years.


Linux support for the 1250 does not include analog in my Mythtv setups.

Sorry, my bad. Looks like you're right. My belief that the cx18 also currently supported the analog half of the 1250 was unfounded.

The OP has several choices for analog cards. Possibly least expensive would be to pick up an older used Hauppauge 1600 on Amazon or e-bay or some such, or a used Hauppauge PVR 150, of which there are still many floating around. The 150 is analog only; the 1600 dual tuner  digital and analog. But I believe the 1600 might need to be a replacement for the 1250 rather than a supplement --there appears to be some traffic on the Mythtv lists to the effect that some users are having trouble getting the 1250 and 1600 to share the cx18 driver nicely.

---

### Post by sbrown7792 on 2011-11-08
Thank you all for your replies. I was indeed planning on getting a replacement rather than a supplement if I could (I'm still in the return window for this 1250). I looked into the MPEG encoder option in the mythtv setup just to be sure, but as expected it wasn't there. I will look into the 1600 and getting this one returned. As far as getting the analog signal, if the 1600 will pick up analog signals, does that automatically include IRC analog? I would assume so (but you know what they say about assuming), but whenever I hear people talking about analog support they are always talking about OTA NTSC signals, and I have no clue if its the same basic function. 

Thanks so much!

---

### Post by poe503 on 2011-11-08
Yesterday I installed a 3rd card in one of my Mythtv setups.  I couldn't use another 1250 because of the lack of pci-e slots so I put in an Avermedia A180 card which is pci. 

It is well supported by Ubuntu on both the analog and digital side.  The only glitch was that I had to download it's NXT2004 firmware and put that in /lib/firmware or the card wouldn't successfully scan for channels.  This was for the 09.04 version of Ubuntu.  It may not be necessary to do this for newer versions.

The A180 digital video quality and signal strength are identical to the 1250.

Sorry but I don't know about IRC cable other than it is an option in Mythbackend for channel scanning.

---

### Post by klc5555 on 2011-11-09
> **poe503 said:**
> Yesterday I installed a 3rd card in one of my Mythtv setups.  I couldn't use another 1250 because of the lack of pci-e slots so I put in an Avermedia A180 card which is pci. 

It is well supported by Ubuntu on both the analog and digital side.  The only glitch was that I had to download it's NXT2004 firmware and put that in /lib/firmware or the card wouldn't successfully scan for channels.  This was for the 09.04 version of Ubuntu.  It may not be necessary to do this for newer versions.

The A180 digital video quality and signal strength are identical to the 1250.

Sorry but I don't know about IRC cable other than it is an option in Mythbackend for channel scanning.

Watch out when buying  an "Avermedia A180" for this purpose: there are two varieties. The older version includes an analog tuner; the newer version is digital only. 

I own both and have used both versions, but I don't use them any longer. I kept finding that on random occasions their digital tunes with high bitrate errors, and the resultant recording (or live tv) suffers from "popping" and generally degraded audio. Next tune would be perfect. Never did find a solid cause for this odd behavior. It happened rarely-to-occasionally on the 2.6.27.7 kernel that I originally installed them on, but became much more frequent with more recent kernels (i.e. 2.6.34.4 and later). Tried them both in a couple of machines.

---

### Post by klc5555 on 2011-11-09
> **sbrown7792 said:**
> Thank you all for your replies. I was indeed planning on getting a replacement rather than a supplement if I could (I'm still in the return window for this 1250). I looked into the MPEG encoder option in the mythtv setup just to be sure, but as expected it wasn't there. I will look into the 1600 and getting this one returned. As far as getting the analog signal, if the 1600 will pick up analog signals, does that automatically include IRC analog? I would assume so (but you know what they say about assuming), but whenever I hear people talking about analog support they are always talking about OTA NTSC signals, and I have no clue if its the same basic function. 

Thanks so much!

IRC refers to the frequency table used to place the individual channels on their individual requencies. (Wikipedia is our friend...) Like poe503 said, cable irc is a frequency option when setting up a channel scan.

The 1600 does cable analog fine; that's why I bought the first couple of them that I own back in 2008. At that time the digital driver was not ready for use, but this flaw  has been long since corrected.

  But if you have a choice get a slightly older 1600 rather than an up-to-the-nanosecond unit --the older ones are all perfectly supported, but Hauppauge changes the analog tuner they use in this card quite frequently, and it occasionally it takes the cx18 driver developers a bit to catch up to the point where the driver autodetects the very newest analog tuner. Basic information on the card is here: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

Pay no attention to the wiki's comments about whether individual 1600 models do digital QAM _on Windows_ The modern (since August 2010) cx18 driver supports QAM on all of these models in Linux. Plus, with 2 cable inputs, you can record a digital channel and an audio channel simultaneously.

---

### Post by poe503 on 2011-11-09
> Watch out when buying an "Avermedia A180" for this purpose: there are two varieties. The older version includes an analog tuner; the newer version is digital only.

I own both and have used both versions, but I don't use them any longer. I kept finding that on random occasions their digital tunes with high bitrate errors, and the resultant recording (or live tv) suffers from "popping" and generally degraded audio. Next tune would be perfect. Never did find a solid cause for this odd behavior. It happened rarely-to-occasionally on the 2.6.27.7 kernel that I originally installed them on, but became much more frequent with more recent kernels (i.e. 2.6.34.4 and later). Tried them both in a couple of machines.

Interesting observations.  I've owned a couple of these for about 4 years with no problems.  The name may be the same but the guts may vary, I guess.

---

### Post by sbrown7792 on 2011-11-09
Aight thanks everyone! I'll probably get a 1600 and make sure I get an older-ish model. This will definitely make me and my roommates happy haha.

---

### Post by LowSky on 2011-11-09
HD-5500 - its built for linux, but will also work with windows

[http://www.pchdtv.com/](http://www.pchdtv.com/)

---

### Post by thatguruguy on 2011-11-10
Or, if you have some USB ports sitting around not being used, you can save $20 and get the [Hauppauge 950Q]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4146195").

---

