---
title: "Watching TV from my Raspberry PI?"
date: 2016-03-09
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2016-03-09
Can I watch what is on my Raspberry PI's, OpenELEC's, Kodi via the ethernet? I'm sorry I don't even know how to form this question properly. The Kodi connects to my home's TV. I would like to see what it sees but on my computer/monitor. I don't want live tv. Streaming from the 'net is what I'm after. I know that the computer and the Pi/OpenELEC/Kodi are on the router. That's about it.

The Pi/OpenELEC/Kodi has an HDMI out to the TV. The TV, while it has an ethernet port, isn't connected directly to the home network. The TV is IPTV DLNA "ready", if that helps to know at all.

The computer's IP is: 192.168.1.65
The Kodi's IP is: 192.168.1.136

Does the PI/OpenELEC/Kodi do the "serving", or can my 14.04 just go look at it over the network? What multimedia app can do this? I do have VLC on the 'puter.

---

### Post by goofprog on 2016-03-09
I know what a Raspberry Pi is.  It is a small combat computer so yea you can watch TV from it by using a TV tuner USB adapter.  Make sure it captures digital broadcasts because all American channels are now digital.  (well that is if you are in America.)  Steaming?  Just set a movie player to capture streaming on the LAN.  I recommend VLC for that.

---

### Post by howefield on 2016-03-09
Doubt you'll have much luck with that, probably best to install Kodi on to the PC.

Any local files that you have on the Pi machine can be accessed over the network and played on the PC but streaming what Kodi is playing (which would normally go over HDMI) is a no go, I'd suggest.

---

### Post by ken73 on 2016-03-10
You should be able to get Kodi to work on your Pi with Openelec.
Go to [http://openelec.tv/get-openelec](http://openelec.tv/get-openelec) and scroll down to the Pi sections.
Once you have it installed do a search on Kodi and addons and you will find information on how to add the streaming add ons that will let you watch stuff.
I have it working on Pi 2, Hummingboards and a Cubebox even with my crappy satellite internet.
As to the TV part, it is really only a monitor/speakers and needs to have an input that is compatible with your Pi, HDMI for example.

---

### Post by howefield on 2016-03-10
> **ken73 said:**
> You should be able to get Kodi to work on your Pi with Openelec.
Go to [http://openelec.tv/get-openelec](http://openelec.tv/get-openelec) and scroll down to the Pi sections.
Once you have it installed do a search on Kodi and addons and you will find information on how to add the streaming add ons that will let you watch stuff.
I have it working on Pi 2, Hummingboards and a Cubebox even with my crappy satellite internet.
As to the TV part, it is really only a monitor/speakers and needs to have an input that is compatible with your Pi, HDMI for example.

Sounds like Mark_in_Hollywood already knows that and has that part set up already.

---

### Post by SeijiSensei on 2016-03-10
I tried watching video on a first-generation Pi using the HDMI port and found it too underpowered to be very successful.  Anything in 720p format and encoded with H.264 will have problems.  

I don't know much about Kodi.  Does it provide a DLNA server?  If so, have you tried connecting to that?

If it doesn't have a DLNA server, you might look into installing minidlna on it.  I stream to devices like phones and tablets with that.  It's pretty easy to configure, too.  You just need to specify the directories where the media files are stored and start it up.  A little browsing suggests that minidlna isn't packaged for OpenELEC, so you'd need to install gcc on the Pi and compile minidlna from scratch.

It sounds like you want both devices to display the same video simultaneously.  I don't think that can be done.

---

### Post by Mark_in_Hollywood on 2016-03-10
Thank you Linux Community.

---

### Post by Mark_in_Hollywood on 2016-03-11
After much searching, I see that what is needed is an HDMI switcher and a cable from the switcher to the computer monitor. The Pi/OpenELEC/Kodi acts as the signal source and the switch selects either the TV or the computer's monitor. The switch, in 2016 prices is about $10 and the 25 foot HDMI cable is $12. Easy enough.

---

