---
title: "ATI amdcccle crashes on &quot;ok&quot; or &quot;apply&quot;"
date: 2012-02-09
forum: Multimedia Software
---

### Post by jhsnowboard on 2012-02-09
When I am trying to change settings inside amdcccle, it crashes when I submit or apply my changes. I am running it from console with gksu and sudo, but there are no errors reported.
I have tried attaching a watcher to the process but no error is reported there either.

I am unable to get a multi monitor display :[
Anyone have any ideas?

Thanks!

edit, using ubuntu 11.10- curently using xubuntu 11.10.

---

### Post by QIII on 2012-02-09
Do you know what version of amdcccle you are using?

Which version of Ubuntu?

Which desktop environment?  (It gave me a lot of grief trying to use it with Gnome shell in Oneiric)

---

### Post by jhsnowboard on 2012-02-09
11.10 
I cant remember the amdcccle version exactly, 11.9 or something..
It was up to date though.

I tried it on ubuntu and xubuntu, and kubuntu.

edit:
ATI Mobility Radeon HD 5800 Series
Catalyst Version: 11.8
Catalyst Control Center Version 2.13


In Older versions of ubuntu I never had a problem with crashing.

---

### Post by QIII on 2012-02-12
Sorry it took so long to get back.

I pulled a 5870 out of my Folding@Home machine for a bit, grabbed another machine and a couple of monitors and set up a test machine.  The monitors are two different sizes, so keep that in mind.

I got the same behavior you are getting until I manually edited the /etc/X11/xorg.conf file.

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "61"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "0-DFP3"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3600 1920
        Depth     24
    EndSubSection
EndSection


```Your setup is going to be different, but take a look at the "Position" options in the two "Monitor" sections and the values in the Virtual line towards the end.

Since I don't know exactly how you are set up, I can't give much more advice than that.  I hope that helps get you on the right track somewhat.

What worries me a bit here is that I didn't have this problem personally when I installed Oneiric (Kubuntu) on my primary machine!

---

### Post by tweetubunt on 2012-09-02
I see this thread is several months old but I'd like to resurrect it to get some help with similar issues. I'm running Ubuntu 12.04 with an ATI Radeon HD 5450 card, two monitors: a Dell E196FP which I believe should be 1280x1024 and a Vizio HDTV (VO320E) which I think should be 1280x720 (its a 720 resolution). The Vizio is set to 1280x1024 in the Catalyst Control Center and if I change it, or if I try to enable dual monitors, the program crashes and I get this output in terminal:

(process:14738 ) : GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14738 ) : GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14738 ) : GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14738 ) : GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14738 ) : GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

Also, here is my entire xorg.conf file:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

I have to think that has something to do with it. I attached a screen shot of the CCC.

Bottom line: I'd like the multi-display desktop to work and set the Vizio to the proper settings.  If I need to rewrite the xorg.conf file, specific help with that would be appreciated.  Let me know if I've forgotten anything, thanks.

---

