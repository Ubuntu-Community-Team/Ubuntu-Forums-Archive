---
title: "Higher screen resolutions (up to 2048x1536) for CRT displays on Ubuntu"
date: 2012-05-11
forum: Multimedia Software
---

### Post by Curious00 on 2012-05-11
Just a note for people who are using CRT monitors and are frustrated that they can't raise the resolution on Ubuntu as high that they have been able to on operating systems like Windows XP. 

Since LCD monitors have become so popular, most video card manufacturers make their drivers adhere strictly to the EDID information which a monitor sends back to the computer about its maximum resolution. This can handicap you at something like a 1600x1200 resolution on a CRT even though larger screens (like my 21" monitor) actually support up to 2048x1536. Extra screen real estate is especially important on Ubuntu where they've made the interface so big, and have bereaved people of any easy way to adjust the screen DPI in order to shrink the GUI like you can with other flavors of Linux.

If you buy an old monitor vga cord, or a cheap little vga adapter, you can bend pin 12 out of the way, and that EDID information will no longer be sent from the monitor. This opens up a whole range of higher resolutions for you.

The issue is discussed [here](http://nookkin.com/content/allowing-any-screen-resolution-on-vista.php) in respect to Vista and Win7, however it also works with the nvidia-settings on Ubuntu, if you're using an Nvidia graphics card. I have not confirmed the effect with an ATI card.


To find pin 12, consult the diagrams [on this wikipedia article](http://en.wikipedia.org/wiki/VGA_connector). Many vga adapters will have numbers etched inside too, which help you orient. Be aware that the the diagram you're looking at on that article is a female VGA pin layout, therefore, the pin numbering will be a mirror image of what they'll be on the male vga layout. From the wire side, it looks like [this](http://www.bbdsoft.com/images/vga.jpg).

(*BTW, as long as you don't bend the post too often or too quickly, you should be able to restraighten pin 12 later with a good pair of needlenose pliers - should you want to.*)

---

### Post by BicyclerBoy on 2012-05-11
With nVidia driver at least..
You can achieve the same by using option keywords in /etc/X11/xorg.conf file.
You can disable individual aspects of video mode pool validation.
This allows server to ignore parts or all of EDID.
Need to replace the EDID data with fixed values in monitor section(s) of xorg.conf etc..
See the driver readme appendix B. X config options.

---

### Post by Curious00 on 2012-05-11
I've tried numerous times to add more resolution options in xorg.conf, and it never worked for me. I'm glad it works for you.

Do you wish to go into more detail about what you're saying?

---

### Post by BicyclerBoy on 2012-05-11
As you know..CRTs are different to DFPs because there can be many "resolutions" you want to use.

The xorg.conf approach is to do the least to get it to work..

Set this to true in /etc/X11/xorg.conf then logout/login.
Option "ModeDebug" "True"
Then check /var/log/Xorg.0.log to see what is reported for your monitor.

Determine the limitation: vert or horiz freq or what ?

The driver builds a list (pool) of video modes from internal list & EDID & custom modelines.
Almost no one needs a custom modeline except CRT & projector users.

Big hammer approach:
 Option "UseEDID" "FALSE"  # completely ignore reported EDID

More fine grained:
 Option "UseEDIDFreqs" "FALSE"   # ignore reported H & V limits
 Option "UseEDIDDpi" "FALSE"  # ingore reported DPI
 Option "ModeValidation" "NoEdidModes" # ignore reported video modes
 Option "IgnoreEDIDChecksum" "string" #ignore checksum error

 Option "ModeValidation" this has about 20 different tokens & display keywords..
(see appendix B. nvidia driver readme)

The driver builds a list (pool) of video modes from internal list & EDID & custom modelines.

If using Custom modelines entries:
I use a custom 1152i50 & 1080i60 modes to get a widescreen CRT to work right.
X driver uses the max resolution listed as the actual screen native pixel size & then calculates the screen size from constant DPI, this messes up any other custom resolutions. This can be overcome by using a fixed screen size entry DisplaySize 350 200 #mm in the monitor section. (appendix E. nVidia driver readme)
This lets the DPI change with each resolution change;The default is constant DPI.

Custom modelines can be calculated using CVT or the online calc
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
This tool is great for getting a modeline for old CRTs.
The actual modeline values can be tweaked manually to adjust screen margins by adding/subtracting small amounts to some of the terms.

Modelines in xorg.conf
Can use directly in monitor section with ModeLine  or place multiple in a "Modes" section; use an unique identifier & refer to this in screen section/display sub-section with UseMode "MyModes"

---

