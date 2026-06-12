---
title: "NVIdia 7200GS Hard Resolution issue"
date: 2008-05-09
forum: Multimedia Software
---

### Post by cschoeps on 2008-05-09
Hi everyone,

I tried posting this in the Beginners forum, but no one seemed to be able to fix this. 

I just did a clean install of Hardy, but when I install the NVidia restricted drixver through the GUI that pops up, it limits my monitor resolution to 1080x1024. My monitor is capable of much higher resolutions, and they ran just fine when I had Gutsy installed. 

I've tried running nvidia-settings, and get this error message:
[I]
Using X configuration file: "/etc/X11/xorg.conf

WARNING: The CorePointer device was not specified explicitly in the layout;
using the first mouse device.


WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
default configuration.
[/I]
After this, I changed linux-restricted-modules-common so that DISABLED MODULES = :nv nvidia_new". This put me into Low Graphics Mode every time I booted up. I then got Envy to run correctly, but results were the same.

Next, I tried Method 2 from here:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

and that restored me to 1280x1024, but with no higher resolutions once again. Running nvidia-xconfig yields the same warnings I'd gotten before. I don't really know where to go for here, I'm kind of new with this stuff. Any help would be greatly appreciated!

---

### Post by cschoeps on 2008-05-09
Also, I now have broken dependencies? 

sudo aptitude update && aptitude upgrade yields this:


[I]The following packages have unmet dependencies:
nvidia-glx-new: Depends: linux-restricted-modules-common but it is not installable[/I]

---

### Post by lessgov2007 on 2008-05-09
Try...

sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation --mode=1680x1050

Where mode=1680x1050 change this to your desired resolution.

If this fails and I suspect it will...Remove the NVidia-new driver completely.  Install the NVidia-glx driver using EnvyNG manual driver selection.  Do not enable the driver through the "Restricted Drivers Manager" this will only install the NVidia-new again.  Instead just make sure your xorg.conf has nvidia listed for the graphics driver.  

After installation I recommend running the code I suggested.

---

