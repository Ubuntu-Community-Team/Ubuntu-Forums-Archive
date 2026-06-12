---
title: "Help! Component Video output with M2NPV-VM motherboard"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by douglaseg1 on 2007-01-03
I'm sure that others have the M2NPV-VM motherboard with component video out.  Has anyone figured out how to get the component video out to work with mythtv?

I'm using the component video output to interface with my HDTV and can get the desktop to appear on the HDTV.  I have normal operation until ->

When I try to play any video (mythtv-watch tv option or totem movie player with DVD) I get a major crash.  I am forced to ssh into my computer and shutdown (or pull the plug).

Can anyone help?  See my xorg.conf file below.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       33.75
    VertRefresh     59.94
    Option         "DPMS"
    Mode "960x540p"
                DotClock 37.26
                HTimings 960 976 1008 1104
                VTimings 540 542 548 563
                Flags "+HSync" "+VSync"
    EndMode
        # My 880x480in540p mode
        Mode "in540p"
                DotClock 37.26
                HTimings 880 944 1048 1104
                VTimings 480 506 520 563
                Flags "+HSync" "+VSync"
        EndMode
        # My 1920x1080i mode
        Mode "1920x1080i"
                DotClock 74.52
                HTimings 1920 1952 2016 2208
                VTimings 1080 1084 1096 1126
                Flags "-HSync" "-VSync" "Interlace"
        EndMode
        # My 1760x960in1080i mode
        Mode "in1080i"
                DotClock 74.52
                HTimings 1760 1888 2096 2208
                VTimings 960 1012 1028 1126
                Flags "-HSync" "-VSync" "Interlace"
        EndMode

EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
#    Option         "MetaModes" "1920x1080"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "960x540p" "1920x1080i"
    EndSubSection
    Option         "Connected Monitor" "TV"
    Option         "TVStandard" "HD1080i"
    Option         "TVOutFormat" "Component"
EndSection

---

### Post by ArtInvent on 2007-04-02
I would like to help you out, but unfortunately I'm a step behind you, I haven't been able to get the component out to work quite right. It's low res, and it looks all blue. Of course my xorg.cong file is not sorted out yet, so that is my first quest. As soon as I get that working I can see whether the video hangs it.

I have the same MoBo, and I have a Sony 1080p rear projector. Beautiful HD image from over the air, and I'd like to eventually run a dual screen setup, but first I need to get each screen working right. Since there evidently aren't that many folks running Ubuntu with this MoBo and using component out to an HDTV, it might be well for us to be able to compare notes pretty closely.

As I say, I intend to do dual monitors and have run a long 50' component cable to the tv. This way I can set up DVR functionality like MythTV using an HD tuner on the Ubuntu box. I don't want to set up a dedicated 'media center' but would rather just have the one computer both for my 'working' computer in the home office as well as for TV centric things in the living room; this seems far preferable to me. I will hopefully be able to edit video and play games using the TV as well as let my wife log in and use the TV as a computer while I'm working in the office. Right now I am able to log in to this new Ubuntu box from my laptop as an XDMCP session and I'm impressed with the system's ability to act as a terminal server for multiple users. 

I also have a bluetooth keyboard and mouse that work fine in Ubuntu, so these can be carried to the TV room. For simultaneous users I will have to sort out multiple keyboard and mouse, but that is a later bridge to cross. For now I would just be happy to get the monitor and the HDTV going at the same time at native full resolution with high image quality.

In prep for dual monitors, I got an inexpensive Nvidia graphics card made by MSI, model number NX6200LE-TD64E. It was about $30 at Newegg. I never could get the onboard DVI jack to work, only the VGA, at least to my monitor. I did get the new card's DVI out to work, and I have a 19" 1280x1024 LCD monitor going nicely on that.

Thanks for putting up your xorg.conf file. How did you figure out these settings? My next order of business will be to try to paste some of your settings into my own file and see if that will improve things.

At this point the problem is multi-fold. I can't get both monitors to work at the same time, even though I have two graphics cards. I have to flip the switch in the BIOS to make one or the other the primary boot monitor, then the opposite graphics system is completely dark. And, as I said, the HDTV looks all blue. Hopefully this is just a problem in the xorg.conf. Anyone's help in this would be appreciated.

---

### Post by ArtInvent on 2007-04-03
I have tried your xorg.conf settings with the component out alone to my Sony HDTV. It seemed to work but with problems. The strange blue color is gone, and the color is good, but the resolution is low, about 1/4 of the full 1920x1080 capability. Also, there is a flicker about every 2 or 3 seconds. However, I did manage to play video through mplayer with no problems, and even had Planet Penguin Racer going nicely which has 3D graphics. It may be that I just need to figure out how to change resolutions

You have a lot of specifics in your conf file 'monitor' section and I'm wondering how you arrived at all this? Did you try simpler settings? 

Also are you running Edgy, and 32 bit or 64 bit or what? I'm on Edgy 32 bit. Seems to be enough issues with the 64 bit version to make it not worth the trouble. 

I have tried various dual monitor setups in xorg with very limited success. It's a lot of changes at once and hard to pin down where it goes wrong. The howto's out there mostly don't address having two video cards, and also assume that both monitors will be used in the same viewing area like extended desktops, which is not what I'm trying to do.

