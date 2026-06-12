---
title: "Hardware question for Comcast Digital and HDTV"
date: 2008-05-06
forum: Mythbuntu
---

### Post by jfenton78 on 2008-05-06
I have Comcast HDTV and I'm trying to figure out what capture cards  to get to record two channels and one for live TV. I'm looking at the PVR500 and PCHDTV 5500. So my questions are these:

-Would the PVR500 allow me to record the digital channels also from the HD STB? If not what could I record? Not recording HDTV on this card would be okay. Correct me if I'm wrong, but if I split the coax line I can at least record the analog channels using the PVR500. 

-If I hook the MythTV up to my digital STB (on a separate connection) I could record all digital channels using the PVR500?

-Would the PCHDTV5500 allow me record all channels from the HD STB (analog, digital, and HDTV) if the connection is through the STB?

-I think my HD STB has firewire. If its active then I don't need any capture card to record at least one channel and I'd be able to record all channels.

Let me know if you need more info. I'm trying to learn, but don't have all the answers yet.

jf

---

### Post by volkswagner on 2008-05-06
> **jfenton78 said:**
> I have Comcast HDTV and I'm trying to figure out what capture cards  to get to record two channels and one for live TV. I'm looking at the PVR500 and PCHDTV 5500. So my questions are these:

-Would the PVR500 allow me to record the digital channels also from the HD STB? If not what could I record? Not recording HDTV on this card would be okay. Correct me if I'm wrong, but if I split the coax line I can at least record the analog channels using the PVR500. 

-If I hook the MythTV up to my digital STB (on a separate connection) I could record all digital channels using the PVR500?

-Would the PCHDTV5500 allow me record all channels from the HD STB (analog, digital, and HDTV) if the connection is through the STB?

-I think my HD STB has firewire. If its active then I don't need any capture card to record at least one channel and I'd be able to record all channels.

Let me know if you need more info. I'm trying to learn, but don't have all the answers yet.

jf

I am not familiar with the pchdtv5500.  You can capture any channel from your cable box to your pvr500 via svid.  This would be in SD quality.  You can use firewire or IR blaster to change the channels.  If you can get a working firewire capture direct from the box, you will most likely only get a limited channel list.  Likely to get major networks in HD, and some basic cable channels.

I would set the pvr500 with two direct coax feeds, and one svid from the cable box.  This will let you capture two channels in SD.  The best way I know to get HD broadcast is via firewire.  wSo yes, splitting the coax will get you the most.  Split two for pvr and one for cable box= 3-way not including pchdtv500.

Do realize the cable box is a single tuner.  I will display to all it's outputs at the same time though.

What is the cable box model?

---

### Post by klc5555 on 2008-05-07
> **jfenton78 said:**
> I have Comcast HDTV and I'm trying to figure out what capture cards  to get to record two channels and one for live TV. I'm looking at the PVR500 and PCHDTV 5500. So my questions are these:

-Would the PVR500 allow me to record the digital channels also from the HD STB? If not what could I record? Not recording HDTV on this card would be okay. Correct me if I'm wrong, but if I split the coax line I can at least record the analog channels using the PVR500. 

-If I hook the MythTV up to my digital STB (on a separate connection) I could record all digital channels using the PVR500?

-Would the PCHDTV5500 allow me record all channels from the HD STB (analog, digital, and HDTV) if the connection is through the STB?

-I think my HD STB has firewire. If its active then I don't need any capture card to record at least one channel and I'd be able to record all channels.

Let me know if you need more info. I'm trying to learn, but don't have all the answers yet.

jf


The pchdtv 5500 works very well for HD and Digital. A great card for these purposes and I have a couple of them in my Myth backend. For analog, however, I've found them to be so finicky that the card is essentially useless for recording analog programming.

The Mythtv wiki article on this card ([http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500)) describes some of the problems and potential solutions for the dvb-v4l driver problem with this card. 

