---
title: "Can't get 1080i out on DVI."
date: 2008-11-22
forum: Mythbuntu
---

### Post by jmail524 on 2008-11-22
Hopefully someone here can help me figure out this problem.  I have seached through the threads but have unable to fix the issue.

I have built a dedicated Mythbuntu frontend.  [Mythbuntu 8.10 64-bit, AMD Athlon64 X2 5000+, 1GB RAM, 4GB Flash HDD, MSI Media Live system (GeForce 6150LE), Sony 34" XBR TV]

I am trying to get the DVI output set to 1920x1080i.  The best I have been able to attain is 1280x720p.  When I set the resolution to 1080i, the TV picture goes blank on the DVI port but it displays fine through the component video ports.  I know the TV supports 1080i through the DVI input because my HD-DVD plays fine through it at 1080i.  I have also tried numerous settings in the xorg.conf file (ie., UseEDID=False, TVStandard=1080i, 1920x1080_60i).

I just don't know what to do next.  Any help is greatly appreciated.

Thanks.
Brian

---

### Post by patnyc on 2008-12-05
I have a MSI media live.  I used to have the same problem when connect via HDMI to my sony 720p (1080i) LCD.  I switched to VGA port instead. 

Recently I've bought 1080p LCD.  Now, I am running 1080p without any issues.

---

### Post by Caps18 on 2008-12-05
Are there any switches/splitters in your setup or any way that it is auto-detecting the resolution to be 1280x720?  I had that happen to me.

---

### Post by SiHa on 2008-12-06
Apparently 8.10 doesn;t use Xorg.conf quite as heavily as previous versions, so this may be not much use.

Have you looged at you xorg logfile?

IN 8.04 it's /etc/X11/Xorg.0.log (note the uppercase 'X').

I found this very useful when trying to figure out why Xorg ignored whatever I told it. If you have 'No valid modes found' it would suggest a problem.

I found a guide here:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
That gave me the answers I needed.

---

### Post by jmail524 on 2009-01-20
Thanks for the replies.  Sorry, I have been away for a while.

**patnyc**:  I was wondering if it was my TV tht wouldn't let it go into 1080i mode.  I have an older Sony 34" XBR CRT TV.  I know the TV displays 1080i from my HiDef DVD player without any problems.  nVidia's settings utility shows a native resolution of 1920x1080.

**Caps18**: No splitters or anything.  Just an HDMI to DVI cable straight to the TV.

**SiHa**: I have looked at the Xorg.0.log file.  It gives me no errors that look related to the display. When X starts up the display just goes blank. (TV shows the 'Video 7' message which seems to appear when the TV is no longer getting a signal,ie. turned off DVD, etc...)  But, I can log in via VNC and see my desktop.

I don't know what the problem truly is.  I should just drag my box to my local electronics store and see if it works on a new LCD TV at full 1080 resolution (and probably walk out with the TV it worked on.)

Thanks.
Brian

---

### Post by Caysho on 2009-01-21
Does the video card you are using support HDCP ?

---

### Post by jmail524 on 2009-01-22
Caysho, thanks for the reply.

I have no clue whether or not the on-board video supports HDCP.  It is a nVidia 6150LE chip.  I think this is one of nVidia stripped down chips, s it probably doesn't support HDCP, but I'm not sure.

I tried something in desperation.  I erased my system and reloaded it with Mythbuntu 8.04 and magically 1080i worked through the HDMI port.  I then proceeded to update the system with the latest updates. and now 1080i stopped working, again.  I'm going to do a little more testing to see if I can figure out which update/module is breaking my video output, but at least I know that the hardware truly does support 1080 output throught the HDMI under Linux.

Thanks.
Brian

---

### Post by xinix on 2009-01-22
Here's my entry with a Geforce 6200.  I don't currently use 1080i but it works if I try it.

```
Section "Screen"
    Identifier     "Screen0"
    Device         "NVIDIA GeForce 6200 TurboCache"
    Monitor        "Television"
    DefaultDepth    24
    Option         "UseDisplayDevice"  "DFP-0"
    Option         "UseEDIDDpi"        "FALSE"
    Option         "NoLogo"            "True"
    Option         "TVOutFormat"       "COMPONENT"
    Option         "metamodes"         "DFP: 1920x1080_60 +0+0"   ##1080p##
    #Option         "metamodes"         "DFP: 1920x1080_60i +0+0"  ##1080i##
    #Option         "metamodes"         "DFP: 1280x720_60  +0+0"   ##720p##
    #Option         "metamodes"         "DFP: 720x480_60  +0+0"    ##480p##
    #Option         "metamodes"         "DFP: 720x480_60i  +0+0"   ##480i##
EndSection

```

It took me a while to get it working but in the end it boiled down to this entry.  It has been a long time since I worked on figuring out so my memory is fuzzy.

What does your xorg.conf look like?

---

### Post by jmail524 on 2009-02-02
Things are getting better.  I modified my xorg.conf ***xinix*** configuration as a model. (Thanks*xinix.)*  I not am getting 1080i, but only if my TV is on when I startup my box.  If my TV is off then my box defaults to (what looks like) 640x480.  The top left quarter of the MythTV main menu filles the whole screen.  I put the line Option "UseEDID" "False" in my xorg under the screen section hoping that if it couldn't detect the TV's EDID data it would just force my 1080i mode.  No luck.

Also I think my combination of TV and video card don't play nice together.  Sometimes the TV loses sync with my MythTV box and goes blank.  If I turn the TV off then back on I get the picture back.  I think the timings from the video card are just within the useable range for the TV, is it possible to relax the video card's timings?

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option          "UseEDID" "False"
#       Option          "TVStandard" "1080i"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "metamodes" "DFP: 1920x1080_60i +0+0"
EndSection

```Thanks.
Brian

---

### Post by Caysho on 2009-02-03
To be clear - you get 1080i if the TV is on first, before you turn on the box ?

If so, that's the HDCP handshake occuring.

I asked about HDCP support because even though a chipset can support it, if the card that is built around it does not, it will be treated as non HDCP compliant HDMI.

There should be no need to change the timings on the video output - this sound more like the box is turning on a screen saver / suspend mode; does it happen after the same amount of time, everytime ?

---

### Post by xinix on 2009-02-03
What do you mean by "relax the video card's timing"?
In the monitor section you can set the horizontal and vertical sync rate range for your tv.  I used edid-read to get info from my tv's edid and use it's suggested horiz and vert ranges (they are better than what the tv's manual listed).
Although the driver can autoselect the TVOutFormat, it might not be guessing it right for your setup.
```
option "TVOutFormat" "Component"
```
This option tells the driver to put out an hd signal and isn't just for component connections (dvi and hdmi fall into this options domain).

Share with us your whole configuration file.

---

### Post by jmail524 on 2009-02-03
**Caysho**:  Yes, if I turn on the TV before the Myth box, it seems to detect that the TV is capable of 1080i and thus I can run at that resolution.  If the TV is off wen I turn on the box, the resolution seems to be stuck at 640x480. This is not a huge problem.  I just thought that because of the boot time of my box, I used to leave the TV off and hit the power on the box and come back late when it was done booting then turn the TV on.

I do not know if the MSI Media Live/GeForce 6150LE uses/is capable of HDCP.  I am sure that the TV supports it.

The amount of time that goes by is very random.  I have days when it never blanks out and days where as soon as the Myth box reaches the main menu, the screen blanks.  I then have to turn the TV off and back on to get my picture back.  I don't think cycling the power on just the TV would cancel the screen saver. (But I could be wrong.)

It might be a video timing/sync issue, which is why I asked about relaxing the video timings.  I have worked with computer monitors that are capable of 1280x1024 resolution, but not at standard VESA timings.  I used to have to modify the blanking/sync time to bring the timings within the capabilities of the monitor.  I just thought something like that might be happening between my GeForce 6150LE and TV.  The GeForce might be pushing a scanrate/etc that is just beyond the acceptable limits of the TV causing the TV to loose sync and go blank.  Consequently, cycling the power on the TV would cause it to resync. (Just a theory of mine.)

**xinix**:  I hope my explanation above cleared up my meaning of "relaxed" video timings.

I can't seem to find/install the "read-edid" command.  It does not seem to be avalable for a 64-bit  OS. (Not that I can find anyway.)

I looked in nVidia's ReadMe (on their website) for the driver and found a section describing the option "TVOutFormat", but it only gives 2 examples (SVideo and Component).  I'm not sure what to type, does "Component" force output via HDMI also or just component.  (Please keep in mind that my board has composite, s-video, componentand HDMI connectors.) Im already using 'Option "ConnectedMonitor" "DFP-0"'. I thought that this was used to force output via HDMI.

Here is my current xorg configuration. The items commented (#) out were attempts that failed with serious consequences.   
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
#       Option          "UseEDID" "False"
#       Option          "TVStandard" "1080i"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "metamodes" "DFP: 1920x1080_60i +0+0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
        Load            "glx"
EndSection
```Thanks
Brian.

---

### Post by Caysho on 2009-02-04
Given it works properly only when the TV is on first, I'd say the card is HDCP compliant :)

read-edid for amd64 is [being packaged]("https://bugs.launchpad.net/ubuntu/+source/read-edid/+bug/242043").

I typed the rest of this before I thought of suggesting you post the xorg.log - that will state what it's using for the modes/standard.

xinix, according to [nVidia (current readme 09/01/2009)]("http://us.download.nvidia.com/XFree86/Linux-x86/180.22/README/chapter-16.html"): 
```
TVOutFormat     Description                                                   Supported TV standards
"AUTOSELECT"    The driver autodetects the output format (default value).     PAL, NTSC, HD
"COMPOSITE"     Force Composite output format                                 PAL, NTSC
"SVIDEO"        Force S-Video output format                                   PAL, NTSC
"COMPONENT"     Force Component output format, also called YPbPr              HD
"SCART"         Force Scart output format, also called Peritel                PAL, NTSC

```
In essence, it's the type of physical connection to use when it's not HDMI (Component is YPbPr, which HDMI doesn't carry)

Connecting via HDMI, the bit you are after is TVStandard:
```
TVStandard     Description
"PAL-B"        used in Belgium, Denmark, Finland, Germany, Guinea, Hong Kong, India, Indonesia, Italy, Malaysia, The Netherlands, Norway, Portugal, Singapore, Spain, Sweden, and Switzerland
"PAL-D"        used in China and North Korea
"PAL-G"        used in Denmark, Finland, Germany, Italy, Malaysia, The Netherlands, Norway, Portugal, Spain, Sweden, and Switzerland
"PAL-H"        used in Belgium
"PAL-I"        used in Hong Kong and The United Kingdom
"PAL-K1"       used in Guinea
"PAL-M"        used in Brazil
"PAL-N"        used in France, Paraguay, and Uruguay
"PAL-NC"       used in Argentina
"NTSC-J"       used in Japan
"NTSC-M"       used in Canada, Chile, Colombia, Costa Rica, Ecuador, Haiti, Honduras, Mexico, Panama, Puerto Rico, South Korea, Taiwan, United States of America, and Venezuela
"HD480i"       480 line interlaced
"HD480p"       480 line progressive
"HD720p"       720 line progressive
"HD1080i"      1080 line interlaced
"HD1080p"      1080 line progressive
"HD576i"       576 line interlace
"HD576p"       576 line progressive

```

Try that without the meta modes.  It is possible to push standards like HD1080i over Component, according to the first table.

---

