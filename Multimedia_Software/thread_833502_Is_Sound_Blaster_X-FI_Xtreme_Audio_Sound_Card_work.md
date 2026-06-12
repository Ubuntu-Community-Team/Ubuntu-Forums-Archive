---
title: "Is Sound Blaster X-FI Xtreme Audio Sound Card working on Ubuntu 8.04?"
date: 2008-06-18
forum: Multimedia Software
---

### Post by chuugokujin on 2008-06-18
I am thinking of buying a new sound card and I like this one. Before buying it I have to make sure it will work on Ubuntu Hardy. Would it work?

Also does ALSA, OSS or PulseAudio support this card?

Will this card work when I wine WOW? My current sound card does.

Thanks a lot.

---

### Post by patrickaupperle on 2008-06-18
I am interested in this as well, so I hope someone posts.

---

### Post by Stochastic on 2008-06-18
according to the [alsa soundcard matrix]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") that card isn't supported yet, but development is underway.
> Sound Blaster X-Fi
emu20k1
[Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative have supplied a data sheet to developers. Development work has started.

---

### Post by notlim_hardy on 2008-06-18
I have a X-fi and I can't play any MIDI files. MP3 and WAV are ok. I read all possible guides and all stuff I managed to find on google. Timidity returns a "error 1" during the install process. Can anyone help me? Thanks.

---

### Post by notlim_hardy on 2008-06-18
Please anyone help me get MIDI to work on Hardy!!!

---

### Post by Stochastic on 2008-06-24
notlim_hardy, you'll probably get better help if you start your own thread on the subject of getting MIDI to work with your card.  Do you have timidity installed?  Take a look here for more info on how to setup midi: [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?highlight=(MIDI)](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?highlight=(MIDI))

It's good to hear the the card is up and working (playing mp3s and wavs) now.

---

### Post by NullHead on 2008-06-24
DO NOT buy a Creative X-Fi!!!!!!!!!!!!! Don't give creative any money either! I highly recommend this card: [http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx](http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx) witch is fully supported by alsa. 

Of course that is just my opinion and you should do some research on your own about this. I do strongly suggest you steer clear of creative at all costs.

The X-Fis are iffy at best when it comes to linux support.

---

### Post by Trollslayer on 2008-06-24
> **notlim_hardy said:**
> I have a X-fi and I can't play any MIDI files. MP3 and WAV are ok. I read all possible guides and all stuff I managed to find on google. Timidity returns a "error 1" during the install process. Can anyone help me? Thanks.

Have you got the digital output working?

---

### Post by jukingeo on 2008-06-25
> **NullHead said:**
> DO NOT buy a Creative X-Fi!!!!!!!!!!!!! Don't give creative any money either! I highly recommend this card: [http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx](http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx) witch is fully supported by alsa. 

Of course that is just my opinion and you should do some research on your own about this. I do strongly suggest you steer clear of creative at all costs.

The X-Fis are iffy at best when it comes to linux support.

Hello Nullhead,

I know you don't like Creative, but I am looking for a USB external sound device that is known to work with Linux/ALSA (whether it be Creative or not). Razor doesn't make an external card.  So do you have other suggestions besides Razor?

Thanx,

Geo

---

### Post by Trollslayer on 2008-06-25
> **NullHead said:**
> DO NOT buy a Creative X-Fi!!!!!!!!!!!!! Don't give creative any money either! I highly recommend this card: [http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx](http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx) witch is fully supported by alsa. 

Of course that is just my opinion and you should do some research on your own about this. I do strongly suggest you steer clear of creative at all costs.

The X-Fis are iffy at best when it comes to linux support.

I have been checking on this and agree - I don't plan to spend six months reverse engineering their Windows driver to work out the interface!
The Rzer is based on the C-Media 8788 and Asus do a cheaper board based on the same chip which has got very good reviews:
[http://uk.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1](http://uk.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1)
Guess where my money is going!

---

### Post by NullHead on 2008-06-25
> **jukingeo said:**
> Hello Nullhead,

I know you don't like Creative, but I am looking for a USB external sound device that is known to work with Linux/ALSA (whether it be Creative or not). Razor doesn't make an external card.  So do you have other suggestions besides Razor?

Thanx,

Geo

I've never investigated an external audio solution before. I would not know of another sound card that would suit your needs. My [good 'ol pall]("http://www.google.com") can surely help you though! ;)
> **Trollslayer said:**
> I have been checking on this and agree - I don't plan to spend six months reverse engineering their Windows driver to work out the interface!
The Rzer is based on the C-Media 8788 and Asus do a cheaper board based on the same chip which has got very good reviews:
[http://uk.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1](http://uk.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1)
Guess where my money is going!

Well it is good that it is fully supported. I heard the Asus sound card isn't that good for gaming though :( I have no facts about it though, so please prove me wrong! I would love to get off of my X-Fi addiction!!! yes I just contradicted myself ... I do hate Creative with all my soul, but I also love their X-Fi's performance on the windows platform :???:

---

### Post by jukingeo on 2008-06-25
> **NullHead said:**
> I've never investigated an external audio solution before. I would not know of another sound card that would suit your needs. My [good 'ol pall]("http://www.google.com") can surely help you though! ;)

Heh Heh, cute :roll: Anyway, I did do some searching right here in this forum and as it turns out the Sound Blaster Live, 24bit and Audigy DO have external models that plug into the USB ports.  Supposedly these versions of the INTERNAL card are supported by Linux, but there are those with Laptop computers that don't have compatible on-board sound devices and these people are trying to get the external USB sound devices to work.  So far I have been getting mixed results.  But it does seem possible to run an external sound card.

