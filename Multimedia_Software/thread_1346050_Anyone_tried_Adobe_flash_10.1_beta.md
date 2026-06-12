---
title: "Anyone tried Adobe flash 10.1 beta?"
date: 2009-12-04
forum: Multimedia Software
---

### Post by ticket on 2009-12-04
Final version comes out early next year.
I think it supports GPU accelerated flash, hopefully under Linux.
Will we get decent flash performance at last?

---

### Post by skiani on 2009-12-08
I just tried it, not promising. Here's what I got on a 2.0GHz Core Due Laptop with Intel GMA 950 graphic processor.

Benchmark site:
[http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html](http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html)

Results:
[INDENT]Ubuntu 9.10 with Flash 10.0.32.18 (default):  20.1 frames per second

Ubuntu 9.10 with Flash 10.1beta:  17.4 frames per second

WindowXP with Flash 10 (latest release): 32.4 frames per second[/INDENT]

I didn't try the 10.1beta on windows to compare. It really sucks that Adobe has become so dominant yet can't provide good performance.

---

### Post by Yellow Pasque on 2009-12-08
[RANT]No, it's just the same old corporate **:
> In Flash Player 10.1, H.264 hardware acceleration is not supported under Linux and Mac OS. Linux currently lacks a developed standard API that supports H.264 hardware video decoding, and Mac OS X does not expose access to the required APIs. We will continue to evaluate adding the feature to Linux and Mac OS in future releases.

Nvidia wants to use VDPAU and Intel&ATI want to use VA-API. Adobe's press release translated means, "We don't give a *** about Linux." Blah blah blah...[/RANT]

---

### Post by markbuntu on 2009-12-09
VDPAU is just a nvidia blob and will be using the VA-API since that is what the players like mplayer and vlc would like to be using. The same people who wrote the VDPAU VA-API interface have also written one for ati's XvBA.

VA-API is used or is going to be used by all open source drivers and is already included in many players. So really, adobe is just confused.

You can read more about that here.

[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

---

### Post by ticket on 2009-12-12
> **skiani said:**
> I just tried it, not promising. Here's what I got on a 2.0GHz Core Due Laptop with Intel GMA 950 graphic processor.

Benchmark site:
[http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html](http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html)

Results:
[INDENT]Ubuntu 9.10 with Flash 10.0.32.18 (default):  20.1 frames per second

Ubuntu 9.10 with Flash 10.1beta:  17.4 frames per second

WindowXP with Flash 10 (latest release): 32.4 frames per second[/INDENT]

I didn't try the 10.1beta on windows to compare. It really sucks that Adobe has become so dominant yet can't provide good performance.

Thanks for that test site - quite useful!
On my old P4 1.5GHz, nVidia PCI 6200 I get 9Hz using the adobe 10.0.42 (karmic), so I guess that just reflects CPU performance.

---

### Post by ticket on 2009-12-20
Seems the acceleration is only for cards that also support VDPAU, ie. 8000 series upwards.

6xxx series not catered for:

[http://www.nvidia.com/object/gpus_supporting_adobeflash.html](http://www.nvidia.com/object/gpus_supporting_adobeflash.html)

---

### Post by scotty64 on 2009-12-21
> **ticket said:**
> Final version comes out early next year.
I think it supports GPU accelerated flash, hopefully under Linux.
Will we get decent flash performance at last?

I tried both beta1 and the recently released beta2. I have to say I have not tested the GPU acceleration as my main hope was that Adobe fixes the terrible camera support that was "introduced" with version 10.x - a lot of cameras that used to work well under version 9.x are not recognized anymore.
Sadly no progress here - you still need kludges to get these cameras to work with the 10.x flashplayer versions.

---

### Post by ticket on 2010-01-16
Can anyone confirm whether a

Acer Aspire Revo R3600, Atom 230 1.6GHz,1 GB RAM, HDMI, nVidia GeForce 9400 ION

can play YouTube HD online videos without stutter?

It clearly can play HD movies stored on disc, but playing HD flash presumably requires the Adobe 10.1 blob and it seems this may not work so well under Linux ???

---

### Post by Maybelline on 2010-02-02
> **ticket said:**
> Can anyone confirm whether a

Acer Aspire Revo R3600, Atom 230 1.6GHz,1 GB RAM, HDMI, nVidia GeForce 9400 ION

can play YouTube HD online videos without stutter?

It clearly can play HD movies stored on disc, but playing HD flash presumably requires the Adobe 10.1 blob and it seems this may not work so well under Linux ???

I just tried my Revo (btw, it's an 8400, not 9400) with some YouTube videos.  The windowed versions worked really well in 360p and 480p, but a 720p video was pretty choppy.  However, switching to fullscreen made things terrible in any resolution.  I have read that there is a problem that NVidia and Adobe are working on -- something to do with the first resolution you use.

So, the Revo is much more usable with Flash 10.1 beta 2, but it's not perfect.

---

### Post by sandy8925 on 2010-02-02
This might look unrelated but any of you heard of HTML 5 and the <video> tag ? Youtube now has html 5 support which (predictably) only works on google chrome so far. Dailymotion also has support for openvideo but it works on firefox.

---

### Post by Blightbow on 2010-02-05
I have both Windows 7 and Ubuntu Netbook 9.01 on a HP Mini 311 with a NVidia Ion (9400M equiv). I've tried the flash beta on both, and the Youtube performance on the Ubuntu side is nowhere close to how the 10.1 beta runs on Windows 7. The 10.1 plugin is properly installed, since Youtube video will not play at all if I rename my user's plugin folder.

Seems like Adobe just doesn't care. :\

---

### Post by domi007 on 2010-03-14
I have tried it, very impressive, a video which caused 100% CPU usage on my P4-M 2.2 GHz laptop and was not enjoyable with Flash 10.0 r45 works almost perfectly with the 10.1 beta (only 80% cpu, flawless terrific video playback! :D)


DOMy

---

### Post by alexcckll on 2010-03-15
Hmm - 80% CPU?  That seems a tad high..

Annoying that the Beeb have seen fit to lock out XBMC et al.. could Canonical use their clout to get some of the open-source solutions onto the BBC iPlayer whitelist?

I'm thinking of buying a netbook as well - am now concerned about whether the moel I go for would handle Flash iPlayer... my Thinkpad R61i handles it OK...

---

### Post by Xyphoid on 2010-03-24
Tried it on my Acer Aspire One A150 and it's still crap.
I can watch 480p Youtube and .mkv files without problems in XP. But Adobe still treats Linux like sh*t.

---

### Post by ticket on 2011-04-21
Announcement from Adobe, accompanying their recent 10.2 release:

H.264 Hardware decoding on Linux is available as an experimental feature and has been tested on NVidia GT 330 and Broadcom BCM70015 GPUs. Users may choose to enable hardware decoding by adding EnableLinuxHWVideoDecode=1 in an mms.cfg configuration file. Users may experiance instability and crashes while watching hardware accelerated video. Please report any issues to [http://bugs.adobe.com/flashplayer](http://bugs.adobe.com/flashplayer)

---

