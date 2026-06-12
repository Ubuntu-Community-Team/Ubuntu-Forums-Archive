---
title: "Nvidia driver errors"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by kiuri on 2007-10-05
I think I posted this on the wrong forum here it goes on the right one.

hello

i was trying to install beryl on my Linux and I needed to install the graphic card drivers, so I used this line to install it, as it is on the "how to install beryl post":
-------------------------------------------------------------------------------------------------------------------------------
drivers nvidia


sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite

Now you need to restart your X by logging out and in or by pressing ctrl+alt+backspace
-------------------------------------------------------------------------------------------------------------------------------

after I pressed the sequence above it gave me an error message:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" (on a blue screen)

I presses ok and it showed up this:
"
Markers: (==) probed, (**) from config file,(==) default setting,(++) from command line,(!!) notice,(II) informational,(WW) warning,(EE) error,(NI) not implemented,(??) unknown. ***<<this is the legend, I want to show exactly how it appeared.>>***

(==) Log file: "/var/log/xorg.0.log",
(==) Using config file:"/etc/x11/xorg.confg"
NVIDIA: could not open the device file/dev/nvidia0(input/output error).
(EE) Nvidia(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) Screen(s) found, but none have a usable configuration.
.
.
Fatal server error:
no screens found."
 <<preesed ok>>
--------------------------------------------------------------------------------------------------------------------------
The X server is now disabled. restart GDM when it is configured correctly.
Then it appears a console login(like when you start your pc in msdos).
------------------------------------------------------------END---------------------------------------------------------

What seems to be the problem? (Wrong drivers I guess, How to put it back to normal and install the correct drivers?)

thanks for the help in advance

---

### Post by dabl on 2007-10-05
Try the Envy script installer:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

:)

---

### Post by greenstar on 2007-10-07
I posted a reply to your question at your first post location, [here]("http://ubuntuforums.org/showpost.php?p=3489572&postcount=2").

Greenstar

---

