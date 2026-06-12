---
title: "Unable to use Catalyst with fglrx"
date: 2012-05-11
forum: Multimedia Software
---

### Post by popejeremy on 2012-05-11
I have a fresh install of 12.04 (64 bit) on an ASUS M2A-VM motherboard (Integrated ATI Radeon X1250-based graphics) going into my LG 52" plasma TV via DVI/HDMI.

I was getting choppy video with the default install, so I did a "sudo apt-get install fglrx" and a reboot. The playback is no longer choppy (good!) but now there's a new problem. When I start a video (in this case an AVI of Star Trek: The Next Generation) the visuals are speeded up while the audio remains normal. The visuals eventually sync up to the audio over a few minutes.

So I should just open up Catalyst and do some tinkering there right? Well, when I click on the Catalyst icon I get this:

> There was a problem initializing Catalyst Control Center Linyx edition. It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.

Please install the AMD driver appropriate for your AMD hardware, or configure using aticonfig.

Of course, I try command lineing "aticonfig" where I'm told "aticonfig: No supported adapters detected". But I clearly remember installing fglrx just a few minutes ago!

In the mean time I've minimized the movie player application. Why don't I full screen it again and see where we are? Well, now the video is speeded up for two seconds and then it halts and then speeds up again. I leave it run for about five minutes but it never syncs up to the audio again.

This is all very strange, since I definately installed fglrx and after I did the behavior of the movie playback definately changed. So I double check. I open up the Additional Drivers application and am told that "No propriety drivers are in use on this system."

What in the world is going on here, and how can I fix my video playback?

---

### Post by Victicom on 2012-05-13
So far, I've found this post to be very helpful with AMD/ATI:  [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

### Post by popejeremy on 2012-05-13
Thanks for showing me that page. It stresses that you fully purge any old drivers and configurations when installing a new one, which I have done. I have followed the instructions on that page verbatum. At this point I have:
[LIST]
[*]Used the default configuration (choppy playback)
[*]Used fglrx from the repository (random speed-up/slow-down, and Catalyst won't run)
[*]Installed version 9.3 of the official proprietary driver as instructed by ATI's online documentation (it crashes X and Catalyst won't run)
[*]Installed version 12.4 of the official proprietary driver as suggested by a random Website (it won't even install, not compatable with any Ubuntu later than 9.04)
[*]Cried
[/LIST]
Solution: I just ordered an nVidea card from Amazon. It will be here in two days.

---

### Post by Victicom on 2012-05-14
Popejeremy,

I don't blame you for ordering NVIDIA, however, there is a compatibility issue with fglrx/Catalyst and Kernel 3.2.

In those links I sent there is a, well... link to a work-around where you can install the patch that will allow fglrx/Catalyst to work. That pretty much fixed things for me.

In case you missed it, here is the link:

[http://ubuntuforums.org/showthread.php?t=1969827](http://ubuntuforums.org/showthread.php?t=1969827)

---

### Post by QIII on 2012-05-14
The problem here is NOT the compatibility of the 12.4 driver with the kernel -- unless you build it from the ATI website.  The 8.960 package works fine.  That is simply the pre-release that Ubuntu got (Ubuntu gets the goods before everyone else every 4th and 10th month.)  The 8.961 package is the release everyone else besides Ubuntu has to wait for.  The driver from the Ubuntu repo works flawlessly.

The problem is that the indicated GPU is "legacy".  The legacy driver is  required to run it, but that driver does not work with recent versions of  xserver.  NVIDIA also has legacy cards that will not work, so it's not just ATI.

I use the 12.4 driver in both Precise and Queztal without any issues.

Please.  FUD doesn't help anyone.

This is simply an old GPU that is no longer supported.  It needed to be replaced, either by a newer ATI card or a newer NVIDIA card.  There is nothing magical about NVIDIA making it work.  In fact, the latest NVIDIA driver has caused some users difficulty.

Both ATI and NVIDIA make good products.  Sometimes there are hitches with drivers in each.  This is how the world is.

---

### Post by popejeremy on 2012-05-15
Victicom, I followed your instructions and installed the patch. The ATI card still doesn't work. I'll install the nVidea card tomorrow.

QIII, just because you use the drivers without any issues proves nothing. You've added nothing to the conversation, and that's no FUD.

---

### Post by Yellow Pasque on 2012-05-15
> **popejeremy said:**
> QIII, just because you use the drivers without any issues proves nothing. You've added nothing to the conversation, and that's no FUD.

The FUD comment may have been unnecessary, but everything else in that post is true. You can't install Catalyst 9-3 on modern Ubuntu. You can install Catalyst 12-x, but it's not going to work on your legacy card.

Didn't you read the big, red warning here?: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

### Post by popejeremy on 2012-05-15
I just got the card in the mail -- ASUS GeForce 8400GS. I plugged it in, and it worked with no hassle whatsoever.

---

### Post by popejeremy on 2012-05-15
> **Temüjin said:**
> Didn't you read the big, red warning here?: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Yes, I did. And it doesn't mention anything about legacy cards whatsoever.

Know-it-all jerks like you and Qlll are the reason why people hate Linux.

---

### Post by Yellow Pasque on 2012-05-16
I suggest working on your reading comprehension, and that's about the nicest thing I can say to you. Good luck.

---

### Post by Victicom on 2012-06-10
I am glad that you were able to work out your problem.

As far as the FUD comment goes, what is FUD? Best I can think of is "Fear, Uncertainty, and Doubt." At any rate, I wasn't truly aware that your card was legacy, as I am not fully aware of such things... In any such case, I do offer an apology as it was not my intention to mislead you, but to share with you something that helped me, and something I thought would help you.

As for the rest of the comments, the red warning and what not... I did write a lot, my original response was going to include that very fact... however, for some reason this Text Editor acts up on me for some odd reason so I was left with no option other than to respond with a single line.

I will repeat, however, that I am glad to hear that things worked out great for you.

Cheers.

---

