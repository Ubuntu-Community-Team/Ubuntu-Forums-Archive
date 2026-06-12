---
title: "The NVidia Overscan Issue and Fixing It"
date: 2011-06-23
forum: Multimedia Software
---

### Post by occulus on 2011-06-23
I have Googled. I have searched these forums and others. 

[I]I have ripped my hair out in frustration.

[/I]As many are aware, custom resolutions- "What the hell" by "that's just messed up" or "Jesus Christ" by "you've got to be kidding"- are very hard to set under the new "xorg.conf isn't really used" paradigm. This should not be. *Many* Ubuntu users are running the OS on displays with either nonstandard display resolutions or devices which overscan the display but do not offer a 1:1 pixel display setting- such as myself, on my 50" Samsung 1080p DLP television, connected via its HDMI port.

After *more than a year* trying to find a hard-and-fast **process** for fixing this overscan problem (note that I did not say "a hard-and-fast FIX for this problem"), I have decided to turn to the collective wisdom of the Ubuntu user community in an effort to put this issue to bed for good. To that end, I create this thread.

Recent research via the web has led me to believe that the problem lies in the X server not being aware of any sort of valid modeline for my- or your- nonstandard resolution. I am well-aware that each solution for each user will be different; if you're reading this, you're probably a geek like me in the first place, and your chops are more than sufficient to tackle both biting off this huge issue *and *chewing it.

My question to the community is this: How do I determine the correct modeline to add to xorg.conf, how do I make it available to the X server, what do I need to do to format the modeline in a valid way in xorg.conf (if necessary), and how do I make it appear in the list of valid resolutions when I run nvidia-settings (or whatever the command is)?

Keep in mind, I'm more interested in establishing the correct *pipeline* for fixing the problem and allowing arbitrary resolutions to the limit of the given device's capacity, rather than an exact solution for my particular hardware. In other words, I don't want an exact answer for my situation; what I'm looking for is a method for finding the proper solution given situations similar to mine.

This is a huge issue for a lot of people; I know this from my endless Googling on the subject. If you know *anything* about how to go about this, please, *please* post what you know. Thank you.

---

### Post by BicyclerBoy on 2011-06-23
Can I just start the discussion with a brief look..& all IMO..

I think you need to break this issue into different categories.
1. DFP with DVI/HDMI
2. DFP with analogue
3. CRT with analogue (VGA or component)
4. last gen CRT with upscaler/digital engine

a.  display of GUI
b.  VDPAU video decode/presentation.

Important info:
All DFPs have a pre-scaler that drives the panel at native resolution.
CRT monitor do not have a pre-scaler except for some HD-ready models with upscaler.
Overscan was required in CRTs
Overscan is normally enabled for HDMI inputs that are not in PC mode.

Modelines:
Are only truly useful for analogue connection. (I explain in a bit).
If you can find the real specifications of a monitor, it is easy to calculate a custom modeline. The tricky/iterative part is to optimize the over/underscan & still allow the monitor to sync.
There are a few calculators workbooks & online  that make this easier.

The analogue RGB video signal is a very elegant serial datastream that has managed to remain usable for decades. For an analogue monitor to sync with a video signal only the horizontal & vertical frequency have to be in range.
This behaviour can be exploited to move the left-right & top -bottom margins of the display.
A DFP using an analogue connection can also be manipulated the same way but the results will depend on the pre-scaler.

[Speculation follows because I have not done the experiment]
A digital connected DFP may not allow the same freedom because the accepted video modes are much reduced/constrained. Similarly they may not accept custom modelines.

To maintain very close to 1:1 pixel mapping & preserve PQ, a better way to manage DFP overscan is to scale the display image to be inside the display frame; this is what MythTV does. And this is similar to what the nvidia driver provides **(a.)**

Scaling is always bad for PQ but you have no choice.
Video is encoded at a resolution; fixed video modes.
The nvidia driver is capable of VDPAU high quality scaling (feature set C,D) for video decode/playback **(b.)** , there are many HQ s/w scalers lancroz bicubic etc..
Example:
MythTV allows a different screen size for GUI & playback. You are able to make the GUI smaller than the video mode frame size.

I have not tried using nvidia overscan compensation with VDPAU playback.

If the desktop virtual size could be made smaller (inside) than the video mode frame then there would be an existing Xorg method to get a system wide overscan adjustment.
I have not tried it yet.

CRT TVs generally have a service menu that allows alignment/geometry adjustments.
The service alignment can be adjusted to obtain the best geometry with a custom modeline.
Geometry alignment is not a problem for DFPs.

---

