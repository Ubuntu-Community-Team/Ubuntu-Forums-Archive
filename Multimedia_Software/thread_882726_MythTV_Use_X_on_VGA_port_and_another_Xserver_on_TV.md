---
title: "MythTV: Use X on VGA port and another Xserver on TV out for Mythtv?"
date: 2008-08-07
forum: Multimedia Software
---

### Post by devnull22 on 2008-08-07
Hi all!

I'm not so much a newbie in the linux world, but I'm new to X configuration on multiple displays and different X servers.

Basically new to MythTV as well, so I'd like your help and experience on these few questions!

Is it possible to run on an nvidia card (GeForce 7100 GS) a X session (in my case kdm with KDE) and on the TV out, a different x session for MythTV? That would let me use Myth TV on the tv output while my girlfriend uses the computer for her work.

If so, how would one go about doing this? I've found articles showing how to run 2 different x sessions, but it was on 2 different videocards. Is it possible to do so on the same nvidia hardware?

Twinview is not so much an option as there are a total of 3 users on the computer who might use it, and I want MythTV to keep running all the time.

If anyone has a similar setup or made it work with a few adjustments, I'd really like your pointers!

Thanks in advance,

Devnull

---

### Post by NT4usB on 2008-08-07
Not only possible but pretty much required to control the output for the TV.
xorg gets a server layout and different configs for each xscreen.
Here's an xorg I used for small LCD and TV while I was configuring MythTV on Dapper. The fields will be similar but all the data will be different for your config.
ED: If you're running a recent release of Ubuntu, (download, install) run ```
sudo nvidia-settings
``` with both monitors connected and you should be able to set up two xscreens from there.

```
Section	"ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
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
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

Section "Monitor"
 #LCD
    Identifier     "Monitor[0]"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci EndSection
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Component" #or SVIDEO Composite etc
    Option         "TVStandard" "HD480i" # "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "720x576_60" "720x480_60" "640x480_60" "480x320_60"
    EndSubSection
EndSection


```

---

### Post by devnull22 on 2008-08-07
Thanks, but unless I'm mistaken, this config makes 2 screen part of one Xserver process.

Meaning that if I log in with my mythtv user, start mythtv, if my girlfriend wants to log on, or start a new X session, or logs off my session to start hers, it would stop displaying MythTV on the tv screen since the VT terminal changes, no?

I would prefer it if say...display :0 is the VGA output, and display :1 is the TV output, started manually by launching X with a config file. 

I just don't know if that can be done with a single nvidia card.

I will try it out and see how it goes though.

---

### Post by mocha on 2008-08-07
Good luck!  Nvidia drivers are so buggy.  I used to struggle with 2 X screens on a 7600GS, DVI to my monitor and S-vidio to my TV to watch videos and MythTV.  Anyway, it was nothing but problems with sync.  I'm one of those people that can detect slight jitters and judder in video, and this setup was full of them.  Lots of posts on [www.nvnews.net](www.nvnews.net) about all the problems with nvidia, Myth, open GL, and Xv sync and so forth.

Good news though, with the 169.12 driver I started using Twinview instead of separate X screens and I have to say that light years of improvements were made.  Metacity puts Myth on the TV and there's no judder!  It's great!

---

### Post by NT4usB on 2008-08-07
Guess I missed the part about logging out and back in as another user.
I'm guessing you'll lose your xsession since myth likes to run as user myth.
Never tried it but what happens if another user logs in without logging out the first user? Isn't that what a multi user enviorment is all about?

---

### Post by devnull22 on 2008-08-08
Okay, basically didn't manage to do what I was aiming for, but it seems due to the design of VT terminals more than the hardware, I think... but might be mistaken.


If I isolate the config so that X starts only on the TV output of the nvidia card, I can start X and see it display on my TV in kdm. Now I rename that file and keep the original one, so kdm is launched on the VGA port. But if I run the command X -config xorg-tv-out.conf :1, I can start a new X server that does display on the TV out, but then I need ctrl+alt+F7 to get back to my original session, and since I'm not in VT8 anymore, it stops displaying in the TV.

I guess I'm trying to do something I can't do ;-) But I'll be trying till I'm sure it can't work!

---

