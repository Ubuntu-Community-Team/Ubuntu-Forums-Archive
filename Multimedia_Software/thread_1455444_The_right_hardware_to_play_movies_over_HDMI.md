---
title: "The right hardware to play movies over HDMI"
date: 2010-04-15
forum: Multimedia Software
---

### Post by bakegoodz on 2010-04-15
I'm trying to find the right combination of hardware to setup playback of my HD movie file collection to my 1080P TV. The plan includes a fairly long HDMI run, so I want to have both video and audio piped through HDMI. I want to use a ITX motherboard because of size, but I'll go to Shuttle XPC size if I need to. I have looked at Zotac ITX motherboard, but there is no mention of HDMI audio. Is there an reasonably priced adapter that will inject another source of audio into HDMI? Or do I need video card with sound support? Does the video cards with HDMI sound work with linux?
Thanks for any guidance you can give me.

---

### Post by VeeDubb on 2010-04-16
The #1 thing I would recommend is to go with nvidia.  nvidia GPU's are currently way ahead of the pack in linux with regaurds to hardware video decoding.  i.e. VDPAU.

You can get VDPAU enabled versions of mPlayer and possibly others that will take full advantage of it.  With the commercial nvidia drivers, you should be able to watch full 1080p hi-def video with about 10-20% CPU usage on an atom processor if you're using a VDPAU enabled player becasue all the video is off-loaded to the GPU.

Right now, the biggest ITX player for that market is Zotax.

The zotax ION-ITX series uses an atom CPU with nvidia 9400 ION graphics chipsets.  Perfect thing for a set-top box, which is what it sounds like you're talking about.  The ION-ITX A-U has it's own external power supply, which would allow you to have an ultra-small, silent or nearly silent system.

ASUS makes a comparable board which costs a little bit more, but comes with an IR remote control.



Also, if you do build a home theater box, I would STRONGLY encourage a few things:

1. Use Ubuntu Netbook Remix.
2. Use one of the two boards I referred to above.
3. Get a case that is either built for this type of board with it's own power, or has it's own external power block and just gut the one little power board that's in the case.
4. Put in the full 4GB of ram, but dedicate 1GB to the graphics chipset.  You can't use more than 3GB with UNR anyway because it uses the standard desktop kernel, and you'll want the extra video ram for watching video with VDPAU
5. Install Boxee.  Seriously, if it's for an HTPC, boxee beats all the rest.
6. Install the latest flashplayer 10.1 release candidate.  You'll need this for Hulu to function properly.



The one caveat here, is that even the latest release candidate of flash, does NOT support hardware video decoding of flash for linux users.  That means that you will not be able to play full-screen flash unless it's a lower resolution video.

If full screen hi-def flash is important, you'll either have to go with a Windows system, or upgrade to another mini-ITX board that will accomodate a desktop CPU.  There are several on the market, but the best ones are probably made by zotac right now.  I'd still recommend going with an nvidia-ION system.  Sadly, there is no way to make a **silent** system capable of full screen hi-def flash.

---

### Post by bakegoodz on 2010-04-16
I appreciate your effort, even though you rambled about things I didn't ask or care about. So does the Zotac Ion do HDMI audio?
Thanks for your time.

---

### Post by iponeverything on 2010-04-16
HDMI Audio appears to work with the Aspire Revo 3610, this does have the Nvidia chipset for VDPAU playback.

[http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option](http://www.greenhughes.com/content/how-install-ubuntu-910-and-boxee-beta-acer-aspire-revo-including-64-bit-option)

@VeeDubb -- Thanks, your post is quite informative.

---

### Post by bakegoodz on 2010-04-16
I think I might get this one
[http://www.zotacusa.com/zotac-g45-itx-wifi-lga775-g45itx-b-e.html](http://www.zotacusa.com/zotac-g45-itx-wifi-lga775-g45itx-b-e.html)

Because according to this [http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2)

Intel G45 has HDMI audio built into the kernel. Anyone confirm this?

---

### Post by VeeDubb on 2010-04-17
> **bakegoodz said:**
> I think I might get this one
[http://www.zotacusa.com/zotac-g45-itx-wifi-lga775-g45itx-b-e.html](http://www.zotacusa.com/zotac-g45-itx-wifi-lga775-g45itx-b-e.html)

Because according to this [http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=2)

Intel G45 has HDMI audio built into the kernel. Anyone confirm this?

I really wouldn't recommend that one.

It will never play 1080p video.

You should seriously consider re-reading my rambling post about unrelated topics, because it's all related, and fairly well eliminates the board you're looking at.

---

### Post by bakegoodz on 2010-04-17
"Never play 1080P"? Do you completely missed that the motherboard has a socket 775 and one can put a Core2 based processor on it. It looks as though a Atom 330 can handle just fine too, though I see the vaule of VDPAU. 

Atom cpu utilization of 1080p H.264 playback with and without VDPAU
[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_mobile&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau_mobile&num=1)

Same with a Core 2 (2008)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1)

---

### Post by VeeDubb on 2010-04-17
I guess I should have said it will never play 1080p video quietly and efficiently.

The thing is, by the time you have put a big enough CPU in there to make up for the lack of video decoding, you're going to have cooling issues.  You'll have a CPU fan, a case fan, a power supply fan, and a much larger case.

In short, your HTPC is going to be so large, and so loud, that you will have completely sacrificed every advantage of using a mini-ITX system, and you would do a whole lot better to just use a micro-ATX system.

There's nothing wrong with either option, but when somebody tells me they want an ITX media system, the point is usually small form factor and silent/near silent operation.

Stick with an Atom 330 w/ nvidia ION graphics and an external power supply, and you can watch 1080p video from a box that is absolutely silent except for the HDD.  Spring for a SSD and will be absolutely silent, in a box that is smaller than most bibles or dictionaries.

---

### Post by bakegoodz on 2010-05-29
Turns out the Video hardware can decode video 10x faster than CPUs can. Sorry for being snarky before, I am now a believer. 
VDPAU on ION based system is the way to go for a Home Theater PC and XBMC is an awesome player.

---

