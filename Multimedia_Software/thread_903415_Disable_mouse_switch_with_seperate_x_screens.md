---
title: "Disable mouse switch with seperate x screens"
date: 2008-08-28
forum: Multimedia Software
---

### Post by WOFD on 2008-08-28
Hi

I have a separate x screen setup (automatically setup with the "nvdia-settings" utility) on Ubuntu Hardy. The secondary screen is my TV (DVI-HDMI) which is only used to display video/presentations directed from my primary computer screen. And of such i never have had any use for the ability to move the mouse pointer from one screen to the next.

That feature however is annoying when playing games particular RTS, since it involves a lot of map scrolling, which is frustrating when the mouse keeps going off-screen.

Question:
Is it possible to disable the mouse switching or setup the screens in another way that would better serve my particular needs?

I have thought of trying to clone the output but on they other hand it's nice to be able to work on the primary monitor when a presentation or movie is playing on the secondary screen. So if possible i would like to avoid this solution.

Thanks in advance
Lasse

---

### Post by lumberjackshaw on 2009-06-11
Not to dig up an old issue but I noticed this post was unanswered and it just so happens that I am trying to accomplish this in 9.04.

I actually have a tv setup as a second monitor and I use mythtv/mythbuntu on the second screen.  I don't use it for any thing else.  It would be great if I could prevent the mouse from switching screens on it own but rather press a special key combo to allow it to switch. 

I have seen some old school screen switchers for cli but for X. Help would be much appreciated.

---

### Post by jelle-e on 2009-12-05
Hi,
I have exact the same question. I want to run XBMC on my second screen (TV) and only use the remote controller with it.
On the first screen I run the normal desktop on which I do want to use the keyboard and mouse. Is it possible to enable the keyboard and mouse on only one of the two desktops?

---

### Post by Blaze1024 on 2010-02-11
Wow once again so much for that fantastic Ubuntu community support. Here once again we have what should be a simple issue and its going on two years with no resolution or response.

---

### Post by Murgle on 2010-07-27
Sorry for digging up such an old topic, but I found it googling for a mouse switching program.

To get the two seperate screens set up so the mouse is 'stuck' in one of the is pretty simple.  Just put the following in your x.org conf file.  What this does is tells X to create two separate screens in the session with the second one being 2000 pixels away from the first.  My understanding is that so long as your resolution is less than 2000 the mouse cursor can't jump the gap and is stuck.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 0 2000
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

```

Then you need to create a second "Device" and "Screen" sections.  Just make a copy of your existing versions of those sections and make sure they have different Identifiers and that the devices are attached to Screen 0 and 1 and the screen sections are attached to different devices.  Mine is below.

```
Section "Device"
    Identifier     "Videocard0 out 0"
    Driver         "nvidia"
    Option	   "RenderAccel" "true"
    Option	   "UseDisplayDevice" "DFP-0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    Screen	   0
EndSection

Section "Device"
    Identifier     "Videocard0 out 1"
    Driver         "nvidia"
    Option	   "RenderAccel" "true"
    Option	   "UseDisplayDevice" "DFP-1"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    Screen	   1
EndSection


Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0 out 0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option	   "NoLogo" "true"
    SubSection     "Display"
        Depth       24
	Viewport   0 0
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen1"
    Device         "Videocard0 out 1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option	   "NoLogo" "true"
    SubSection     "Display"
        Depth       24
	Viewport   0 0
    EndSubSection
EndSection

```

As to the mouse switching program the Gentoo Dual Monitors wiki has one that didn't work for me: [here]("http://http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Moving_focus_between_screens").  It also had a link to a project that had a few different ones listed, but all the links were dead.  I'll see if I can round one up somewhere.

EDIT:
It looks like the dualscreen-mouse-utils script hasn't been unavailable for long, perhaps just a small glitch and it will be back.

---

### Post by aldebrn on 2010-10-05
This thread broke my heart. 

On Fedora 11, I got everything to work thanks to this link:

[http://ds.mcbf.net/wiki/DualscreenMouseUtils](http://ds.mcbf.net/wiki/DualscreenMouseUtils)

Murgle's idea is echoed in the link above. With a 1920-wide "left" display, I set the absolute position of the "right" display at +3920. Then I installed the above tool (it was included in yum, so hopefully is in synaptic).

Just run the command "mouse-switchscreen" to switch to the other display. Tie this to a keyboard combination and off you go.

---

