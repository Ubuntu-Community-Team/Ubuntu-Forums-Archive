---
title: "How do I set Nvidia HDMI audio as default audio output"
date: 2014-10-25
forum: Multimedia Software
---

### Post by jewfromdahood2 on 2014-10-25
So I have my HTPC with Ubuntu 14.04 LTS and my default Intel 3400 GPU was not doing so great for video rendering so I threw in an MSI Nvidia 210 GPU because it had a low profile bracker for my HTPC and the video issues are all solved. Now I have this minor issue that every reboot it seems to not keep the HDMI for the Nvidia card as the default output. So I need to know how can I lock it as the default audio output?

---

### Post by fballem on 2014-10-25
I ran into a similar issue - I have Bose speakers driven through a USB port.
There is an application, gnome-media, that I have installed from the repositories. It provides a GUI based way to set defaults for input and output. It seems to work very well.
I've attached a screenshot.

You may install this using the Software Center or in a Terminal: sudo apt-get install gnome-media.

I hope this helps,

---

### Post by jewfromdahood2 on 2014-10-26
Ok so it's installed how do I launch it on 14.04.1 LTS I can't find it

---

### Post by fballem on 2014-10-29
In the HUD, type multi. It will be identified as Multimedia Systems Selector.

Sorry that I didn't mention it.

---

### Post by fballem on 2014-10-30
Hi,

I remembered that there is a setting in the gnome-media configuration file that you need to change.

**If the Gnome Media tool was installed, by default it will not be displayed. To correct this:**

     1. copy the following command into a Terminal: gksudo gedit /usr/share/applications/gstreamer-properties.desktop
     2.   this will open up the desktop file in an editor.
     3. locate the line for NoDisplay. By default, this is set to true.
     4. change the value to false.
     5. save the file, then close the editor.

That should correct any remaining issues.

Hope this helps,

---

