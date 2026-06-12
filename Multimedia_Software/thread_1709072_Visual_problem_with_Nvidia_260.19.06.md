---
title: "Visual problem with Nvidia 260.19.06"
date: 2011-03-17
forum: Multimedia Software
---

### Post by dargaardms on 2011-03-17
Ever since I let the update manager install the 260.19.06 Nvidia driver I have had page tares about 1/4 of the way down the screen when vsync is enabled, if i disable vsync I get tares all over the screen, with vsync on only 1/4 of the way down the screen.  Same in Video playback, flash, games, window draging, always the same location.  Its not a big issue as I'm not doing multimedia or games under Linux. I'm more wondering if this is just effecting me or if it's a known issue.

---

### Post by BicyclerBoy on 2011-03-18
Do you use VPDAU for video decode/presentation ?

Do you have desktop effects turned on (composite compiz) ?

There are vsync settings for compiz that can be accessed from some config program..this program is not installed by default.

VDPAU uses vsync internally..
XVideo vsync is set by the nvidia-setting GUI app..

I had a fading memory of 260.19.06 being very short lived when it was first released.Sept 2010. It is not listed in the driver archive.

---

### Post by dargaardms on 2011-03-21
I have a feeling this will probably go away with the next driver update.  It seems to be an issue with detecting refresh rates, a program I was using gave me a detected refresh rate of 50hz when the Nvidia control pannel is set to 60hz.  xvidtune shows a refresh of 60.01  When I manually set compiz 60hz rather then auto detect, the visuals are greatly improved but still not perfect.

Flash, compiz, and vlc are the only things that this is an issue as I don't play games.  Flash is probably not tweakable, compiz is already done, I just need to play with vlc.  But knowing my luck if I get it working the update manager will show a new driver that will fix the problem.

On another note, I discovered I can take a screen shot of the page tare. Don't know if that is specific to my problem or you can do this normally but it will be handy for explaining to people what a page tare is.

---

### Post by BicyclerBoy on 2011-03-21
You can get driver updates in a package archive from
Ubuntu nvidia x-swat team ppa or xorg-edgers ppa

---

### Post by dargaardms on 2011-03-22
Upgraded the driver as per your suggestion (now running 270.29).  Everything seems to be working just fine except I still have the screen tearing (note: Fast user switching works now and didn't in the previous driver).  I did some reading on screen tearing and I'm now thinking although this may look like a screen tare it's not.  According to what I have read taking a screen shot of a screen tare is impossible, I however can.  I'm thinking that the video driver (or something else) is actually drawing this artifact and vsync is working fine.

From what I have found screen tares are caused by the display and video card being out of sync.  Taking a screen shot will show you what is in the frame buffer.  So what ever my problem is its happening before it gets to the screen.

For comparison I dual boot to windows 7 for gaming and have not noticed any issues in windows.

---

### Post by dargaardms on 2011-03-22
Here is what I'm seeing.

---

### Post by BicyclerBoy on 2011-03-28
My guess is this is a compiz problem..

It does not look like vsync video tearing

I can use compiz max effects with MythTV (vdpau) using  nvidia 260.19.36..

If you drive a monitor at a non-native resolution mode/refresh rate, you can introduce an effect like this with moving windows..

---

### Post by jimmybute on 2011-03-30
I'm having this same problem, this is really bothering me on my HTPC.
I am running a Nvidia ION with a Samsung big screen 1920 x 1080 @ 60Hz.
The Nvidia X server settings seems to have the correct setting to match the LCD panel, really need to find a fix for this. Since the newer drivers didn't seem to help this, it's being blamed on sync issues?
HorizSync or VertRefresh?

Also I'm not currently running compiz.

@dargaardms so you saw no improvement with the newer drivers, have you found a fix yet?

---

### Post by jimmybute on 2011-03-30
Found this thread [http://ubuntuforums.org/showthread.php?t=1680775&highlight=video+tearing]("http://ubuntuforums.org/showthread.php?t=1680775&highlight=video+tearing")

This seems to do the trick, I'm not seeing the tearing any more.
:D

---

### Post by dargaardms on 2011-04-07
I have just learned to live with it for now.

---

### Post by dargaardms on 2011-04-15
Finally Solved this.  Don't ask me why but I noticed on my wifes profile she didn't have the problem, I compared our nvidia settings.

X Server XVideo Settings has Sync to VBlank Set
OpenGL Settings does NOT have Sync to VBlank Set

on my profile I had both set, unchecking the vblank setting in opengl settings has fixed my problem, everything is working GREAT! now, compiz, video playback, flash, games,  don't ask me why but it's working good now.

---

