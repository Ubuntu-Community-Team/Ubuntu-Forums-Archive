---
title: "How To Add (wifi) router when no modem available"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-08-28
My computer reaches the internet via wifi. I have a wifi adapter plugged in. I also have a wifi-router. How can I attached the wifi-router via the ethernet cable so that the wifi I have for the computer (via the adpater) can be shared with the wifi-router. I hope I'm making myself clear here. I want to have a wired connection available that get to the internet via my computer to wifi adapter to modem. The source of the internet is behind an apartment wall and I cannot run an eth cable to it.

---

### Post by kurt18947 on 2013-08-28
Sorry, maybe I'm more dense than usual but I'm not clear what you're trying to accomplish.  If you want an wired ethernet connection from WiFI, sure that's possible.

---

### Post by Mark_in_Hollywood on 2013-08-29
Three devices in the mix. The modem is not in this room. It's in another apartment. I have my computer reaching the internet via wifi. I want to connect a router to my computer via ethernet. I want to network from the ethernet router cable to an Raspberry PI ethernet port. I want to connect the PI (Raspbian) to the internet via the ethernet cable which connects to my computer which connects back to the (wifi) modem router in another apartment. I cannot run a cable (cat 5e) through the wall (landlord issues).

---

### Post by grahammechanical on 2013-08-29
The wireless adapter in my machine can be set up in 3 possible modes - Access Point (AP) mode, Infrastructure mode and Ad-Hoc mode. At the moment the wireless adapter is set up in Infrastructure mode. The machine is connected by wireless to an Access Point (the router/hub) connected to the telephone cable.

I can also set the connection to Ad-Hoc mode by editing the connection. In this mode the computer will communicate with other wireless stations (computers) without needing an access point (router connected to the Internet)

Access Point mode is not available by editing the connections but in System Settings>Network there is a button labelled use as a Hot spot. It appears when I select Wireless. I have never tried this but I think it should put the wireless adapter in the machine into Access Point mode. I am using Ubuntu 13.04.

I think Access Point mode is what you need in order to do what you want. You need to turn the computer connected to the Internet by ethernet into a wireless access point.

Regards.

---

### Post by Mark_in_Hollywood on 2013-08-29
I see I don't have a sufficient understanding of networking to describe what I am trying to do adequately. I will try again.

My computer has internet access via wifi. The internet is _got_ (obtained) via wifi adapter connected to this computer.

I have a router (it is also a wifi device, but I don't want a wifi connection via this device).

I want to get my internet access into this router via an ethernet cable from my computer. I want to share the wifi? signal? bandwidth? I can't say the right term here. I then want to connect another device via an ethernet cable and have internet access from that router.

---

### Post by kurt18947 on 2013-08-29
If I have it right, you could accomplish this with a wireless bridge, or perhaps better a router loaded with 3rd party firmware to make it a wireless bridge plus 4 port switch.  The repurposed router will gather in the wifi signal and redistribute it via up to 4 ethernet cables. I just used a Linksys WRT54G running DD-WRT to supply wired ethernet to a machine without a functioning wifi adapter in a location without an ethernet port.  Do these links help?
[URL="http://lifehacker.com/368094/wire-your-living-room-over-wi+fi-with-a-bridge"]
http://lifehacker.com/368094/wire-your-living-room-over-wi+fi-with-a-bridge[/URL]

How to install DD-WRT to make a commodity router into a wireless bridge/ethernet converter.  This gives 4 wired ethernet ports 'fed' by a wifi signal.  Be aware that not all consumer routers have this firmware available.
[http://www.makeuseof.com/tag/ddwrt-router-superrouter/http://www.makeuseof.com/tag/ddwrt-router-superrouter/](http://www.makeuseof.com/tag/ddwrt-router-superrouter/http://www.makeuseof.com/tag/ddwrt-router-superrouter/)

---

### Post by scbingham on 2013-08-29
I'd say the solution provided above by kurt is what you would like to achieve, however it will depend on the capability of the router that you have.

Alternatively, why not just get a wifi dongle for your Pi?

---

### Post by scbingham on 2013-08-30
Mark, would you like to share how you solved your problem? It may help someone else in a similar situation.

---

### Post by Mark_in_Hollywood on 2013-08-30
Due to my lack of understanding about both hardware, software and the complexities of "networking", I thought the easiest solution would be to send the internet through my computer through a router or switch and into the other devices. I had tried to understand how MythTV/MythBuntu worked. I could not understand whether my TV (a "smart" one with an ethernet port) was a "device" in MythTV-Buntu terms. I believed I needed a static IP address (I'm still guessing) for the TV, as I have both a computer monitor (which is also a tv, but not a "smart" tv) and the "smart" tv. My best understanding was confused by the term "front end role". (I'm not into role playing) I have a SiliconDust (HDHomeRun) dual tv tuner. (those guys should win the worst possible name for a company/device award, as I have to do searches for both names). This device uses an ethernet port to output the tv signal to the (you name it) device, router, wifi, ethernet switch, et al. and I would try and try to find the "over the air" tv signal and send it out to the "smart" tv via ethernet. I also want to have Hulu and/or NetFlix via the internet. I know that the bandwidth would be halved, but as the SiliconDust HDHomeRun tv tuner does the de-muxing itself, the bandwidth used is small, even on a 10/100 ethernet system. So as I played around with all this, I learned about tvheadend and torc and some other stuff people seemed to use to get their home theater to work, but every time I tried something it got worse. All this was compounded by the fact that with Google's Reader going away, I was trying to setup an Apache2 server in order to use TinyRSS. This went as well as the home theater stuff. After reading that new hacker software is recently available to break into the server (It's called: Hand of Thief), and as I don't want to be a system operator/webmaster, I have removed the Apache server apps. The Myth people call the myth a "server"  or "media server" The Apache people do likewise. I could never figure out whether if I installed Apache that would serve (be sufficient) for Myth's needs. Nor could I determine how to send the Myth tv picture through any server, Myth or Apache.

So, in response to SCBINGHAM, I have not solved my problem. And in a way, on reflection about my goals, I will say that going from forum to forum, e.g., Ubuntu Forum to Apache2 Forum to SiliconDusts' Forum, to this-that-and-the-next forum has shown me that my goals were simply too complex for an amateur, such as myself, to achieve. Not enough people had the same combinations of hardware and software and the same problems with setup/cofiguration/usage to generate useful information at these Forums. And that is completely understandable.

Having experienced all the forgoing, I changed my mind and decided to make a stand-alone home theater. Towards that end I started reading up about Raspberry PI, Raspbian, and XBMC. I may have misunderstood whether the PI would work over the wifi on first run boot up. My readings made me believe that I would have to run the PI to the internet via ethernet cable. That may prove to be untrue. I will be getting the last piece of the PI this week and then I will see if the PI Foundations NOOB (stand for New Out Of Box) OS will "do the wifi". It also offers a selection of 3 or 4 possible home theater configurations on 1st boot and I'm looking forward to that.

Thank you for your time in reading this.

---

### Post by scbingham on 2013-08-31
Not sure what happened to my reply :-(

Anyway, your Pi will use wifi from boot. xbmc is the way to go. I have it running on Openelec, which is a very cut down debian distribution.

Lots of info out there, have a read of: [http://www.makeuseof.com/pages/xbmc-full-html](http://www.makeuseof.com/pages/xbmc-full-html)

Try not to tackle too many things all at once, just concentrate on individual parts & I'm sure you'll manage to achieve all that you hope.

Good luck & enjoy!

I bought an sd card with Openelec & xbmc pre-installed for little more than the price of the sd card; gets you up & running even quicker.

---

