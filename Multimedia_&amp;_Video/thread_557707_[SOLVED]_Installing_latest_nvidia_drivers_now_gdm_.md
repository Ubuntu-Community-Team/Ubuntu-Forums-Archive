---
title: "[SOLVED] Installing latest nvidia drivers now gdm no longer works. HELP"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by maltman on 2007-09-23
I attempted to load the latest nvidia-glx-new drivers based on the tutorial from a sticky in this forum [HERE]("http://ubuntuforums.org/showthread.php?t=301499")
I chose the simple method 1.
The install seemed to go just fine, but when I rebooted, I'm greeted instead with a screen that says:
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Looking at that log doesn't give too much info. The last couple lines are simply:
Fatal server error:
Caught signal 11. Server aborting

Then after getting past that it also asks:
Would you like to view the detailed X server output as well?

That also doesn't seem to display any error messages to me, other than also repeating the same above Fatal server error message as above.

Then it says:
The X server is now disabled. Restart GDM when it is configured correctly.

Then I'm dumped to a command line.
I've searched around on the forum and nothing has seemed to help. I've tried reinstalling the previous driver. Tried using my backed up xorg.conf. Tried recreating a new xorg.conf. Tried restarting gdm. But everything I've tried so far still produces the same result above. 

Please help.

Thanks.

---

### Post by maltman on 2007-09-23
I did find an additional error if that will help anyone help me...

Error: API mismatch: the NVIDIA kernel module as the version 1.0-9755, but this X module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Please, does anyone know how to fix that?

I was able to get gdm running again, but I had to uninstall all nvidia drivers and reset my xorg.conf.
It would be nice to be able enable the nvidia drivers again.

---

### Post by tafkamk on 2007-09-23
I had a similar problem after a kernel upgrade

The solution for me was to read the nvidia linux driver page and follow their directions. Not only were they easier they worked.

> STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-100.14.19-pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-100.14.19-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

---

### Post by dabl on 2007-09-23
Or, you can do it with Envy: [http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

:popcorn:

---

### Post by maltman on 2007-09-23
Cool, thanks. I ended up using Envy, and that worked like a charm.
The hard part was getting back to the desktop in the first place, and I had to uninstall all nvidia drivers and recreate xorg.conf.
Then downloaded the Envy script, and then manually updated xorg.conf to support my widescreen lcd of 1680x1050. All is good now. Thanks.

---

### Post by dabl on 2007-09-23
Cool!

Please edit your title to add "[SOLVED]" so other folks can find some help here.  Thanks! :)

---

