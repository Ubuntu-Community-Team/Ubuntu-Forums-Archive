---
title: "HDHomeRun PRIME vs Firewire HD Cable Box"
date: 2014-02-03
forum: Mythbuntu
---

### Post by Senkoboy on 2014-02-03
I am getting ready to upgrade my cable package to HD., Now I only get my local channels in HD.   The HDHomeRun PRIME appears to work well with myth from what I have read, just have to get a cable card.  I will be getting a HD box from the cable company, (Suddenlink).  How hard is it to get a cable box working with Firewire?   From what I have read the firewire also controls the channel changing, no need for a IR Blaster?  I have a Intel BLKDP35DPM motherboard with IEEE 1394a port.  New install of Mythbuntu, 12.04, Myth .25

Thanks

---

### Post by TheFu on 2014-02-04
There is another thread here from the last few weeks about the HDHR-Prime. Worth reading.  I don't have a PRIME, but do own 2 HDHR3 tuners for OTA stuff now that comcast encrypts everything. They completely rock.... NOT!  The HDHRs a fantastic.

I was never able to get firewire to work. Perhaps I'm an idiot? Yes, it is required to be enabled by law in the USA, but there isn't anything else required, so actually getting what you want from the firewire will be dependent on the protocol used by the STB. Also, there is no requirement that the firewire stream be 1080p/i or even 720p output.  Content providers are doing more and more to _close the analog hole_.  I use component video and a few friends who do this too use component video.

So - if you can make the firewire change channels, then you will not need an IR blaster.  The best IR blasters are 98% effective, so once in a while, the wrong thing will be recorded. Until you get things setup just right, that could be 80% effective.

With the HDHR-Prime, you don't need to worry about the cablebox. Channels will be tuned perfectly. It is a much, much easier solution. Plus the myth-back-end can be anywhere on the network, not near the TV at all.

---

### Post by Senkoboy on 2014-02-13
I ended up with a Pace RNG 110 cable box.  I am going to try to get this working before I look into buying a HD Home Run Prime.  My Myth backend setup shows the Pace box, Pace RNG110 Aspen Jedi_linux, but I cannot get it to lock onto a channel. I tried a couple of different settings in the backend setup, Dct6200, ect...  I think my problem is when I go the the Diagnostic menu on the cable box, #21 Interface status, it shows 1394 status: disabled.  I guess this is my current problem, need to have a chat with my cable company.

---

### Post by uteck on 2014-02-14
I was using a Hauppauge HDPVR connected to my cable box with component cables, so the best I got was 1080i, but I had no worries about content flagging or other DRM crap.  I was going to use the Firewire on the cable box but I could not get anything from it, and even if I could people said only the over the air channels were available, so I just used it to change channels.

If you think 1080i is not good enough, you should check what signal you are getting out of your cable box.  Many channels are 720p or 1080i, and they rely on your TV to up-convert the 1080i to 1080p.  So you may not lose any resolution by using an analogue capture device like the HDPVR.

---

### Post by Senkoboy on 2014-02-14
I called the cable company this morning. They said the 1394 (firewire) ports were turn off by the manufacturer, couldn't be turned on.  I ask about the federal regulation that required them to furnish me with a cable box with a working firewire port, she said I was wrong.  I should just go buy a HD Prime, but for now I will fight this a little longer, they pissed me off.  The good news is the CCI on the channels I want to record is 0X00, copy freely.  My Pace cable box outputs 720P or 1080I, my TV is only a 1080I anyway.

---

### Post by TheFu on 2014-02-14
[http://www.avsforum.com/t/936410/firewire-on-set-top-boxes-legal-requirement](http://www.avsforum.com/t/936410/firewire-on-set-top-boxes-legal-requirement) has references to the FCC mandate being overthrown in court. This would apply only in the USA. A few of my friends are holding onto old STBs due to this.

---

### Post by Senkoboy on 2014-02-15
From 2010:

1394 and other outputs

Many manufacturers have long asked the FCC to eliminate its requirement that all HD set-top boxes include the little-used IEEE 1394 output, but so far had obtained only temporary waivers. Once the Order goes into effect, the 1394 output is no longer required, although cable operators will remain required to provide an HD set-top that includes a 1394 interface to customers on request.

On July 1, 2011, two-way HD set-top boxes must include an interface capable of delivering recordable high-definition video and closed captioning data in an industry standard format. The Order names as examples several IP-based interfaces such as Ethernet, Wi-Fi, USB, and MoCA, but does not limit operators to IP.

Effective Dec. 1, 2012, two-way HD set-top boxes will also have to comply with an open industry standard that provides for service discovery, video transport, and remote control command pass-through for home networking.

The FCC exempted one-way, nonrecording HD DTAs from the specific interface output requirements.

---

