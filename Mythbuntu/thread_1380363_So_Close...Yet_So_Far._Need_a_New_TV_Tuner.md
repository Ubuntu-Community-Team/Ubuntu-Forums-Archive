---
title: "So Close...Yet So Far. Need a New TV Tuner"
date: 2010-01-13
forum: Mythbuntu
---

### Post by jquintana on 2010-01-13
I have succesfully built my Mythbuntu box to do everything I want with the exception of PVR.

I am in Houston, TX and use Comcast as my cable provider. I would like to be able to record EVERYTHING that I can get from my Comcast box.

I currently have a Hauppauge HVR-1600 but have read that the QAM is not very good on these cards so I am willing to get something else.

Can someone suggest a card that will allow me to view/record HD channels through Comcast?

Thanks in advance!

(Heading to Frys, MicroCenter, of Best Buy as soon as someone suggests something for me to try.)

---

### Post by larsolav on 2010-01-13
If you want to record everything Comcast can offer (including encrypted HD channels), I think the [hd-pvr]("http://registration.hauppauge.com/webstore/hardware2.asp?product=hd_pvr") is your only option.

---

### Post by the_pod on 2010-01-13
Before you give up too soon and spend money, I strongly encourage you to try Devin's drivers.  

[http://ubuntuforums.org/showthread.php?t=1318206](http://ubuntuforums.org/showthread.php?t=1318206)

Was just poking around his site and it seems that his changes are  being built into the "official" V4L stuff but I haven't personally confirmed this.  I have personally confirmed that his updates to the digital driverset have eliminated my need for a different video card, however, and I suspect you'll find the same thing.

---

### Post by jquintana on 2010-01-13
> **larsolav said:**
> If you want to record everything Comcast can offer (including encrypted HD channels), I think the [hd-pvr]("http://registration.hauppauge.com/webstore/hardware2.asp?product=hd_pvr") is your only option.What about these: [Hauppage HVR-1950]("http://www.hauppauge.com/site/products/data_hvr1950.html") or HD [HomeRun]("http://www.silicondust.com/products/hdhomerun_atsc") ?

I was at Frys and saw both of these so I decided to pick them up and see what happens.

---

### Post by jquintana on 2010-01-13
> **the_pod said:**
> Before you give up too soon and spend money, I strongly encourage you to try Devin's drivers.  

[http://ubuntuforums.org/showthread.php?t=1318206](http://ubuntuforums.org/showthread.php?t=1318206)

Was just poking around his site and it seems that his changes are  being built into the "official" V4L stuff but I haven't personally confirmed this.  I have personally confirmed that his updates to the digital driverset have eliminated my need for a different video card, however, and I suspect you'll find the same thing.I think my issue is more configuration related than drivers. I am able to watch TV using VLC but nothing in MythTV. :confused:

---

### Post by hrobinson on 2010-01-13
Hi jquintana,

Can you tell us what you did, step by step (don't skip anything) to get to where you are now?  From what I understand QAM or **Quadrature amplitude modulation **is for terrestrial broadcasts (OVER the AIR, not CABLE), I don't believe it has an affect on what you are trying to accomplish now.  One of the other pieces of equipment you will need is a digital cable box from your cable provider, and an item called an IR blaster which will sit in front of the cable box to change the channel when a show is about to record.

Sincerely,

Harold Robinson

---

### Post by jquintana on 2010-01-13
> **hrobinson said:**
> Hi jquintana,

Can you tell us what you did, step by step (don't skip anything) to get to where you are now?

Sincerely,

Harold RobinsonI can certainly try but I have done a lot and may miss something.

A) I installed Mythbuntu 9.10 from the cd.
B) I changed video drivers to use the recommended Nvidia driver
C) Ran system updaate
D) Installed my HVR-1600 
E) I added "vmalloc=256M" to my grub
F) Rebooted and made sure I was able to use my video card while the 1600 was installed
G) Ran mythtv backend setup to configure the capture card using [this]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Backend_Setup") guide
H) Was not able to watch anything in Mythtv so I tried using VLC and was able to watch one channel only with VLC
H) Became very frustrated with my limited knowledge of tuner cards and went to Frys to get something else.
I) Bought an HD HomeRun and also an HVR-1925

:D

---

### Post by hrobinson on 2010-01-13
jquintana,

how is your cable hooked up.  It should be from the wall to the cablebox, from the cable box to the MythTV box.  Is that how its set up?

Sincerely,

Harold Robinson

---

### Post by jquintana on 2010-01-13
Yes.

Wall > Scientific Atlantic Explorer 8300HD > HVR-1600 via coaxial cable

I have tried both the "Analog Cable TV" In and the "ATSC/QAM Digital TV In"

Thanks!

---

### Post by hrobinson on 2010-01-13
Next Set the TV tuner card to Channel 3, then you should be able to change channels from the cable box.  Use the Analog in on the TV card.

Sincerely,

Harold Robinson

---

### Post by jquintana on 2010-01-13
> **hrobinson said:**
> Next Set the TV tuner card to Channel 3, then you should be able to change channels from the cable box.  Use the Analog in on the TV card.

Sincerely,

Harold RobinsonTried that but all I got was static on the TV.

Am going to delete all tuners and video sources and follow the wiki again.

---

### Post by jquintana on 2010-01-13
Well, I finally got the HVR-1600 to work. I am not using the cable box, though. I connected it straight to the wall and am only viewing the clear QAM channels.

I will be returning the HVR-1600 tomorrow. I ordered the HD-PVR tonight so hopefully that will be easy to configure when I get that.

Now my problem is that my channels dont match up with my schedulesdirect.org lineup. I will start a new thread for that, though.

Thanks for all the help thus far -- I greatly appreciate it!

---

### Post by ei777 on 2010-02-20
The only way to get this Hvr 1600 to work with the cable box is as follows.
1) buy a s-video cable to run from the box to the card

2)buy a rca to headphone 3.5mm plug converter for the sound port on the HVR 1600 from the cable box

3) when in the Wintv7 go to the configuration menu.

4) go to the devices tab run the tuner setup.

5)highlight the composite/s-video box

after the tuner setup is done the s-video channel is the cable box input channel then change the channels from the cable box only

---

