---
title: "Mythbuntu with Virgin Media stb in UK"
date: 2008-09-24
forum: Mythbuntu
---

### Post by patslap on 2008-09-24
I am subscribed to Virginmedia cable tv. I have a Samsung SMT-2100C ([http://chrismi.com/pages/samsung/index.html](http://chrismi.com/pages/samsung/index.html)) which is a digital set top box provided by Virgin. I receive their basic digital TV package (basically free-to-air channels, plus a few extra avail on cable).

I wish to build a media centre for the main TV running Mythbuntu. I will be building it from scratch and have chosen all the components, but need help on a TV Tuner card:

1. Is a TV tuner card necessary, or can I just plug a USB cable or ethernet cable between the mythtbuntu box and the Samsung stb and use that as a tuner instead (the virginmedia stb has a usb and ethernet port at the back, but no firewire)? 

2.If I need a TV Tuner pci card, would I need a DVD-C card, or can I use any TV Tuner on the basis that the Samsung stb outputs a TV signal? 

3. How can Mythbuntu control the stb, to change channel for example? I've read that Mythbuntu can control a cable stb, but have so far only seen this described using a serial link with an IR LED on the end of it taped to the front of the cable stb - is there a better way?

Many thanks for any help.

---

### Post by patslap on 2008-09-24
(bump) - Does anyone here connect a mythbuntu box (or just mythtv for that matter) to virginmedia cable set top box? If so, what tv card do you use use, if you use one at all?

Thanks!

---

### Post by david_f1976 on 2008-09-25
Hi,

We subscribe to Virgin but have a very old STB from Telewest days. I'm pretty sure that the signal output by the STB is analogue i.e. so that it can be used by our old CRT TV. We would basically need to connect the RF output from the STB to an analogue tuner, e.g. Hauppauge 150 or 500, in your MythTV box.

I'm pretty sure this is the way to go. Can you confirm what TV you have and how you currently connect the Samsung STB to it.

---

### Post by patslap on 2008-09-27
Hi David

I connect my virgin cable stb (digital cable, but not the Virgin+ ) to a CRT TV via SCART. The stb does have an ethernet and a usb port as well, but not sure what these are for, or even whether they function.

I'm looking to put the mythbuntu box I plan to build in-between the TV and stb and be able to watch one channel whilst recording another - is this possible on your set-up?

Many thanks

---

### Post by david_f1976 on 2008-09-28
I don't actually have Virgin connected to my mythbox, I decided to use MythTV with Freeview instead and maintain Virgin for normal TV usage. So my responses are based on the testing/research I did last year.

In general it is only possible to tune to one channel at a time with Virgin. There are some Virgin boxes that can output a cable channel and also one of the analogue terrestrial channels simultaneously, but they may be few and far between. It may be possible to do what you want to do, but would probably require you to subscribe to V+ or something. And even then I suspect it would only be possible if the V+ box had two independent outputs.

As for the ethernet and usb ports, I'm not so sure. If nobody on here can help you with that info, it may be worth checking out a digital TV forum, or searching for the STB manual.

In summary, what you're trying to do is very difficult, both technically and legally. See this post here for more details
[http://www.killswtch.net/2008/06/19/alternatives-to-dvb-t-in-the-uk/]("http://www.killswtch.net/2008/06/19/alternatives-to-dvb-t-in-the-uk/")

Dave

---

### Post by patslap on 2008-10-24
> **david_f1976 said:**
> I don't actually have Virgin connected to my mythbox, I decided to use MythTV with Freeview instead and maintain Virgin for normal TV usage. So my responses are based on the testing/research I did last year.

In general it is only possible to tune to one channel at a time with Virgin. There are some Virgin boxes that can output a cable channel and also one of the analogue terrestrial channels simultaneously, but they may be few and far between. It may be possible to do what you want to do, but would probably require you to subscribe to V+ or something. And even then I suspect it would only be possible if the V+ box had two independent outputs.

As for the ethernet and usb ports, I'm not so sure. If nobody on here can help you with that info, it may be worth checking out a digital TV forum, or searching for the STB manual.

In summary, what you're trying to do is very difficult, both technically and legally. See this post here for more details
[http://www.killswtch.net/2008/06/19/alternatives-to-dvb-t-in-the-uk/]("http://www.killswtch.net/2008/06/19/alternatives-to-dvb-t-in-the-uk/")

Dave

I'm still looking into this! Can't get a Freeview signal in my flat (the communal aeriel isn't pulling in a strong enough signal), so I'm looking into running the cable stb to the mythbuntu box which will have a happauge pvr-150 tv card in it. An IR transmitter will run back to the cable stb and change channels under instruction from mythbuntu (I hope).

That's the idea anyway - anyone got any suggestions, or built anything similar (I expect to run into difficulties with the IR transmitter)?

---

### Post by Pvt_Ryan on 2008-11-04
The ethernet port is/was for when you had broadband and cable. The stb acted as the modem and the ethernet cable when to the PC to allow broadband access. 

They stopped doing it as 1 service breaking could break both services.


I am looking the same advice as you are on which capture card to use.

[QUOTE=odinb]Ryan, I use the HD 5500 with myth on my HTPC. This card is supported natively in Linux, so it works out of the box!

No drivers for windows, be aware of that though. Not a problem for me as I run Ubuntu on my HTPC...

[http://www.pchdtv.com/](http://www.pchdtv.com/)[/QUOTE]

(from the XBMC forums where I originally asked the question)

Anyone else tried the card he mentions?

---

### Post by patslap on 2008-11-04
After further investigation I'm going to go down the same route as david_f1976: > I decided to use MythTV with Freeview instead and maintain Virgin for normal TV usage

It appears that the signal quality will degrade substantially, noticeably affecting the picture quality, once an anaolgue feed is sent from stb to pci tv card then on to the television itself.

I am now looking for a good quality freeview indoor antenna as i live in a flat where I cannot have an external aeriel. I believe Philex make a good quality indoor antenna with a signal booster.

It's a shame virgin media don't allow customers to connect a DVD-C tuner directly to their network to access channels as those in the USA can as this would be ideal.

---

