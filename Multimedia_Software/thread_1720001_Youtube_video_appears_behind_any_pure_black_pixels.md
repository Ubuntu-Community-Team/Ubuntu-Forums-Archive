---
title: "Youtube video appears behind any pure black pixels on screen"
date: 2011-04-02
forum: Multimedia Software
---

### Post by elsporko on 2011-04-02
Hey all. This is a really tough problem to describe, since I've tried to take screenshots of the problem but they show up normal.. If nobody understand what I'm talking about, then I'll try to post some pictures with my regular camera when it happens again :P

So lately I've noticed that if I play a youtube video, the video shows up behind any pure black pixels on my screen. As I type this, I can see the black pixels that make up the text, lines of the message window, etc, show the video playing. It's like the black pixels are just a window that you can see through to see the video playing :P

I opened VIM to work on a CS assignment, and since the background of my VIM theme is just flat black, the entire youtube video shows up clearly, with the text in VIM overlayed on top of it. It happens with a terminal open as well, since my terminal background is flat black.

The only way I've found to fix the problem is to do a full restart of Ubuntu, or to log out and lock back in. I've reinstalled flash, and it's made no difference. This happens with any program that has any sort of flat black pixels, and it makes no difference whether the video is or was playing in firefox, chrome, etc. After the video is finished, the effect remains with a glitchy still-image of the video and the screen that shows up once a video is over. Even if I close the video, the image stays there until I restart or log in/out.

I should add that it doesn't matter what program or window is open or what's behind the windows, it will still show up. I've tested it with a flat black desktop background, and it looks like the video is playing entirely on my desktop.

Has anyone had this happen to them before? I'm running Ubuntu 10.10 if it matters, and have an Nvidia card.

