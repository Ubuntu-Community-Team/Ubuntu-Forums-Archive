---
title: "Beginner Installation Recommendation"
date: 2009-01-06
forum: Mythbuntu
---

### Post by cohenb on 2009-01-06
I'm trying to replace my Comcast HD box and DVR and am seeking some recommendations on the best hardware to purchase for installation. My current system has the following specifications:

Intel Celeron 2.20 GHz
1 GB of RAM
Intel 82845 G Graphics Controller
189 GB Hard Drive

I would like to buy a dual tuner HD card. Do you have any recommendations on the kind of card to buy? Secondly, based on my specs, can my system support HD? I'm willing to upgrade my graphics card and RAM if necessary. I'd also welcome recommendations on Graphics cards.

---

### Post by klc5555 on 2009-01-06
> **cohenb said:**
> I'm trying to replace my Comcast HD box and DVR and am seeking some recommendations on the best hardware to purchase for installation. My current system has the following specifications:

Intel Celeron 2.20 GHz
1 GB of RAM
Intel 82845 G Graphics Controller
189 GB Hard Drive

I would like to buy a dual tuner HD card. Do you have any recommendations on the kind of card to buy? Secondly, based on my specs, can my system support HD? I'm willing to upgrade my graphics card and RAM if necessary. I'd also welcome recommendations on Graphics cards.

Tastes, pocketbooks, and tech skills can vary. Also, it's not clear what you mean by "replace" your Comcast HD box. 3rd party tuners receive OTA digital and unencrypted QAM only (including HD). If your Comcast package includes encrypted fare, you'll still need a Comcast settop box that, maybe, will pipe the freshly decrypted content to your Myth machine via Firewire. No other 3rd party tuners necessary.

But if you're interested in OTA signals from an antenna, or unencrypted QAM from your provider, then I suppose the HD HomeRun is the Gold Standard among dual HD tuners. There are other possibilities, whose current support under Linux is assessed at the mythtv wiki page [http://mythtv.org/wiki/index.php/Category:HDTV_capture_cards](http://mythtv.org/wiki/index.php/Category:HDTV_capture_cards)

As for the rest of your system, I'd think 2.2 Gig might be a bit borderline for the displaying of HD content, which is very CPU intensive. As for graphic display, a good solid NVidia GE Force 6xxx, 7xxx, or 8xxx with, say, 512 Megs or above graphics memory would likely be the best-supported choice under Linux for HD. The onboard Intel controller is likely OK for analog or SD content.

1 Gig RAM may be OK --I do dual HD records with simultaneous HD playback on a machine with 1.5 Gigs without trouble.

Finally, HD files are _really_ big: recording HD kills roughly 7 Gigs per hour. I'd recommend keeping your current disk as the systems-swap-and-other-files disk, and get something in the 500 Gig to 1.5 T-byte range as a separate drive dedicated solely to recordings storage. Preferably SATA (about the only thing that exists above 500 Gigs) since EIDE occasionally proves to be a tad too slow to handle all the read/writes without bottlenecks.

Just my own preferences. Others may disagree.

Cheers! :)

---

### Post by tdmarvel on 2009-01-06
> **klc5555 said:**
> Tastes, pocketbooks, and tech skills can vary. Also, it's not clear what you mean by "replace" your Comcast HD box. 3rd party tuners receive OTA digital and unencrypted QAM only (including HD). If your Comcast package includes encrypted fare, you'll still need a Comcast settop box that, maybe, will pipe the freshly decrypted content to your Myth machine via Firewire. No other 3rd party tuners necessary.

But if you're interested in OTA signals from an antenna, or unencrypted QAM from your provider, then I suppose the HD HomeRun is the Gold Standard among dual HD tuners. There are other possibilities, whose current support under Linux is assessed at the mythtv wiki page [http://mythtv.org/wiki/index.php/Category:HDTV_capture_cards](http://mythtv.org/wiki/index.php/Category:HDTV_capture_cards)