>  I heard the Asus sound card isn't that good for gaming though :( I have no facts about it though, so please prove me wrong! I would love to get off of my X-Fi addiction!!! yes I just contradicted myself ... I do hate Creative with all my soul, but I also love their X-Fi's performance on the windows platform :???:

I have been sold on Creative devices for a long time now.  In fact for an external device, that is what I would want.  I only deviate from the Creative path when it comes to pro audio devices.

As of now I don't think there is a Linux based audio card that can handle 192khz frequency.  The X-Fi can do 96k and my Alesis IO-26 can do 192k in Windows.  Most of the Hammerfall cards only go up to 96k as well.  So for the X-Fi... that is a pretty impressive spec for a consumer card.

Now sure I can go with a Sound Blaster Live external USB device and it probably will work...but as far as I recall, the SB Live isn't 24 bit, it is 16 bit.  Also 48k is the highest frequency it can go.  Those specs aren't good enough for me for recording.  The card/device MUST at least do 24bit 96k with 192k being my preference. BUT in the very least with A sound card that works, I can at least test the waters with the Ubuntu Studio applications.  It gives me something to work with.  So it is better than nothing.

I think M-Audio may have some compatible external devices as well.  However, I know M-Audio's products and they are built like crap.  They have a very high failure rate among their computer based products out in the field.  Their keyboards are horrendous.  They constantly break.  Pure junk.  Go look on Musicians Friend and see how many bad reviews M-Audio products get.  Look how many Blem (B stock) M-Audio products they have in their clearance section.  The only thing decent M-Audio makes are the USB midi interfaces.

Anyway, I am going to do a little more of this ](*,) and then I am going to hit the sack.

Thanx,

Geo

---

### Post by Trollslayer on 2008-06-26
> **NullHead said:**
> I've never investigated an external audio solution before. I would not know of another sound card that would suit your needs. My [good 'ol pall]("http://www.google.com") can surely help you though! ;)


Well it is good that it is fully supported. I heard the Asus sound card isn't that good for gaming though :( I have no facts about it though, so please prove me wrong! I would love to get off of my X-Fi addiction!!! yes I just contradicted myself ... I do hate Creative with all my soul, but I also love their X-Fi's performance on the windows platform :???:

I understand about the gaming issue and it seems to stem from their doing a lot of processing with the CPU.
For my HTPC (using MythTV) this isn't a problem since I don't need wave tables etc.
The alternative is for me to spend six months reverse engineering Creative's interface so I can then understand ALSA well enough to add features to the CA0106 driver....

---

### Post by Trollslayer on 2008-06-26
> **jukingeo said:**
> Heh Heh, cute :roll: Anyway, I did do some searching right here in this forum and as it turns out the Sound Blaster Live, 24bit and Audigy DO have external models that plug into the USB ports.  Supposedly these versions of the INTERNAL card are supported by Linux, but there are those with Laptop computers that don't have compatible on-board sound devices and these people are trying to get the external USB sound devices to work.  So far I have been getting mixed results.  But it does seem possible to run an external sound card.



I have been sold on Creative devices for a long time now.  In fact for an external device, that is what I would want.  I only deviate from the Creative path when it comes to pro audio devices.

As of now I don't think there is a Linux based audio card that can handle 192khz frequency.  The X-Fi can do 96k and my Alesis IO-26 can do 192k in Windows.  Most of the Hammerfall cards only go up to 96k as well.  So for the X-Fi... that is a pretty impressive spec for a consumer card.

Now sure I can go with a Sound Blaster Live external USB device and it probably will work...but as far as I recall, the SB Live isn't 24 bit, it is 16 bit.  Also 48k is the highest frequency it can go.  Those specs aren't good enough for me for recording.  The card/device MUST at least do 24bit 96k with 192k being my preference. BUT in the very least with A sound card that works, I can at least test the waters with the Ubuntu Studio applications.  It gives me something to work with.  So it is better than nothing.

I think M-Audio may have some compatible external devices as well.  However, I know M-Audio's products and they are built like crap.  They have a very high failure rate among their computer based products out in the field.  Their keyboards are horrendous.  They constantly break.  Pure junk.  Go look on Musicians Friend and see how many bad reviews M-Audio products get.  Look how many Blem (B stock) M-Audio products they have in their clearance section.  The only thing decent M-Audio makes are the USB midi interfaces.

Anyway, I am going to do a little more of this ](*,) and then I am going to hit the sack.

Thanx,

Geo

For 192kHz card such as Razer support this on all outputs but USB is going to remain a problem as Creative won't release documentation on their devices.
I can only recommend that you try and find a way to use PCI as USB isn't the best real time protocol.

---

### Post by jukingeo on 2008-06-26
> **Trollslayer said:**
> For 192kHz card such as Razer support this on all outputs but USB is going to remain a problem as Creative won't release documentation on their devices.
I can only recommend that you try and find a way to use PCI as USB isn't the best real time protocol.

Ok, let's try a different path...Firewire.  That should be fast enough.

At this point I really really really would need a tremendously good excuse to tear the X-Fi card out of my machine.

For example, if I know that Ardour, Rosegarden, Hydrogen, Audacity can do what high end Windows programs can do such as Cubase, Sonar, Live, Fruity Loops and Soundforge...then that would give me more of an incentive to pull the X-Fi card out sell it off and my Alesis IO_26 and then I would splurge for a Hammerfall card.

I think at this state I do have to talk to people whom have set up successful professional studio's that are Linux based.  Granted that is not going to solve my problem, but at least it will tell me there are those out there that are using Linux for professional recording applications.

But as of now, I just really want to get sound out of and into my machine so I can see what these Linux applications can do.  And thus far, I can't even do that.

Thanx,

Geo

---

