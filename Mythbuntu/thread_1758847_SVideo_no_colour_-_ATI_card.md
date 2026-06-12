---
title: "SVideo no colour - ATI card"
date: 2011-05-15
forum: Mythbuntu
---

### Post by Chewiesw on 2011-05-15
Hello

When I use the svideo out on my ATI X1950 card I get no colour, no problems using DVI.  I am currently using the generic driver. 

What I find strange is that I have no xorg.conf in /etc/X11 as I have heard that if you play around with the tv out settings you may get it to work.

If I install fglrx I loose all display. What I think I need to find is the legacy ATI driver for X1950.

Andrew

---

### Post by klc5555 on 2011-05-15
Though no xorg.conf is used by default nowadays, if you happen to know the specialized xorg settings you need, you can add your own specialized xorg.conf including just the section that contains those specific settings. 

That was the type of technique I had to use to get XBMC to run in 10.04. Although X was already running at a 24-bit color depth, unless XBMC found an actual physical xorg.conf file in which the default color depth was set to 24, it refused to start. So I provided one that had just the single 'Section "Screen"' block included.

Perhaps a similar approach will solve your tv out settings issue.

---

### Post by Chewiesw on 2011-05-15
How do I edit the tv-out settings if there is no xorg?

What I was going to try to do by editing/checking the xorg.conf was to see what the TV Out settings and possibly are and check if the card was PAL or NTSC.

---

### Post by klc5555 on 2011-05-15
Like I said: fire up a text editor and make one. Put it in the right place directly under /etc/X11/ i.e., /etc/X11/xorg.conf

I'm not sure what precise tv out settings you'll need, since I don't use tv out.

But I suspect that your homemade xorg.conf file will have only one section - Section "Screen", and this will resemble what is described here: [http://snippets.dzone.com/posts/show/2986](http://snippets.dzone.com/posts/show/2986)

When you have edited your trial xorg.conf and put it in the right place, log out of and restart X to see if the settings have the desired effect. If not, fire up the text editor and reedit the file.

---

### Post by Chewiesw on 2011-05-15
This is what I think I need, but I am not sure of all the settings (those in red)

Section "Device"
Identifier [COLOR="Red"]"aticonfig-Device[0]"[/COLOR]
Driver [COLOR="red"]"fglrx"[/COLOR]Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "TVFormat" "PAL-I"
Option "ForceMonitors" "tv,nocrt1"
Option "UseFBDev" "false"
# Option "TVOverscan" "on"
Option "OverlayOnTV" "0"
Option "TexturedVideo" "on"
EndSection

Section "Screen"
Identifier [COLOR="red"]"aticonfig-Screen[0]"[/COLOR]Device [COLOR="red"]"aticonfig-Device[0]"[/COLOR]
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "800x600"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection

---

### Post by klc5555 on 2011-05-15
Well, then, give it a try and see if it runs. It may work, whereupon your job is done.

Or, if your initial attempt at an xorg.conf results in an error that fails to allow X to start, and for whatever reason does not drop you to a terminal, you just need to be able to either ssh in from another machine to a terminal, or boot to the repair terminal from Grub so as to do something like

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

to get your homewritten xorg.conf out of the way to let to let X start normally. Whereupon you can edit the file to try to fix whatever the mistake was, mv it back to "xorg.conf" and try it again.

Good luck.

---