As for the rest of your system, I'd think 2.2 Gig might be a bit borderline for the displaying of HD content, which is very CPU intensive. As for graphic display, a good solid NVidia GE Force 6xxx, 7xxx, or 8xxx with, say, 512 Megs or above graphics memory would likely be the best-supported choice under Linux for HD. The onboard Intel controller is likely OK for analog or SD content.

1 Gig RAM may be OK --I do dual HD records with simultaneous HD playback on a machine with 1.5 Gigs without trouble.

Finally, HD files are _really_ big: recording HD kills roughly 7 Gigs per hour. I'd recommend keeping your current disk as the systems-swap-and-other-files disk, and get something in the 500 Gig to 1.5 T-byte range as a separate drive dedicated solely to recordings storage. Preferably SATA (about the only thing that exists above 500 Gigs) since EIDE occasionally proves to be a tad too slow to handle all the read/writes without bottlenecks.

Just my own preferences. Others may disagree.

Cheers! :)

Even though I didn't post the question, I want to thank you for the response. I've been looking at this for a while, and with my second job I'm getting the funds to jump in with both feet (basically I'm building a Myth-box up from scratch.) I'm not having much luck with finding the HD HomeRun in card format anywhere. I've been considering the Network-based version of HD HomeRun with the Ethernet interface (from Newegg.com). Is that what you're referring to?

---

### Post by cohenb on 2009-01-06
Thanks for the speedy reply klc5555. I was trying to figure out a way to completely replace my Comcast box to save a few bucks, but I didn't realize that they encrypted their HD signal.

I have just a couple of clarifying questions:

1. If I keep my Comcast box, can I use the HD HomeRun to watch encrypted HD by first running the main coax into the cable box and then from the cable box to HD HomeRun?

2. To add to a part of tdmarvel's question, do I just connect the HD Homerun to my PC via the ethernet port?

Thanks again for the help.

---

### Post by newlinux on 2009-01-06
> **tdmarvel said:**
> Even though I didn't post the question, I want to thank you for the response. I've been looking at this for a while, and with my second job I'm getting the funds to jump in with both feet (basically I'm building a Myth-box up from scratch.) I'm not having much luck with finding the HD HomeRun in card format anywhere. I've been considering the Network-based version of HD HomeRun with the Ethernet interface (from Newegg.com). Is that what you're referring to?


Yep, the hdhomerun is a networked device (not a card), which certainly has its advantages. It's well supported and popular. Are you looking for PCI or PCIe cards. Hauppage makes some well supported PCI and PCIe cards, and you sometimes can find some of the older well supported cards (Avermedia A180, Kworld ATSC 110/115, Dvico Fusion 5s) on ebay.

A good list of supported ATSC/QAM cards:

