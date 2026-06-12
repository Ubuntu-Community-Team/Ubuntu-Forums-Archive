---
title: "How can I get mode information from xrandr?"
date: 2012-12-30
forum: Multimedia Software
---

### Post by project_isaac on 2012-12-30
Let me start from the beginning:
    I have a dual monitor set up on my Ubuntu 12.04.1 OS. My graphics card(s) is/are AMD Radeon HD5830. Installing the drivers required me to reinstall with command line, but that went smoothly and no problems there. My main monitor is a Dell 1440x900 LCD, and the second is an ACER 1680x1050 LCD. 

    The Dell is hooked up via a mini display port to DVI adapter, and is posing no problems. The ACER is hooked into the DVI port of the card via a VGA-DVI converter, and the cords running into the monitor are VGA. Now, in order to run the VGA cables out of the way to where I want my monitor set up, I required two extensions to the Male-male VGA (15-pin) cable hooked up to my graphics card. The first extension is a 15-pin VGA, and CCC (Catalyst control center) recognizes that the monitor is an ACER, and its native resolution (so does Ubuntu's display settings). 

     Once I add in the second extension (14-pin :-|), then CCC and the display settings recognize the display only as analog, and while most of the resolutions are the same, the 1680x1050 resolution option is not available.  I realize this is likely because the missing pin (pin 9) wouldn't give power to the EDID rom, and thus my computer was unable to glean much information.
  
    I managed to find out how to manually add the resolution via xrandr (getting the mode information from "cvt"), and while it added successfully, choosing the resolution would result in an image that only took up about the leftmost 2/3 of the screen, with the right 1/3 being black (the desktop was "squished" to the left).

    Now, when my ACER is hooked up to the 15-pin VGA and correct resolution is set, but then I unplug it, plug in my 14-pin extension, and plug the extension into my ACER, the resolution is perfect and no 'squishing' occurs. Squishing occurs if I open up CCC and it re-detects my monitor. This makes me think the 1680x1050 resolution setting I made before is kind of "wrong."

    So my question is: How can I get information on the mode currently used in xrandr in order to make an identical mode for when my 14-pin VGA cable is connected?


    Also, I know getting a 15-pin VGA extension would be easier and very inexpensive, but I'd like to know this information regardless, and I would have to wait for the extension to ship :roll:.

   Thanks a bunch, and sorry for the long read, I just felt that completely explaining my situation may inadvertently give some information one may need to help answer this.


EDIT:  by mode information, I mean the modeline of the current resolution, with all the information I would need for making a new mode and would get from cvt or gtf

---

### Post by gordintoronto on 2012-12-30
With all the conversions and extra cables, I'm surprised you get any video at all.

Your graphics card had DVI out, and one of your monitors supports DVI, my suggestion is to put the computer next to that monitor and use a simple DVI cable. Then begin thinking about a second monitor.

---

### Post by project_isaac on 2012-12-31
*Display Port almost always needs to be converted to DVI; there are not too many monitors with display port (or mini display port) in*. *Really, I could consider both of them to be DVI. *
EDIT: ok, a quick google search shows me both feet seem to have been  planted firmly in my mouth. However, the converters from DP or mDP to  DVI are usually pretty reliable (and it is in my case).

Also, it's not really surprising I'm getting video; the only real conversion is a DVI-I to VGA (15-pins at connection to computer), and this has worked fine in every setup I've had, linux or not. The problem lies in the 14-pin VGA extension, and I know I can fix this if I have the right settings.

While I thank you for your time, my question was how to get information out of xrandr. I know I can fix this with a simple cable swap, I just want to try to get this setup working on Ubuntu, as Windows xp, 7, and 8 managed to give a correct 1680x1050 resolution over this.

Also, my cables are shielded as if I expected an EMP, so I have every reason to believe I could run this signal up to 15 or 30 meters if I was more crazy ;)

---

### Post by project_isaac on 2013-01-01
Alright, still no progress on getting that mode information, but an interesting change has occurred. My custom set (via xrandr) resolution of 1680x1050 (at 59.9 Hz) now doesn't squish; instead the ACER appears to have a lower horizontal resolution, with an image that is outside the horizontal "limits" of the display. This is still remedied by having CCC auto-detect the ACER while plugged into the 15-pin and then changing to the 14-pin without re-detection.

---

