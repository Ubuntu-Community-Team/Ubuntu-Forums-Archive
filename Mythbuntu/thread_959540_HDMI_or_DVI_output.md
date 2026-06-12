---
title: "HDMI or DVI output"
date: 2008-10-26
forum: Mythbuntu
---

### Post by thusgaard on 2008-10-26
Hi 

I'm trying to gather info for building a new frontend/backend solution. 

The frontend is going to be connected to a full HD screen (1080). How ever I'm not a TV or screen geek and I do not know if DVI is OK or if I need a HDMI output. 

Any recomendations to specific cards will be very welcome. 

And by the way which is better nVidia or ATI for that "it just works feeling"

Kind regards J;-)

---

### Post by ciscosurfer on 2008-10-26
It is often said that it depends on what your source is and what you plan on outputting to (which you've stated already).  Having said that, here are some quick links for you to get started:
[http://en.wikipedia.org/wiki/Hdmi](http://en.wikipedia.org/wiki/Hdmi)
[http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by SiHa on 2008-10-26
As far as video quality is concerned, DVI=HDMI. There is no difference at all in the digital video signal they are exactly the same. HDMI has HDCP (copy protection) added and includes audio over the same cable. 
So, a DVI-out card will be fine, with a DVI-HDMI cable, it will probably autodetect to 1080p as well.

One major caveat:

I'm using DVI-HDMI on my Panasonic 32" 720P set, using the external audio-in for the sound. No problems there.

**But**

We got a 19" Philips set for the bedroom, so we could use HDMI from the FE/BE in the loft (using S-video before - crap picture). On installation, I discovered that both HDMI inputs will only accept audio over the HDMI cable. So I've ended up using the VGA input - it's not quite as good up close, viewing something with sharp edges like a menu. But for general bedroom viewing it's OK.

So, check that the HDMI will work with separate audio-in.

Finally, based on my experience - go for nVidia every time - especially if you want to make use of the hardware MPEG decoding.

---

### Post by gilgongo on 2008-10-26
I've heard that HDMI sound support isn't too good yet. I've just built an HTPC for my living room (using XBMC and Hardy) and am using a DVI=>HDMI lead with a jack=>phono sound output to the TV. Works fine.

I also reccomend going with NVidia. I've had trouble with ATI chipsets.

---

### Post by thusgaard on 2008-10-26
Do you know of any graphics cards with HDMI and audio over HDMI?

Any thoughts on the video decoding. I'm thinking of going for an Atom motherboard. And I would for starters need to decode DVD quality video but what about HD quality video?

---

### Post by Helios1276 on 2008-10-26
I thought you could only get full HD from the likes of Bluray over HDMI?

---

### Post by newlinux on 2008-10-27
You can get Blu-Ray 1080p through DVI-D, so long as it supports HDCP.

---

### Post by gmoser on 2008-10-27
/agree with above posts.  I worked in the AV field for the past 8 years (did IT for an AV manufacturer).  The only real difference in HDMI vs DVI-D is the HDMI carries audio information as well as the digital video info.  It's a consumer standard that makes it easy for Joe Homeowner to connect his DVD player to his TV set and get a good picture and surround sound.  

I hooked my PS3 into my 22" WS monitor via HDMI - DVI cable and the images were AWESOME!  300 on bluray is AMAZING!  

For home theater HDMI is a good standard.  For HTPC situations I'd go with a DVI out (which I am still working on getting to look right - since I suck at Linux and can't get my ATI card with the DVI output to look right) and optical sound to surround sound receiver.

For the record, I currently have a Nvidia card running VGA out into my 46" LCD via VGA outputting 1920x1080 resolution and it looks great!  Granted, all my videos are 700mb AVI file I "aquired" but the standard desktop looks great!

---

### Post by newlinux on 2008-10-27
I should add, if you are playing Blu-Ray content in Linux, most likely you will have stripped all of its DRM, so HDCP won't be an issue anyway. You can play it back through whatever output your vidcard has.

---