[http://linuxtv.org/wiki/index.php/ATSC_Devices](http://linuxtv.org/wiki/index.php/ATSC_Devices)

---

### Post by newlinux on 2009-01-06
> **cohenb said:**
> Thanks for the speedy reply klc5555. I was trying to figure out a way to completely replace my Comcast box to save a few bucks, but I didn't realize that they encrypted their HD signal.

I have just a couple of clarifying questions:

1. If I keep my Comcast box, can I use the HD HomeRun to watch encrypted HD by first running the main coax into the cable box and then from the cable box to HD HomeRun?

2. To add to a part of tdmarvel's question, do I just connect the HD Homerun to my PC via the ethernet port?

Thanks again for the help.



1. No. You would need an analog capture device that can capture via one of the analog outputs of your DVR via composite, RF, or S-video. I've used a pvr-150 for this. All signals (including HD) would be captured in SD. And you would need to use an IR blaster or firewire to change the channels on the cable box.


You may be able to use this [http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels) to see what stations you'll be able to get without a cable box. Otherwise if you have a digital TV it may have a QAM tuner that can tune unencrypted QAM and that can tell you what stations you have available via unencrypted QAM as well.

2. Yes, but you'll be better off (unless you have two network cards in your computer)  just connecting the HDhomerun up to your router. 

for more info:

[http://www.silicondust.com/hdhomerun/instructions](http://www.silicondust.com/hdhomerun/instructions)

---

### Post by tdmarvel on 2009-01-06
> **newlinux said:**
> Yep, the hdhomerun is a networked device (not a card), which certainly has its advantages. It's well supported and popular. Are you looking for PCI or PCIe cards. Hauppage makes some well supported PCI and PCIe cards, and you sometimes can find some of the older well supported cards (Avermedia A180, Kworld ATSC 110/115, Dvico Fusion 5s) on ebay.

A good list of supported ATSC/QAM cards:

[http://linuxtv.org/wiki/index.php/ATSC_Devices](http://linuxtv.org/wiki/index.php/ATSC_Devices)

I guess I'm not really sure what I need to be looking at, then. I've got a Firewire out on my cable box, but Bresnan keeps telling me that it's disabled/disconnected. (I have enough electronics knowledge to see a cut wire, I just can't bring myself to crack the case.)
I'm looking at capturing video from the cable signal and OTA. I've got a home theater setup with a DVD changer, as well as a stand-alone DVD player/VHS recorder. My TV has plenty of inputs to handle things. I guess I'm really looking more at just a stand alone card, PCI or PCIe. I'd been looking at the Hauppage 1600. Anybody have any thoughts/concerns/advice?

---

### Post by klc5555 on 2009-01-07
> **tdmarvel said:**
> I guess I'm not really sure what I need to be looking at, then. I've got a Firewire out on my cable box, but Bresnan keeps telling me that it's disabled/disconnected. (I have enough electronics knowledge to see a cut wire, I just can't bring myself to crack the case.)
I'm looking at capturing video from the cable signal and OTA. I've got a home theater setup with a DVD changer, as well as a stand-alone DVD player/VHS recorder. My TV has plenty of inputs to handle things. I guess I'm really looking more at just a stand alone card, PCI or PCIe. I'd been looking at the Hauppage 1600. Anybody have any thoughts/concerns/advice?

Among pci cards, for digital use I've had very good luck with the pcDH5500. IT is not, however, hardware encoding (which is no big deal with recording SD/HD streams). More significant for you may be the awful, awful analog side of the card. If you don't need analog much or at all, then this card, which really does do beautiful HD, may be for you.

I've been wrestling with a Hauppauge 1600 and its Spawn-of-Satan cx18 beta driver for the better part of 3 months. It can work, but each installation is frighteningly unique depending on your hardware, and I would not recommend the card to anyone who is really new to Linux. My own particular 1600 has come to work quite nicely on analog, finally, but is digitally almost deaf. By sliding in a Motorola line-drop amp I was finally able to get the card to locate (with dvb-apps) and tune 7 of the 21 clear QAM stations that are all easily visible to my two pcHD5500s. This blissful state of affairs lasted for maybe a couple of hours; thereafter it has only been able to locate and tune 2 of the QAM signals.

In short, there are likely much better choices out there than the 1600. :( Hopefully other folk will voice their preferences.

---

### Post by newlinux on 2009-01-07
> **tdmarvel said:**
> I guess I'm not really sure what I need to be looking at, then. I've got a Firewire out on my cable box, but Bresnan keeps telling me that it's disabled/disconnected. (I have enough electronics knowledge to see a cut wire, I just can't bring myself to crack the case.)
I'm looking at capturing video from the cable signal and OTA. I've got a home theater setup with a DVD changer, as well as a stand-alone DVD player/VHS recorder. My TV has plenty of inputs to handle things. I guess I'm really looking more at just a stand alone card, PCI or PCIe. I'd been looking at the Hauppage 1600. Anybody have any thoughts/concerns/advice?

For tuners...
Digital OTA = ATSC
Digital cable = QAM (but you can only tune unencrypted QAM)
Analog cable = NTSC

I have only PCI cards... I have 3 Kworld 110/115s (QAM/ATSC/NTSC capable) 1 Avermedia A180 (QAM/ATSC) 1 Dvico fusion 5 lite (QAM/ATSC/NTSC), and one PVR-150 (NTSC, hardware encoding). All of these cards are old and easiy to get working. I've also used a pchdtv 5500 and it is easy to get working digitally as well. I sold it (overpriced) and bought two more Kworld 110s. 

HArdware encoding means nothing with digital capture, since the stream is already encoded. There is no difference in quality of capture from digital card to digital card, because all they do is capture the stream as is from QAM or ATSC. the only difference in those cards is tuning sensitivity.

---

### Post by tdmarvel on 2009-01-07
> **newlinux said:**
> For tuners...
Digital OTA = ATSC
Digital cable = QAM (but you can only tune unencrypted QAM)
Analog cable = NTSC

I have only PCI cards... I have 3 Kworld 110/115s (QAM/ATSC/NTSC capable) 1 Avermedia A180 (QAM/ATSC) 1 Dvico fusion 5 lite (QAM/ATSC/NTSC), and one PVR-150 (NTSC, hardware encoding). All of these cards are old and easiy to get working. I've also used a pchdtv 5500 and it is easy to get working digitally as well. I sold it (overpriced) and bought two more Kworld 110s. 

HArdware encoding means nothing with digital capture, since the stream is already encoded. There is no difference in quality of capture from digital card to digital card, because all they do is capture the stream as is from QAM or ATSC. the only difference in those cards is tuning sensitivity.

Great info, thanks. Well, on that note, I'll be looking at something else other than the 1600. While I believe I have the inclination to learn to make things work well, I don't really have the patience. Thanks to both of you (klc5555 and newlinux, as well as cohenb for starting the thread). I'll be posting the results when I finally get going.

---

### Post by cohenb on 2009-01-07
> **newlinux said:**
> 1. No. You would need an analog capture device that can capture via one of the analog outputs of your DVR via composite, RF, or S-video. I've used a pvr-150 for this. All signals (including HD) would be captured in SD. And you would need to use an IR blaster or firewire to change the channels on the cable box.


You may be able to use this [http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels) to see what stations you'll be able to get without a cable box. Otherwise if you have a digital TV it may have a QAM tuner that can tune unencrypted QAM and that can tell you what stations you have available via unencrypted QAM as well.

2. Yes, but you'll be better off (unless you have two network cards in your computer)  just connecting the HDhomerun up to your router. 

for more info:

[http://www.silicondust.com/hdhomerun/instructions](http://www.silicondust.com/hdhomerun/instructions)

I apologize but I guess I'm a little slow to learning all of these new concepts. Is there a way to record the freshly decrypted HD Content from the cable box in an HD format? Or would I have to settle with SD recordings?

Are most pci cards, for example the Hauppauge 1600 which was mentioned here and which I was also looking at, used only to record unencrypted QAM and over the air transmissions? Is there a way to record the encrypted content? Would that be the firewire method mentioned in the intial reply to my post?

---

### Post by newlinux on 2009-01-07
> **cohenb said:**
> I apologize but I guess I'm a little slow to learning all of these new concepts. Is there a way to record the freshly decrypted HD Content from the cable box in an HD format? Or would I have to settle with SD recordings?

Are most pci cards, for example the Hauppauge 1600 which was mentioned here and which I was also looking at, used only to record unencrypted QAM and over the air transmissions? Is there a way to record the encrypted content? Would that be the firewire method mentioned in the intial reply to my post?

You could use the Hauppage HD-PVR to capture HD output form the components, but I believe the myth/linux drivers are expiremental. Other than that, your best bet is firewire, and then you have to worry about 5c (DTCP) encryption. May be turned on or not, channel by channel. Those are your only options for encrypted content. The cable companies really want you to use their box. There is no cable card support in Linux. Cable cards are the additional way you could if you were on Windows (but buying PCs with cable card support is pricey - you can't build it yourself, last I checked).

---

