---
title: "Hauappage 1600 question"
date: 2010-08-05
forum: Mythbuntu
---

### Post by agentsmith23 on 2010-08-05
I have a hauppage 1600 setup in my htpc and I am kinda new to having a tuner in my PC. I have cable through time warner and when I run a channel scan I would estimate that I get about 80 to 90 channels that show up. However when I try to view the channels only about 18 of them are viewable. When I run the scan i check the option to check decryptability and only free. The other settings are:
Frequency Type: Cable
Modulation: QAM256
I have the coax going into the ATSC digital TV connector.

Is it possible to view the other channels also or will I only be able to view the QAM stations? If the Hauppage 1600 doesn't allow me to view the other stations, is there any tuner that would allow me to view them?

Thanks for any possible help!

---

### Post by klc5555 on 2010-08-06
> **agentsmith23 said:**
> I have a hauppage 1600 setup in my htpc and I am kinda new to having a tuner in my PC. I have cable through time warner and when I run a channel scan I would estimate that I get about 80 to 90 channels that show up. However when I try to view the channels only about 18 of them are viewable. When I run the scan i check the option to check decryptability and only free. The other settings are:
Frequency Type: Cable
Modulation: QAM256
I have the coax going into the ATSC digital TV connector.

Is it possible to view the other channels also or will I only be able to view the QAM stations? If the Hauppage 1600 doesn't allow me to view the other stations, is there any tuner that would allow me to view them?

Thanks for any possible help!

Depends on what you mean by "viewable".

1) If by "viewable" you mean that the rest of the signals your 1600 scan has found are encrypted, and not clear QAM, then you already have what any clear QAM tuner is going to give you. Your cable provider will provide you as part of your cable package a decryption device --a settop box or a digital transport adapter-- which will tune and decrypt the encrypted channels you are authorized to receive according to your cable package and will output these channels in a format your myth pc can handle: firewire, or more generally analog via component or composite cable, or even an analog signal via channel 3 or 4 than can get piped into the NTSC (analog) input on the 1600. (I have 3 of these DTAs piping to 3 1600s on a couple of PCs.) The analog side of the card stays tuned to channel 3 (or 4) all the time, and your mythtv pc will change channels on the settop box or DTA by using an infrared transmitter (a "blaster") and Linux's infrared controller LIRC. Not nearly as difficult and opaque as it all sounds, and fairly copiously documented.

2) If by "viewable" you mean you know for certain you have 80-90 clear QAM stations (and if you do, I want to live where you live), but when your 1600 tries to tune the ones it has scanned and locked the stations are unwatchable because of pixelation and artifacts in the signal, then you may be having signal strength issues of the sort that still occasionally affect the QAM side of the 1600. The normal cure is to compile the currentmost v4l-dvb drivers (not difficult) and/or clean up the physical cabling to the tuner while adding a small signal amp.  

In any event, some reading to do from the mythtv wiki, starting with (but not limited to) [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

and maybe [http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)

Cheers!

---

### Post by LowSky on 2010-08-06
Let me say this in more understandable terms.

Cable companies are only legally required to show local broadcast stations unencrypted. Your other channels will require a cable box.

The only legal way to see all your channels right now is this device
[http://www.fluiddigitalmedia.com/products/ceton](http://www.fluiddigitalmedia.com/products/ceton)

Unfortunatly it will only work in Windows 7 Media center. and there is no support for Linux planned.

Your other option is one of these connected to a cable box
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030&cm_re=hd_pvr-_-15-116-030-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030&cm_re=hd_pvr-_-15-116-030-_-Product)

This option will work in MythTV but it isn't a internal tuner

---

### Post by agentsmith23 on 2010-08-10
I got it to work. I followed the guide in the mythtv wiki for the 1600 for setting up the digital and analog side of the card. From my wall I have the cable coming out then to a 3-way splitter two of the outputs on the splitter are going to the tuner (one digital and one analog), and the other to my TV. I can view all of the QAM stations on the digital half and the rest on the analog side. I can record two shows at once as long as one is digital and one is analog.

Thanks for the input though!

---

### Post by klc5555 on 2010-08-10
Well done! Not everyone is so lucky with the 1600! :)

The great advantage of the 1600, when the card is working correctly like yours is, is that at some later time, if you need some sort of settop box for encrypted digital channels, you'll be able to hook the box to the analog port on the 1600 while leaving the clear QAM port and tuner unaffected. Can't do that with most other card options that only have a single port.

All the best!

---

