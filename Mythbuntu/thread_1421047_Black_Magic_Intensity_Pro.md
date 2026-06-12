---
title: "Black Magic Intensity Pro"
date: 2010-03-03
forum: Mythbuntu
---

### Post by tk2kewl on 2010-03-03
Does anyone have any experience with the Black Magic Intensity Pro ([http://www.blackmagic-design.com/products/intensity/techspecs/)?]("http://www.blackmagic-design.com/products/intensity/techspecs/%29?")

I am still trying to plan my build and since I am using my set top boxes for tuning I need only video capture and display.  It seems like this card can provide both.

Also, since it has digital HDMI in and out it seems like it should improve performance over HDPVR-in as it doesn't need to be re-encoded for normal playback.

---

### Post by timconradinc on 2010-03-04
Two things to consider:

1 - Your HDMI may be encrypted from whatever box you're recording from. I really don't know the ins & outs of this, but even if your device isn't encrypted today doesn't mean it won't be tomorrow.

2 - This card likely is putting out an uncompressed HD stream of video. Which, in a nutshell, means you're going to have *very* big files. I don't think there's  a 'standard' bitrate for HD, but, it's going to be ~2x of that of the compressed format that the HD-PVR is putting out.

There's some other things in the back of my mind that might be issues, as well, like will the video work with VDPAU, but those might not be as important to you.

For ~$200, it's not a terribly expensive card. If you're new to MythTV and/or Linux, it's probably not the best thing in the world, since it'll likely take some finagling to get to work properly, if it works at all. 

I did a quick Google search, and didn't see much about anyone actually trying it. However, if you do try it and it works, report back and let us all know.

---

### Post by roundhay on 2010-04-21
I have started looking into this and there it looks like there is  way to get around the HDCP issues but it means buying another box!

[http://www.overclock.net/htpc/460359-snap-stream-hdmi-into-pc.html]("http://www.overclock.net/htpc/460359-snap-stream-hdmi-into-pc.html")

I have not found any good info on how to compress the HD signal going into the card which will be vital unless you have loads of HDD space

I'll post any more info I find

Edit - The Blackmagic Design website is now advertising that the Intensity Pro works with linux......

---

### Post by iamlindoro on 2010-04-21
Linux drivers, but no interface whatsoever to standard capture APIs in linux-- meaning for all intents and purposes, there is no linux driver.  If it's not V4L (it's not) and the API isn't public (it's not), it won't work with Myth.

---

### Post by ebharv on 2010-04-30
As for the HDCP issues, if the device has component out just use that it shouldn't have HDCP on it (but don't quote me it's just what I've been hearing over the net). I've also been to the website for the card and the company has released Linux software (through the support link). As I don't have the card yet I can't say if it works. But, here's why I'm here:

I want to do some video game montages and stuff and at first glance the Intensity Pro looks like the card to go with, but I'm hearing some crazy things as far as system requirements. You need a RAID array with LARGE drives, minimum quad core cpu only captures uncompressed video. 

Well I found out that the uncompressed part wasn't true but if you compress the video being captured it'll seriously tax your cpu. 

Can anyone give me their setup on the tuxbox they use cpu, memory, video card, linux version, sound card, hd size rpm raid/no raid, etc.? Or tell me if I'd be good to go with my system. (specs are in signature HD is WD caviar blue 500gb SATA 7200rpm)

P.S. I did check the requirements on the website weren't to specific.

---

### Post by tgm4883 on 2010-04-30
Where did you see the intensity pro is receiving compressed video? (or where did you hear it was not receiving uncompressed video?)

---

### Post by ebharv on 2010-05-03
> **tgm4883 said:**
> Where did you see the intensity pro is receiving compressed video? (or where did you hear it was not receiving uncompressed video?)
I can't even remember. I just googled "intensity pro capture card" and it was in one of the forums.

---

### Post by gst-kaps on 2010-05-31
Hey, 
You can try Blackmagic Gstreamer Plugins from Media-magic Technologies @ [http://mediamagictechnologies.com/products.html](http://mediamagictechnologies.com/products.html)
With the help of these gstreamer plugins you can capture HD video in any gstreamer application.

---

