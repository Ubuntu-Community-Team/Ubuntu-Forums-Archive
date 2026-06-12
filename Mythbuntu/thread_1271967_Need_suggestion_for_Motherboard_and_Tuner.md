---
title: "Need suggestion for Motherboard and Tuner"
date: 2009-09-21
forum: Mythbuntu
---

### Post by TTGator on 2009-09-21
I have a headache reading about so many different things!  So many terms I'm not familiar with (yet!).

I would like a suggestion for a good deal on a motherboard and tuner.  Here are the knowns:

   * I'll be running Mythbuntu 9.04
   * I bought [this case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129054") already, so I know I need a micro ATX motherboard
   * I only need OTA channels with my antenna
   * I would like a dual tuner

Suggestions?  (Of course I would like it to be as cheap as possible, but that's not the most important factor)

---

### Post by mitchell2345 on 2009-09-22
- Motherboard
   Really personal pref.  I have always had good luck with Asus.  I normally stick with AMD as the price is a lot less and they provide plenty of power for Myth.  Also look for a intigrated Nvidia 9200+ video card.  This will allow you to use VDPAU when .22 comes out (soon).  This puts the actual playback 100% on your GPU.  You then use your AMD proc for commflag, schedulig, http, etc.

- tuner
  Best advice I ever took was the HDHomeRun as a tuner.  While not the cheapest it is by far the easiest.  I have purcharsed PCI versions of cards and its always a fight to get the correct firmware installed.  Almost gave up and bought a new hdhr.

GL,
Mitchell

---

### Post by TTGator on 2009-09-22
Well, I finally found a site that specifically listed some motherboards that weren't from 2008.  I mostly took your advice w/out knowing it :)  Here's what I have so far...

[ASUS M3N78-EM AM2+/AM2 NVIDIA GeForce 8300 HDMI Micro ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131354")
So it's Asus and AMD, but it has an integrated 8300.  Will this not allow the VDPAU you mention?

I also ended up going with the HDHomerun.  I've only heard people say good things about it, so figured it was probably worth a few extra bucks.

---

### Post by williammanda on 2009-09-22
Try this site:

[http://ubuntuforums.org/showpost.php?p=7989230&postcount=7]("http://ubuntuforums.org/showpost.php?p=7989230&postcount=7")

---

### Post by TTGator on 2009-09-22
Williammand, that's the exact place I found the Asus board I went with.  I see now that the one you recommend has the 9300 integrated.

---

### Post by mitchell2345 on 2009-09-22
> **TTGator said:**
> Well, I finally found a site that specifically listed some motherboards that weren't from 2008.  I mostly took your advice w/out knowing it :)  Here's what I have so far...

[ASUS M3N78-EM AM2+/AM2 NVIDIA GeForce 8300 HDMI Micro ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131354")
So it's Asus and AMD, but it has an integrated 8300.  Will this not allow the VDPAU you mention?

I also ended up going with the HDHomerun.  I've only heard people say good things about it, so figured it was probably worth a few extra bucks.

The 8300 will do VDPAU fine.  It is limited on the de-interlacing it can do.  If you get in the 9000 series cards you can do advanced 2x.  

Either way you have a good board.

Mitchell

---

### Post by TTGator on 2009-09-22
That's good to know.  A brief read about Myth and VDPAU sounds like I have to recompile Myth to get the VDPAU support?  Is that only until .22 or something?

---

### Post by mitchell2345 on 2009-09-22
> **TTGator said:**
> That's good to know.  A brief read about Myth and VDPAU sounds like I have to recompile Myth to get the VDPAU support?  Is that only until .22 or something?

no, you can use the VDPAU repo by jean avenard or wait until the .22 stable packages come out.

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Mitchell

---

### Post by williammanda on 2009-09-22
> **TTGator said:**
> That's good to know.  A brief read about Myth and VDPAU sounds like I have to recompile Myth to get the VDPAU support? 
Follow this post to get VDPAU without compiling.

[http://ubuntuforums.org/showthread.php?t=1063102&highlight=vdpau]("http://ubuntuforums.org/showthread.php?t=1063102&highlight=vdpau")

> Is that only until .22 or something? Yes

---

### Post by TTGator on 2009-09-22
Mitchell,

Since you have pretty much the same setup that I will have, can I ask you a couple more questions?  I have my hardware ordered and it should be here in a couple days.  One thing I don't have yet is a wireless keyboard/mouse.  I already own a Logitech 890 remote, and assume I can use this with the HTPC.

Can you tell me how you control yours?  (i.e. remote, keyboard, etc)  And how does the HDHomerun play into it all?

---

### Post by mitchell2345 on 2009-09-22
> **TTGator said:**
> Mitchell,

Since you have pretty much the same setup that I will have, can I ask you a couple more questions?  I have my hardware ordered and it should be here in a couple days.  One thing I don't have yet is a wireless keyboard/mouse.  I already own a Logitech 890 remote, and assume I can use this with the HTPC.

Can you tell me how you control yours?  (i.e. remote, keyboard, etc)  And how does the HDHomerun play into it all?

i don't have a wireless mouse/keyboard. very rarely have a need for it.  Just use VNC when i need console access.  

I use a MCE remote receiver with my Harmony 880.  The HDHR sits in the basement.  

You could use the HDHR as your IR receiver to your harmony 890 but i have never done this. Just configure Mythbuntu for a media center remove and your harmony the same.  then do the configuration for the hdhr + lirc (have not done this before)

Mitchell

---

### Post by bsntech on 2009-09-22
I see that Asus motherboard has the GeForce 8300 video card - and mitchell indicated it will do VDPAU.

What about the GeForce 8100 or 8200 cards?  Is there a better site that details what cards will allow VDPAU support?

---

### Post by mitchell2345 on 2009-09-22
> **bsntech said:**
> I see that Asus motherboard has the GeForce 8300 video card - and mitchell indicated it will do VDPAU.

What about the GeForce 8100 or 8200 cards?  Is there a better site that details what cards will allow VDPAU support?

please read the entire post before posing...a few messages back:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)


There is a TON of good info on the MythTV wiki.

Remember this is for .22 or unsupported backports.

Mitchell

---

### Post by williammanda on 2009-09-22
Here is another resource for the VDPAU support, it shows the core names supported as well. Also the mythtv wiki doesn't show my card (9600 GT) supported but this one does.

[http://en.wikipedia.org/wiki/VDPAU]("http://en.wikipedia.org/wiki/VDPAU")

---