In my case I find that upon analog startup, the card races for a couple of seconds, then stalls, then races again, etc.  To get the analog section of this card working properly, after starting it I need to use the "y" keyboard shortcut to shuttle through all my tuner cards. When the 5500 analog comes around the second time, it works normally. This means that once I've got the card started I can record from analog "live tv", but timer recordings will fail. (The recordings seem to be running at about double speed, with wonky sound) To record analog I was compelled to add a Hauppauge PVR150 to the backend. I've tried compiling the driver as recommended in the wiki, but my compiled drivers have not been functional and I've had to go back to the default Mythbuntu (7.10) module package.

So in short, the 5500 cards ought to give you beautiful HD and Digital. But I'd recommend getting a Hauppauge (150, 350, 500)if you want to do analog viewing and recording.

Good luck!:)

---

### Post by jfenton78 on 2008-05-07
Thanks for the help. I'm starting to learn more, but have a few other questions.

-If I use a direct connection to the cable with a PCHDTV-5500 I can only receive unencrypted channels and how many would that be? If I went through a HDTV STB with a Svid or Coax connection to the 5500 will get me all the HD channels?

-If I used either the analog or a digital STB I could receive all channels, but only at SD?

-Can I specify for any card (the PVR500 or PCHDTV) which channels it can record and when I select the program from the frontend it records to the specified card for that channel?

Thanks again.

jf

---

### Post by klc5555 on 2008-05-08
> **jfenton78 said:**
> Thanks for the help. I'm starting to learn more, but have a few other questions.

-If I use a direct connection to the cable with a PCHDTV-5500 I can only receive unencrypted channels and how many would that be? ...

...

Thanks again.

jf



I use a direct connection to Comcast with a standard analog account. This gives me the usual cable lineup in analog and the unencrypted digital/HD channels. These unencrypted digital/HD channels consist of all the local broadcast channels, of which the network channels are available in 2 variants: one digital and one HD. The local broadcast channels (and local access) are available in their digital versions. Some cable-only channels are also available unencrypted in digital, notably the History channel, BET, RAI international, Speed, Style, CMT and a couple of the specialized PBS channels, along with the usual broadcast PBS channels and an HD PBS variant. Perhaps a couple of other digital channels may have slipped my mind.

I can't directly answer STB questions, because I've been unwilling to set up the type of account that would require one. As far as I know, though I may be wrong, Comcast only uses S-card based STBs, and I'm much happier with analog and MythTV's functionality with multiple cards than to possibly lose the bulk of this functionality by going all-digital through single-tuning STBs. Maybe someone else out there will have better answers to this. 

Cheers!:)

---

### Post by jakep_82 on 2008-05-08
> **jfenton78 said:**
> If I use a direct connection to the cable with a PCHDTV-5500 I can only receive unencrypted channels and how many would that be?

Yes, coax direct from the wall into the 5500 will get you digital QAM channels.  I get ABC, NBC, CBS, Fox, CW and PBS in HD with Comcast here.

> **jfenton78 said:**
> If I went through a HDTV STB with a Svid or Coax connection to the 5500 will get me all the HD channels?

No, svid will not carry HD and generally all but the local broadcast channels are encrypted.

> **jfenton78 said:**
> If I used either the analog or a digital STB I could receive all channels, but only at SD?

Currently the majority of HD digital channels are only recordable in SD.  The Hauppauge HD PVR will offer the ability to record HD from component input, but it's not shipping yet and it won't be supported in Myth right out of the gate.  I would wager that in a few months it will be supported in Myth.  When that happens you'll be able to record every HD channel.

> **jfenton78 said:**
> Can I specify for any card (the PVR500 or PCHDTV) which channels it can record and when I select the program from the frontend it records to the specified card for that channel?

You can create custom lineups and assign each custom lineup to a specific tuner.

---

### Post by jfenton78 on 2008-05-08
Hey all thanks for the great help. I can live with using a STB and analog signal to separate tuners to get all or most of my channels. I'm personally not happy with recording 4 or 5 channels in HD for so little return. I'm going to go with a PVR500 or two. Thanks.

jf

---

