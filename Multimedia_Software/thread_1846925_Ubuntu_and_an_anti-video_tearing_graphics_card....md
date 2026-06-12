---
title: "Ubuntu and an anti-video tearing graphics card..."
date: 2011-09-19
forum: Multimedia Software
---

### Post by Roasted on 2011-09-19
So I plan to set up a home theatre computer using Ubuntu. Problem is, I've always experienced video tearing with Ubuntu. Video tearing, of course, is simply unacceptable with a home theatre system. :P

That said, what graphics card would be safe to go with? Is there a better one? My only requirement is that it have HDMI out. Besides that, I could care less.

No top end gaming here... just need enough for a solid picture via HDMI to a 52"(ish) TV.

---

### Post by Roasted on 2011-09-22
uppppppp...


Also, is there a proper name for mini PCI graphics cards? Is it just mini PCI graphics card? Micro? Half? 

I have one of these on the right:

[http://www.productwiki.com/upload/images/dell_optiplex_740.jpg](http://www.productwiki.com/upload/images/dell_optiplex_740.jpg)

So I need a shallow graphics card...

---

### Post by .... on 2011-09-22
I believe you're referring to low-profile (aka half-height) cards. MiniPCI is something different.

> I've always experienced video tearing with Ubuntu.
So what video cards have you used in the past?

---

### Post by Roasted on 2011-10-01
All right. Back to basics. 

SO. I have this computer. It's like my 8th one with Linux that has had this issue.

And... I'd like to get rid of my video tearing.

I have compizconfig settings manager installed. The refresh rate is 60hz and sync to vblank is checked. The same settings are true in the nvidia-settings manager. I have the latest Nvidia driver through the hardware manager.

How can I get rid of video tearing? It's been YEARS that I've tolerated it...

---

### Post by 4Orbs on 2011-10-01
Just a suggestion: Play a video BEFORE activating the proprietary driver and see what happens.

---

### Post by BicyclerBoy on 2011-10-01
I have not had video tearing problems with years of use with multiple PCs different video cards. I would not tolerate it either..

The problems all seem to revolve around compiz, twinview or other composite managers.
But compiz & twinview (& unity maybe) have no place on a HTPC interface.

Ubuntu 10.04/ nVidia VDPAU/ separate X screens/ compiz does **not** tear..

If you use HT app like XBMC or MythTV you never use the gnome desktop.
Get your bling fix from the interface & not the desktop..

Video playback via VDPAU is guaranteed not to tear & is always internally vsync.

If you need half-height PCIe
GT430 easy winner
GT220 very good
GT520 too slow
GT210 too slow
GT530/540 does not yet exist..

---

### Post by Roasted on 2011-10-02
> **BicyclerBoy said:**
> I have not had video tearing problems with years of use with multiple PCs different video cards. I would not tolerate it either..

The problems all seem to revolve around compiz, twinview or other composite managers.
But compiz & twinview (& unity maybe) have no place on a HTPC interface.

Ubuntu 10.04/ nVidia VDPAU/ separate X screens/ compiz does **not** tear..

If you use HT app like XBMC or MythTV you never use the gnome desktop.
Get your bling fix from the interface & not the desktop..

Video playback via VDPAU is guaranteed not to tear & is always internally vsync.

If you need half-height PCIe
GT430 easy winner
GT220 very good
GT520 too slow
GT210 too slow
GT530/540 does not yet exist..

Maybe that's the case. On my desktop at home I'm using twinview, whereas a HTPC only has 1 monitor (it's a desktop, so it's not like it's a laptop splitting a connection).

I wonder how in the world I would set up separate X screens then?

---

### Post by BicyclerBoy on 2011-10-02
Just as easy/same as twinview..same config program..just find the tick box separate X screens.

The trick is to launch the programs on to the required screen display
e.g.
DISPLAY=":0.1" mythfrontend
launches myth onto 2nd display

launcher script eg:
```

#!/bin/sh
# Run MythTV front end on display 1
export DISPLAY=:0.1
mythfrontend

```

---

### Post by Roasted on 2011-10-02
So I've come across several things tonight, and I'm hoping somebody here can clear the air.

Tonight in the IRC chat somebody told me that my refresh rates in the two monitors I'm using must match, because twinview sees the two monitors as one and having different refresh rates (even 59.94 vs 60 like I'm dealing with) may cause issues. This user said they noticed this from their own experience. 

If I disable one monitor in the nvidia settings, I have no video tearing. It doesn't matter what vsync settings I have enabled or disabled. It doesn't matter if I'm in Unity or Gnome Shell. It doesn't matter if it's Ubuntu 6.06 or Ubuntu 11.10. One monitor no tear, two monitors in twinview = tearing.

On top of that, it looks like (based on what I'm hearing) that "separate X screens" were dropped support for 11.10. I tried using it, but it gave me a ton of issues, and when I asked in ubuntu+1 IRC chat that's the answer I got that support was dropped.

Moving along, I'm using an Nvidia 9600GT graphics card. Now on another system which I am using as a HTPC, I do not see any video tearing whatsoever. But it's also a single monitor (the monitor being the TV) using an Nvidia 6150.

Is it true? Could having slightly different refresh rates be causing this issue?

---

### Post by Roasted on 2012-03-04
Hello! Bumping up my old thread with a similar question. It does seem apparent that on my desktop system having multiple monitors with less-than-identical refresh rates will result in tearing. However, I just did a new HTPC build with an Intel G620 processor, Nvidia GT430 graphics card, 4gb RAM etc. To my surprise I have tearing via HDMI on the HDTV. It's not a rolling tearing. It's only about 2 inches away from the top of the screen. It never moves, it's just a static line across. It's hard to notice unless what you're watching has a lot of activity at the top of the screen where this line is. I tried the post-release-updates driver as well as the regular driver listed in the Additional Drivers menu. It works great otherwise, but it made me want to re-visit the tearing discussion here as it was concluded multi monitors is what caused it before... but like I said... no multi monitors here. Just a single TV.

Eh??

---

### Post by papibe on 2012-03-04
These tips found [here]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing") (see post #4) where very helpful to eliminate all tearing in my HTPC.

Hope it helps.
Regards.

HTPC: Pentium D (2 cores), Nvidia Geforce 9500 GT, Lucid, drivers from additional drivers, 2 separate X screens, Dell Monitor, 40" Sony Bravia.

---

### Post by Eromatic on 2012-03-05
(Ubuntu 11.04 running Unity and 295.20 nvidia driver)

**CompizConfig Settings Manager:**

[INDENT]**OpenGL:** 
Sync To VBlank should be enabled, [s]which should tell the display driver to go ahead and do Sync to VBlank for this program.[/s] ...should as it indicates: Only perform screen updates during vertical blanking period. There will be tearing in gl with this disabled, most notable when moving windows around.

**Composite:** 
Detect Refresh Rate should be disabled, so that you can set the below slider refresh rate.
Refresh Rate value should* be set to the refresh rate of your monitor. (*Double this value if desired to make Compiz render faster. It makes moving the windows around most notably smoother.)[/INDENT]

**About the Detect Outputs setting of display settings:**
When this is disabled, you will always have to reconfigure the Outputs configuration whenever you switch to another monitor that is running a different display resolution. Best to leave it enabled, as it has absolutely nothing to do with correcting video display tearing.


**Nvidia Settings:**

[INDENT]**X Server Display Configuration:**
Resolution - Set this value to your monitor's native display resolution.
The _Make this the primary display for the X screen_ should be enabled. (That setting should dictate on which monitor is the default sync., but also applies to other things such as to open new windows to this monitor, and where the unity launcher should be placed (assuming Unity ever gets it correct...).) 

Click Apply when done. Then click OK on the popup window to confirm. If you do not see anything, or your monitor doesn't display anything, just wait some seconds for the nvidia settings program to automatically revert back to the setting that you previously had.

**X Server XVideo Settings:**
(This is generally used only when using the XV video output driver. It shouldn't do anything to affect GL video and Compiz.)
Sync to VBlank should be enabled.
_Sync to this display device_ should be set to the monitor that you do not want the video to tear on.

**OpenGL Settings:**
(Should affect Compiz and GL video output.)
Sync to VBlank should be enabled, so that the driver (it has the final say) knows that anything that is using GL needs to sync to the refresh rate of the monitor. Because there isn't a enable when requested by the program option, enabling this should ensure that anything that needs to get vsynced in GL, will get vsynced. XV video output should be unaffected by these settings.[/INDENT]


Some tips on the current trends of video playback on Ubuntu:

As with anything that needs to use Compiz (and Unity), you must keep the composite plugin enabled in your Xorg config (enabled by default). VDPAU doesn't really like it when the composite plugin is enabled, but it will still play a supported video. As outdated as VDPAU supported hardware currently is, VDPAU can no longer support all forms of H.264 encoded videos. Because of this, it is recommended to use GL for the video rendering (if your CPU is fast enough), and to playback the content using SMPlayer2 with mplayer2. 

(GL video rendering provides a better video quality for things such as subtitles when compared to XV video rendering. Use XV perhaps as a last resort to work around the tearing issue if all else fails.)

And if anyone is experiencing any problems with Adobe Flash player, it is Adobe's fault for any playback problems encountered. Even if the cat had spilled your coffee all over your keyboard, it's always best to fault them. Seek a replacement to Adobe Flash player whenever possible. For YouTube I use the FlashVideoReplacer add-on for FireFox, as it can be configured to open the video to SMPlayer2 or even the original SMPlayer. ...thus no tearing and jerky video playback on that.

---

### Post by Roasted on 2012-03-05
Very useful information here... seems as if the tearing is gone. I have to wonder, though... considering there seems to be no negative results coming from these changes, why wouldn't they be set to default? Granted, they're super easy to change... a matter of a checkbox or two... but I see this as something that could be set out of the box... Unless I'm missing something??

---