Thanks everyone :) Like I said before, if it's not clear what's going on, I'll try to take some pictures of it happening and upload them, since the last time I tried to take a screenshot, the effect wasn't actually visible in the screenshot for some reason (Imagine trying to take a screenshot to show where a monitor's dead pixel is :P)

---

### Post by tomobson on 2011-04-02
just got this problem.  i'm new to ubuntu so i won't be much help to you.

---

### Post by andrew.46 on 2011-04-03
Might be well worth your while to disable hardware acceleration for flash videos on youtube. Try right-clicking on a flash video, going to settings and un-checking the hardware acceleration option. Not a guarantee but it cures many odd flash related problems.

---

### Post by elsporko on 2011-04-04
Tried disabling hardware acceleration like you'd mentioned, no luck :\ the problem occurred again a few minutes later.

---

### Post by andrew.46 on 2011-04-04
> **elsporko said:**
> Tried disabling hardware acceleration like you'd mentioned, no luck :\ the problem occurred again a few minutes later.

In that case I am out of ideas :(.

---

### Post by Bruno Lima on 2011-04-11
Hi, i've got the same problem.

Remove the flash.
Download and install it again, but this time use "Ubuntu Software Center".

I think that there's a problem with the official *.deb file, from Adobe wesbite.

---

### Post by tamas413 on 2011-04-28
This bug is irritating. It's really bad when the video was white. The text then turns white and is unreadable.
It's like whatever Flash video was last played on the screen, it takes the place of anything purely black on the screen (even after the plugin and browser are closed).

Latest Flash installer from the Canonical repositories as well as the latest proprietary nVidia driver.
Video Card: nVidia 9600M GT

---

### Post by WannabeFantasma on 2011-04-29
> **tamas413 said:**
> This bug is irritating. It's really bad when the video was white. The text then turns white and is unreadable.
It's like whatever Flash video was last played on the screen, it takes the place of anything purely black on the screen (even after the plugin and browser are closed).

Latest Flash installer from the Canonical repositories as well as the latest proprietary nVidia driver.
Video Card: nVidia 9600M GT

Yeah it's very annoying! I cant even watch 360P youtube movies on my HD screen.... stutters so much because I had to disable hardware acceleration (atom 330 + ION here)

---

### Post by el_koraco on 2011-04-29
KDE has been having similar problems with ATI cards, and I'm hearing that people had issues with Nvidia. Check out the bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/764650]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/764650")

Also, the 10.3 flash plugin beta from Adobe labs has been helpful to some people.

---

### Post by WannabeFantasma on 2011-04-29
> **el_koraco said:**
> KDE has been having similar problems with ATI cards, and I'm hearing that people had issues with Nvidia. Check out the bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/764650]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/764650")

Also, the 10.3 flash plugin beta from Adobe labs has been helpful to some people.

btw X doesn't crash here, for me flash only shows on ANY black...

Didn't know about that 10.3 flash gonna try that on my pc downstairs, I don't want to mess this one up it's running perfect :D

---

### Post by trehanabhinav on 2011-04-29
There is no problem with operating system
adobe flash player is not working well with ubuntu now
try using other flash players instead of adobe
that will solve the problem

---

### Post by WannabeFantasma on 2011-04-29
> **trehanabhinav said:**
> There is no problem with operating system
adobe flash player is not working well with ubuntu now
try using other flash players instead of adobe
that will solve the problem

What do you suggest then? I need hardware acceleration :)

Just found out you can watch youtube in XBMC... works flawless most of the time... :D

---

### Post by Pablo_F on 2011-04-29
I think I have solved this problem but I am not sure how. I have tried the following (some restarts, firefox and session, along the way):

Disable shockwave flash in firefox (I am using firefox4) in Tools -> Add-ons -> Plugins.

Add suport to html5 in youtube via [http://www.youtube.com/html5](http://www.youtube.com/html5)

However, I prefer flash (because of jack audio support which afaik html5 does not have yet), so I disabled html5 and enable shockwave flash again and I am not having this problem anymore (fingers crossed).

Cheers, Pablo

---

### Post by WannabeFantasma on 2011-05-03
seems like 11.04 doesn't have this bug anymore... what has changed from 10.04? using the Same flash version and the same firefox (4)....

Gonna see if the bug still exists in 10.04... If yes that would be quite sad :(

---

### Post by strfireblue on 2011-05-06
I was having this issue on 10.10 for the past week.  The problem would occur with any Flash videos.

The way that I ended up fixing it was by upgrading my nvidia driver.  I downloaded the latest driver (as of this time the file is: NVIDIA-Linux-x86_64-270.41.06.run).  After rebooting I have no trouble.

---

### Post by Objekt on 2011-05-20
> **strfireblue said:**
> I was having this issue on 10.10 for the past week.  The problem would occur with any Flash videos.

The way that I ended up fixing it was by upgrading my nvidia driver.  I downloaded the latest driver (as of this time the file is: NVIDIA-Linux-x86_64-270.41.06.run).  After rebooting I have no trouble.

That did not fix the problem for me.  I have Flash version 10.3.181.14, the same Nvidia drivers as you except for being 32-bit (since I run Ubuntu 10.04 32-bit), and Flash videos still show through any solid black parts of the screen "in front of" the Flash video.  

This happens whether I'm viewing Flash in Firefox or Chrome.

The problem does NOT happen when I watch a Flash video (*.flv) in VLC Media Player.

I "fixed" the problem by turning off Hardware Acceleration in the Flash plugin settings.  

Not sure how much hardware accel matters.  It doesn't seem to help any - CPU use is still excessive (>50%) when playing a 720 HD video, regardless of whether "hardware acceleration" is on or off.  So turning it off is no big deal.

Even though it's sorta-fixed for now, I am tired of the broken junk that is Adobe's Linux browser implementation of Flash.  First the Linux version of Flash uses too much CPU, then it crashes a lot, and now this.  Is there an alternate plugin I could use?

---

### Post by Exüberance on 2012-04-17
I have the same problem (on Ubuntu 11.10) except it's pure white pixels instead of pure black pixels and it happens on any flash file, and only if firefox is minimized (if I drag a window with pure white overtop of the firefox window, it will cover up the flash animation, but if I then minimize firefox, it appears overtop of the white window). I'm using the NVIDIA drivers on version-current. Exact same behaviour under post-release updates.

How is it even POSSIBLE to make it do that accidentally? They must be using some completely ridiculous hack to display video that works "good enough". I get the feeling that when Adobe bought out Macromedia, they had no clue how Flash works, and still don't. At least flash video is slowly dying out to HTML 5. *sigh*

---

