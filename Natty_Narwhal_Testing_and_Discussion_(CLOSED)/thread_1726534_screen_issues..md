---
title: "screen issues."
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Duncan Williams on 2011-04-11
my screen started going black for about 20 seconds every 5 minutes or so. Does anybody know what causes this so I can stop it.

---

### Post by Harry33 on 2011-04-11
> **Duncan Williams said:**
> my screen started going black for about 20 seconds every 5 minutes or so. Does anybody know what causes this so I can stop it.

1) what is your graphics card model?
2) what graphics driver are you using?
3) are you using any additional sources (PPA's)?
4) in what desktop session (Classic, Unity, Unity2D) do you experience this?

---

### Post by Duncan Williams on 2011-04-11
> geforce5200 (I think) nvidia 128mb.
> Nouvea (I think) - but it's not working properly.
(I have to use failsafe graphics from recovery mode to get gui up)
> Dont know what ppa's are
> Classic (I think)

The black screens have settled down and only happen occasionally now. (after a day of constant black screens)

I would love to just boot into ubuntu and know that my video card is being detected properly, I am new to linux and don't know how to sort it out. Everything seems to be working fine, the only time I notice it is say watching a youtube video.
(my monitor is ok and set to 1900 by 1080 (24")

---

### Post by Harry33 on 2011-04-11
> **Duncan Williams said:**
> > geforce5200 (I think) nvidia 128mb.
> Nouvea (I think) - but it's not working properly.
(I have to use failsafe graphics from recovery mode to get gui up)
> Dont know what ppa's are
> Classic (I think)

The black screens have settled down and only happen occasionally now. (after a day of constant black screens)

I would love to just boot into ubuntu and know that my video card is being detected properly, I am new to linux and don't know how to sort it out. Everything seems to be working fine, the only time I notice it is say watching a youtube video.
(my monitor is ok and set to 1900 by 1080 (24")

PPA is personal package archive. Developers use them for testing software.
Well it is likely you do not have any one of those.
Your graphics card is a bit old, so I think the latest proprietary driver (nvidia-current, 270.30) does not support it.
But perhaps nvidia-173 would. I would try to install that.

---

### Post by Duncan Williams on 2011-04-11
I got (in additional drivers)
Experimental 3D support for NVIDIA cards.
tested by ubuntu developers.

This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.

You need to restart your desktop session after installation.
.this driver is activated and currently in use.

It states on boot > use recovery > use failsafe graphics.
`No proprietory drivers installed' and it doesn't know my monitor graphics etc.

However as stated it does all work.

I am a bit worried about corrupting the installation.

do I
install the nvidia driver you mentioned from the repositories?
do I
need to uninstall the experimental driver?
what about nouvea?
and will my ubuntu boot into normal mode from start after I have setup the nvidia drivers?

or should I just put up with the minor issues and wait for more additional drivers/updates to appear?

---

### Post by Harry33 on 2011-04-11
> **Duncan Williams said:**
> 
...
However as stated it does all work.
I am a bit worried about corrupting the installation.
do I
install the nvidia driver you mentioned from the repositories?
do I
need to uninstall the experimental driver?
what about nouvea?
and will my ubuntu boot into normal mode from start after I have setup the nvidia drivers?
or should I just put up with the minor issues and wait for more additional drivers/updates to appear?

The experimental drivers override the common nouveau.
If you are content with the current drivers you use, you should not install anything else.

---

### Post by Duncan Williams on 2011-04-11
> Well I can't get into ubuntu gui unless I go in through recovery mode/failsafe graphics. This doesn't worry me for an extra few clicks but am curious as to if it limits anything (I can't get unity as far as I know).

> All my graphics, photos etc seem to be in full resolution at 1900 by 1080. But if I watch videos downloaded from youtube they are a bit choppy and seem to be a lower resolution.

It has been stable for 4 days (since I installed) and nothing else seems out of place.

And the black screens seemed to have disappeared?

---

### Post by Blasphemist on 2011-04-11
You know what they say about the simplest explanation right? Couldn't have been a power saving setting could it?

---

### Post by Duncan Williams on 2011-04-11
I was in that sort of area, first thing I checked was screen saver settings.  Anyway I just checked the power settings and they are all switched off, thank you for the comment though. The black screen started up and then disappeared by itself?
(touch wood it doesn't come back)

---

### Post by Harry33 on 2011-04-12
> **Duncan Williams said:**
> > Well I can't get into ubuntu gui unless I go in through recovery mode/failsafe graphics. This doesn't worry me for an extra few clicks but am curious as to if it limits anything (I can't get unity as far as I know).
> All my graphics, photos etc seem to be in full resolution at 1900 by 1080. But if I watch videos downloaded from youtube they are a bit choppy and seem to be a lower resolution.
It has been stable for 4 days (since I installed) and nothing else seems out of place.
And the black screens seemed to have disappeared?

Notice, that when you boot into recovery mode and select failsafe graphics, you are actually not using any specific graphics driver (like nouveau). You are using the general vesa driver (xserver-xorg-video-vesa).
That is meant to a safe environment, but at the same time only temporary solution. It does not provide a good graphical environment.

So, try first the experimental 3D support (mesa-experimental) and if that does not work well, then install Nvidia proprietary drivers. Use Jockey.

---

### Post by Duncan Williams on 2011-04-12
Little like magic, I installed todays updates and all problems resolved for awhile.
Hi unity...

Dropped back to gnome next boot.

But my graphics are excellent and no black screens.

---

### Post by Duncan Williams on 2011-04-12
No proprietory drivers after last install of natty.
I was advised in additional drivers of:
experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.

The resolution is superb on my 24" monitor > the best it has been, photos are now clearer than any previous installation of either windows or ubuntu.

---