---

### Post by halfhalo on 2007-04-03
There is a line that you put into the xorg config files for the blue component.
for Standard def tv
    Option "TVStandard" "HD480i"
    Option         "metamodes" "TV: 720x480 +0+0"
needs to be put in the Screen section.  Then, through nvidia-settings, you can change the screen resolution.

I beleive the newest drivers are needed, as those oare the only ones that work for me.
(Tri-Moniters
1650-1080 on 7900GT
Tv out+ 1280-1024 on integrated 6150)

---

### Post by djseto on 2007-04-08
I am having the same problem. Here is what is in my screen settings are in my xorg (this file was auto configured when I downloaded and ran the NVidia drivers):

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

How do I make the blue go away and get it to output 720p?????

---

### Post by ArtInvent on 2007-04-11
> **djseto said:**
> I am having the same problem . . .

How do I make the blue go away and get it to output 720p?????


As has been mentioned (thanks) basically the key seems to be in the 'screen' section, using the option "TVStandard" which can have a number of valid arguments corresponding to standard TV broadcast resolutions. I use "1080i"  but "720p" also worked for me so that is what you will want. "480i" is also possible. "1080p" did not work for me even though my hdtv should be capable of that.

Using this option, you can get rid of all the mode definitions in subsections. (They seem to be ignored.)  Xorg is smart enough to generate the valid modes and you will be able to still choose lesser and VESA standard resolutions.

Also note the "ConnectedMonitor" option, which tells X to use the Asus's tv interface rather than the computer monitor ports on the onboard video.

Also note the "TVOutFormat" is set to "Component" as we are using the component jacks rather than the S jack or composite on the panel.

Here are my complete xorg.conf device, monitor, and screen settings that work well. (I am using this as part of a multi-monitor setup so I'll just post this part of the file to keep it simple.)

*********************************
##SONY HDTV SETUP

Section "Device"
	Identifier "VidCard0"
	Driver "nvidia"
	BusID	"PCI:0:05:0"
	Option "MetaModes" "1920x1080; 1280x1024; 1280x720"
EndSection

Section "Monitor"
	Identifier "Monitor0"
        HorizSync    30.0 - 90.0
        VertRefresh  50.0 - 75.0
        Option     "dpms"
EndSection

Section "Screen"
	Identifier "HDTV"
	Device "VidCard0"
	Monitor "Monitor0"
	DefaultDepth 24
    SubSection "Display"
	Viewport 0 0
	Depth 24
     EndSubSection
	Option "ConnectedMonitor" "TV"
	Option "TVOutFormat" "Component"
	Option "TVStandard" "HD1080i"
EndSection

******************************

So the above works pretty well for me. I can choose a high res. of 1920x1080 and can also choose 1280x720 or 1280x1024 and lesser sizes. I really like the 1920 res, however be warned that most hdtv's including mine overscan pretty badly. The outer edges of your desktop are not visible, which means the menu bar is probably not visible. I have not been able to solve this, but a workaround cheat is possible: for the time being I have simply added four extra empty menu bars to the four edges of the screen. I colored them black and adjusted their sizes a pixel at a time so that they just disappear beyond the edges of the screen. I like my desktop arranged with a single functioning menu bar at bottom, so I moved the extra blank menu bar at bottom below my functioning menu bar. This does not solve all problems, but at least I can see my menu bar, and I can maximize a window and it won't spill over the edge of my screen. If I hit F11 in Movie Player, it does still maximize beyond the edges, but this is in video and most video is shot to expect some tv overscan so you are basically seeing what you would be seeing on a regular tv screen anyway.

One other note, I am using 50 foot long component cables. The computer is in the other room and I have a bluetooth keyboard and mouse. I read that component cables, being analog, can be run to lengths of over 200 feet or something without degradation. Unlike DVI or HDMI cables which are digital and have very limited length ability. So sticking with component in this case is a good deal.

Now that the displays are working well I'm getting a tv tuner card to see if I can get MythTV going. I will probably buy the pcHDTV HD-5500 card since it is a purpose built linux device and has both analog and digital tuners. 

Hope this helps. I have a 55 inch HDTV and having the full Ubuntu desktop in full resolution on this huge screen is truly fantastic. AppleTV - Schmapple tv.

---

### Post by Verbatim9 on 2007-05-11
As mentioned before, the key is the Screen section in your xorg.conf...in my experience it requires the following three lines for my M2NPV-VM:

for 1080i:
Option "ConnectedMonitor" "TV"
Option "TVStandard" "HD1080i"
Option "MetaModes" "1920x1080"

for 720p:
Option "ConnectedMonitor" "TV"
Option "TVStandard" "HD720p"
Option "MetaModes" "1280x720"

...you might also want to have the option of dropping down to a lower resolution to avoid overscan problems, in which case you might set your "MetaModes" option to something like "1280x720; 800x600" for 720p...I'm not sure what options work for 1080i (though certainly "1920x1080; 1024x768" would work) ...you could also try some of those found [here](http://en.wikipedia.org/wiki/List_of_common_resolutions) and see if you can get a somewhat larger resolution without overscan.

---

