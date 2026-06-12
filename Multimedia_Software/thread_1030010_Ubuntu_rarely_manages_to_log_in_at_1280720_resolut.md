---
title: "Ubuntu rarely manages to log in at 1280*720 resolution w/ Intel GPU"
date: 2009-01-04
forum: Multimedia Software
---

### Post by saratoga on 2009-01-04
Hi.

I'm trying to use Ubuntu with my Samsung 720p TV.  Unfortunately, 8.10 will rarely manage to login without blanking the screen (though on occasion it randomly does manage it so I know it is possible).

Here is my Xorg.0.log file:

[http://www.duke.edu/~mgg6/Xorg.0.log](http://www.duke.edu/~mgg6/Xorg.0.log)

I've got an intel 915 or similar onboard GPU, P4, and am using DVI to drive the TV via an HDMI adapter.  The login screen works (and at 720p) but quickly crashes upon login most of the time.  At which point I can fall back to the terminal which is heavily distorted but usable (and stuck at 640*480).

Is there anything else I should post?

---

### Post by densou on 2009-01-05
> **saratoga said:**
> Is there anything else I should post?

no that's enough :)

first, trying tu update Intel drivers adding these lines to your /etc/apt/sources.list  [then sudo apt-get update or open Synaptic]

```
deb http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
```

then you probably need to set MANUALLY your default (favourite) resolution, but it requires some attention. :)

Note: HDMI doesn't work well with Intel cards, so don't expect to solve everything ;)


Bump your thread when ready ;)

---

### Post by bsmith1051 on 2009-01-05
the login screen uses what's known as the Virtual Desktop resolution.  By default this is set to the maximum available resolution.  Looking at the log file you posted it looks like your TV is reporting an max available resolution of 1920x540??  Instead of letting the video driver auto-detect this you can manually specify the available resolutions in xorg.conf
```
> gksudo gedit /etc/X11/xorg.conf
```
Here's a very basic "Screen" section you can use as a model,
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
	        Modes	"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
You can also manually specify what Virtual Desktop you want the system to use but this requires a lot of extra commands in the xorg.conf and it's usually simpler to just specify your max resolution.

---

