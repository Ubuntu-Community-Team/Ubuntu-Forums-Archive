---
title: "Large Deployement"
date: 2008-10-17
forum: Mythbuntu
---

### Post by marcellodj on 2008-10-17
Morning,
i'm investigating about adoption of mythbuntu in our school multimedia lab.
We want use mythbuntu as backend server for approx 25-30 front/end clients (diskless, xbmc or other):
anyone experienced with similar scenarios? how about server specs, usability, bandwith, user experience?
thanks for replies.

---

### Post by newlinux on 2008-10-17
what kind of content do you want to serve (TV recordings, livetv, videos, music? HDTV? x.264?). If you aren't serving TV you might want to go with a fileserver and then just run XBMC or geexbox or something else.

---

### Post by marcellodj on 2008-10-17
THe lab is used for language training/teaching, so we want setup a VOD system to share dvd-rips and audio tracks in foreign languages; also if possible we want use myth to eventually stream dvb sats, but is an option.

Thanks for interest, have a nice day.
marcello.

---

### Post by mrand on 2008-10-17
> **newlinux said:**
> what kind of content do you want to serve (TV recordings, livetv, videos, music? HDTV? x.264?). If you aren't serving TV you might want to go with a fileserver and then just run XBMC or geexbox or something else. Related to the content question... the most important question may be: what bit rate is your content?  Also, can all nodes will be equipped with Gigabit Ethernet interfaces?

You can probably see where I'm going with this... bandwidth (both network, computer bus, and disk) may very well be an issue for serving video to that may users at the same time.

You can probably get around the disk bandwidth issue by using one of several RAID configurations.  You'll have to research your bandwidth demands against real-world reports to see if you require a hardware controller (or perhaps two to obtain duplexing).  If you do go with a hardware RAID controller, buy a spare or two at the same time to have on hand.  For the network side, you might want the server to have multiple Ethernet cards, with each network segment having between 5 to 15 clients.

My advice: don't skimp on the server.  Get one that has known good bandwidth numbers for the memory, disk, and bus interfaces.  With high def coming on quickly, don't underestimate the bandwidth, and reserve a little room for expansion to more clients.

[INDENT]Marc[/INDENT]

---

### Post by iponeverything on 2008-10-17
I would be very interested to hear about your experience. One master feeding 30 slaves -- my oh my - The I/O alone -

I am sure it can done and someone will have good time with the project. The main things I would start with..

- Disk I/O.
- Tons of memory.
- Lots and Lots of raw power.
- Maybe split lab into two segments, each fed with Gigabit interface.
Each client will need between 4-5 Mbps. 

Ok say 15 clients:

5*15 = 75 Mbps 

One Gigabit card - 115 MB/s real bandwidth.  Not to mention the limitations of the PCI bus..

---

### Post by marcellodj on 2008-10-17
I know that mythtv is made for home user, that s clear, so i drop the idea to stream live video feeds.

I m considering to build a robust NAS with samba, multihomed with 2 or more gigacards, and convert all my multimedia content to flv or flash like formats and using xbmc like frontend.

Thanks again for suggestions. m

---

### Post by rschapman on 2008-10-17
I work as an instructional technologist at a university and we played around with this as well and started doing some testing. We used the windows mythtv player with some success on the client side. The big issue was copyright. As far as TV we relied heavily on the Cable in the Classroom list to deal with tv shows. Ripping DVDs and the like is a different story. Technically as the laws now stand the only exemption allowed are for those in film studies classes to rip DVDs and bypass encryption and stream copy written material. It's a dumb law and one that will hopefully get changed. There is also a huge debate over transcoding of material for distribution. Before investing too much in any streaming solution I would suggest setting aside a few hours to read up on the insanity that is fair use and the TEACH Act. It's one thing to do this stuff at home but when you expose a school to it that changes the game. Good luck.

---

