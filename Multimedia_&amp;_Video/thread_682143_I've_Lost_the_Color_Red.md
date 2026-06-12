---
title: "I've Lost the Color Red"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by NotPhil on 2008-01-29
A few days ago my screen turned a bluish-green color. Initially, I thought the problem was with the monitor, so I unplugged it for a few hours. When I plugged it back in, the screen looked fine for a few minutes, and then lost the color red again.

I replaced the monitor and cable, but, still, no red. I've also tried removing the Nvidia (restricted) driver, but I still can't see any red on my screen.

Has anyone heard of a video driver suddenly losing the ability to process one color? Is there some other bit of hardware or software that could be causing this problem?

I have an AcerPower 1000 with a Nvidia GeForce 6150 video card and I'm running Ubuntu 7.10.

---

### Post by prabbit237 on 2008-01-29
> **NotPhil said:**
> When I plugged it back in, the screen looked fine for a few minutes, and then lost the color red again.

Red''s hiding behind Blue. (Sorry, I couldn't resist.)

On the serious side, it seems that you're not alone in this. I found the following on a google search:

[http://www.nvnews.net/vbulletin/showthread.php?t=106588](http://www.nvnews.net/vbulletin/showthread.php?t=106588)

(Also has no red. No-one replied to this person.)

[http://ubuntuforums.org/showthread.php?t=450734](http://ubuntuforums.org/showthread.php?t=450734)

(The folks in this thread are leaning towards software issues.)

[http://www.daniweb.com/forums/thread3260.html](http://www.daniweb.com/forums/thread3260.html)

(This poor soul is running Win98, which makes me think this is a hardware issue that's endemic with nvidia cards.)

 Try booting to a command-line only, be it DOS or linux, and see if it's white or blue-green. If it's white, it's (possibly) a driver issue (I say "possibly, since the VGA output might use different parts of the card than the higher-res outputs.) If it's blue-green, it's definitely a hardware issue. Also it's kinda funny that I did a search for the words "red", "nvidia" and "card" and got the above three in the first 35 hits but searching for "blue" or "green" didn't seem to match anything (i.e. it's only red that folks are losing.)

---

### Post by NotPhil on 2008-01-29
> **prabbit237 said:**
> I found the following on a google search:It looks like they're having problems connecting their Linux box to a TV. But I'd just like to have my computer monitor display the correct colors again. 

It's odd. My system has worked correctly for a little over a year. But not now. And this didn't happen after a software update. The system just stopped showing red one day.

> **prabbit237 said:**
> Try booting to a command-line only, be it DOS or linux, and see if it's white or blue-green. The console is light-blue text on a black background now. 

Are there any other 3D graphics cards out there that have Linux drivers besides Nvidia?

---

### Post by prabbit237 on 2008-01-30
> **NotPhil said:**
> It looks like they're having problems connecting their Linux box to a TV. But I'd just like to have my computer monitor display the correct colors again. 

I don't think the last one (with win-98 on his machine) was doing so but there was the common thread of "red has gone AWOL" in all of them.

> **NotPhil said:**
> It's odd. My system has worked correctly for a little over a year. But not now. And this didn't happen after a software update. The system just stopped showing red one day.

More reason to suspect the hardware rather than software.

> **NotPhil said:**
> The console is light-blue text on a black background now. 

Is that the console if not running X at all or the console in an xterm window? The xterm window uses the X drivers but booting linux into text-only mode wouldn't. So if it's in text-only mode, even more reason to think it's a hardware issue.

> **NotPhil said:**
> Are there any other 3D graphics cards out there that have Linux drivers besides Nvidia?

On that, I'll defer to others. I'm not the gaming or "whizz-bang, gotta have the flashiest screen-saver" type (no offense tp those who are; I'm just not one of your ranks) so all I care about is "does my command line show up ok? How about my webpages? Email? Word processing? Occasional photo-editing? Movies show OK? etc." so I don't worry about the graphics card that much. As long as it can boot into windows or linux, I'm happy as a clam.

---

### Post by NotPhil on 2008-01-30
> **prabbit237 said:**
> Is that the console if not running X at all or the console in an xterm window?I tried booting into the safe terminal session, which gives me a muddy blue-green background with a light blue-green square with black text in the bottom-right corner of the screen, and I've tried using [ctrl]+[alt]+[F(number)] which gives me a black screen with light blue-green text. I've also tried running another distro's live CD (PCFluxBoxOS), which also won't show the color red.

I still get intermittent moments with the correct colors on my screen. I read in another thread that Nvidia has released a new driver for Linux, which corrects some problems, including, apparently, the graphic card's fan not running correctly, but I can't say whether this will help. You can't install it through Gutsy Gibbon. Presumably, the console modes and the other distro weren't using Nvidia's driver anyhow.

> **prabbit237 said:**
> More reason to suspect the hardware rather than software.I suppose. It's tough to imagine what would only affect the color red, though. I don't think the connector is color-separated that way (it looks like a 15-pin socket), and I don't know whether the hardware processes the colors separately or not.

I guess I'll take it into a shop. Thanks anyhow.

---

### Post by prabbit237 on 2008-01-31
> **NotPhil said:**
> I suppose. It's tough to imagine what would only affect the color red, though. I don't think the connector is color-separated that way (it looks like a 15-pin socket), and I don't know whether the hardware processes the colors separately or not.

I guess I'll take it into a shop. Thanks anyhow.

Actually 15-pin VGA **is** seperated out into RGB signals (see [http://www.technick.net/public/code/cp_dpage.php?aiocp_dp=pinconvid_vga_15pin](http://www.technick.net/public/code/cp_dpage.php?aiocp_dp=pinconvid_vga_15pin) for details. But S-video doesn't.) The hardware would process the colors separately (and then combine them for an S-Video output.)

---

