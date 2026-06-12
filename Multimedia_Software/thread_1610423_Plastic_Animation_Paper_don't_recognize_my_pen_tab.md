---
title: "Plastic Animation Paper don't recognize my pen tablet"
date: 2010-10-31
forum: Multimedia Software
---

### Post by alexan on 2010-10-31
Ok, I've downladed and installed this [free program](http://www.plasticanimationpaper.dk/download4.asp)

I've done **sudo apt-get install libstdc++5** and **sudo ./papconfigure.run**
Everything gone smooth (except I've to run the program with sudo) and so is working my graphic tablet... as mouse with no pen pressure :(
It tell me
"*PAP is best experienced with drawing tablet, but none could be found*"


My lsusb:
Bus 003 Device 002: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet

my xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="DarkGreen"]**UC-LOGIC Tablet WP5540U                 	id=9	[slave  pointer  (2)**[/COLOR]]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=13	[slave  keyboard (3)]


The software lacks in settings devices (like GIMP or MyPaint).. plus the support for this software ended 2~3 years ago 
How to solve? :confused::confused::confused:

---

### Post by alexan on 2010-11-03
still need help with this. :confused:

---

### Post by Favux on 2010-11-03
Hi alexan,

Is Plastic Animation Paper hard coded to expect to see stylus to work?  Blender was like that.

If so it's possible you could do that by configuring your UC-LOGIC Tablet WP5540U through xorg.conf.  You would have to use stylus as the section Identifier so the system sees stylus.  That might work.

---

### Post by alexan on 2010-11-04
this:
```
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```
is my /usr/share/X11/xorg.conf.d/70-wizardpen.conf 
I've changed the Identifiers (both or just the first) in stylus.. but nothing did happen :(

---

### Post by Favux on 2010-11-04
Hi alexan,

No not /usr/share/X11/xorg.conf.d/70-wizardpen.conf.  It's the xorg.conf in /etc/X11.  Depending on your video driver you may not have one currently.

It would look something like:
```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
EndSection
```
From:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)  and:  [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)

You'd also need a "ServerLayout" section.  You'd change:
```
        Identifier      "WizardPen Tablet"
```
to
```
        Identifier      "stylus"
```
The "ServerLayout", if you don't currently have a xorg.conf would look something like:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"
EndSection
```
Remember messing with a .conf file or xorg.conf can break X.  You should always back up your current working file and be prepared to restore it from the command line if needed.

I'm not advocating going to xorg.conf because you would lose the ability to hot plug your tablet.  But it's the only way I know to get stylus to show up in 'xinput --list' and hopefully get a program hard coded to expect stylus to work.

---

