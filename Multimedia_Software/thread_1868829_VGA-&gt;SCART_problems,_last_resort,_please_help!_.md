---
title: "VGA-&gt;SCART problems, last resort, please help! fglrx, ati radeon"
date: 2011-10-24
forum: Multimedia Software
---

### Post by _Smiler_ on 2011-10-24
Hello everyone, I'm really hoping for help with my problem. I'm trying to hook my laptop up to my old TV in order to play avi backups. I'm using a VGA cable with Radeon HD5400. I'm using 11.10 with the fglrx driver. In case it makes any difference, I've tried to update the driver to the post release fglrx, but I get an error to look at /var/log/jockey.log, the relevant bit of which is [here]("http://pastebin.com/raw.php?i=dKnuFpNP") as it was too big to upload to the thread.

So, I click on displays from the upper right corner menu. Click the "unknown" display as it's labelled, slide to on, set the resolution to  800x600 and do the same with the laptop resolution, intending to set the TV resolution higher when I have everything running. (It won't let me do this when having both screens running, obviously I want to keep my laptop screen running until I get it transferred to the TV). However when I click apply, nothing happens on the TV end.

So, I go to Catalyst control centre with admin powers. No matter what settings I choose there (clone display, multi-display), there is no difference. 

I've even fiddled around the back of the TV, tried a different scart port in case it could be something totally simple. I am just completely ](*,) right now :( I absolutely can't stand clutter and am broke so it would be really great if someone tells me I did not spend 20 quid on VGA and RCA-AUX cables just to fail!! Big virtual hugs for anyone that tries to help :mrgreen:

---

### Post by _Smiler_ on 2011-10-27
Bump!

---

### Post by BicyclerBoy on 2011-10-27
I don't think you can use the gnome display tool with catalyst drivers.

The SCART interface can support:
- composite video
- s-video (separate chrome&lum)
- RGB + sync  (NOT component)

The sync (hsync+vsync) can be on composite or sync-on-green.

The problems are:
- this sync signal is not always compatible.
(it should have been separate syncs + combined)
- most SCART equipment only supports composite/S-video.
- VGA has separate h & v sync + RGB.

The passive VGA-SCART adapters don't always work..
I planned to build a sync separator circuit to make use of SCART RGB but it never happened..

Can you define the model of adapter ?
You need to determine the SCART capabilities of each input on the TV..

You need to be using an interlaced video modes for old TVs.
I have used 1024x768 interlaced on a very old CRT (svideo ?).

The last of the CRTs could support progressive modes like 480p60 or 576p50.
And these TVs tended to have component video.

Component video (3 cables) is not directly compatible with RGB+HV (VGA) but there are converters.

You can get video cards that output s-video & component.. 9400GT etc..

---

### Post by mcduck on 2011-10-27
The thing here is that since you are using VGA output from your graphics card instead of a TV output, the card isn't converting your set resolution to something a TV could actually use.

So instead of using 800x600, and even considering setting that *higher*, you should set the resolution *lower*, directly to what your TV can handle.

That would be interlaced 720x576@50Hz or 640x480@60Hz (depending on if your TV uses PAL or NTSC). That's as much as you are going to get through SCART. Using a component cable might give you progressive versions of the same resolutions if you happen to have a TV that handles progressive scan. Most analog TV's don't.

(I suppose the confusing thing here is that if you do use a TV output connector from your video card you are able to set the resolution to somehting like 800x600 or 1024x768. The thing is that the card simply downscales the image from that resolution into TV resolution, which is usually easily visible if you try to display any sharp graphic, small text or similar things. The main purpose of that feature is to allow you to duplicate what you see on the monitor into the TV without having to use such a small resolution on the monitor as well)

---

### Post by mcduck on 2011-10-27
edit: sorry, duplicate post for some reason. :/

---

### Post by _Smiler_ on 2011-10-27
Thanks so much to you both for replying. Sorry to be clueless, but I understood little of that :( 

The cable I got, a Hama VGA-SCART cable, which has these technical details on Amazon [CODE]Product Features
Video connecting cable
To connect devices with Scart OUT (signal RGB-Y) to NEC beamer
Also devices with 15-pin HDD IN
5m length
Black exterior
Technical Details

Connection 2: Scart Plug
Filter: No
Colour: Black
Connection 1: HDD-Plug
15-pin
Length: 5 [CODE]

800x600 is the lowest display settings will give me. So are you saying I can't get anything with VGA? Because I can't afford a new graphics card to get S-video, if that's what you mean by TV-out. From what I understand from both of your replies is that VGA to SCART is directly incompatible. If that's the case, what is the point in this cable being produced?

---

### Post by mcduck on 2011-10-27
You can use the cable, but you'll have to create a configuration for the suitable resolution & refresh rate manually in the /etc/xorg.conf as such resolutions aren't normally used on any computer use.

Sadly, it's been something like 10 years since I've used a VGA-to SCART connection, and  several years since I've had to configure anything in xorg.conf manually (the file doesn't even exist by default any more) so unless somebody else is able to come up with a working configuration, you'll just have to try to google for instructions...

edit: This page from MythTV Wiki might help a bit, at least: [http://www.mythtv.org/wiki/RGB_Scart]("http://www.mythtv.org/wiki/RGB_Scart")

---

### Post by _Smiler_ on 2011-10-27
Lol, that's the last link I was at in my display manager/xorg.conf journey before returning here, but thanks anyway :)

So, I read that xorg.conf is no longer created, so when using ```
gksudo gedit /etc/X11/xorg.conf

``` I get a generic-looking file, just six lines or something. Of course I haven't saved it so I can't show you, but I replaced it anyway with this:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    14.0 - 18.0
        VertRefresh  50
        Option      "DPMS"
        Modeline     "720x576" 15.125 720 778 834 968 576 579 607 625 composite interlace +hsync +vsync
EndSection
Section "Device"
   Driver   "fglrx"
   #BusID "PCI:1:0:0"
   Identifier "Card0"
   Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Extensions"
   Option      "Composite"   "enable"
#   Option      "RENDER"   "disable"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "synaptics"
    Option   "TapButton1" "1"
    Option   "TapButton2" "2"
    Option   "TapButton3" "3"
    Option   "VertTwoFingerScroll" "on"
    Option   "HorizTwoFingerScroll" "on"
EndSection

```
Compiled using these two links: 
[xorg.conf someone used for VGA-SCART]("http://www.minimyth.org/forum/viewtopic.php?f=7&t=2256") and [xorg conf of someone with a Radeon 5400]("http://forums.debian.net/viewtopic.php?f=6&t=66788")

Problem is, when I run xrandr, the resolution for CRT2 hasn't changed. I really wish I had the know-how of you guys to figure this one out myself, and appreciate if this is taking too much of your time, but...dunno, in IRL I would owe you a drink!!

---

