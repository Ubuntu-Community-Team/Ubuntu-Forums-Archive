---
title: "Finally I installed the nVidia driver in Ubuntu"
date: 2009-01-30
forum: Multimedia Software
---

### Post by DeMus on 2009-01-30
Hi,

As many of you I also had big problems installing the nVidia driver in Ubuntu, I use 8.0.4.2 but this might (!!) also work with other versions of Ubuntu.
I tried it all:
several threads in this forum saying use CTRL-ALT-F1, shut down the X server, install the driver and start the xserver
I used Envyng (also from outside the graphical desktop) to get it done, but nothing worked. The best I could get was a 800*600 display mode, sometimes 640*480 and most of the time a screen which was divided into two parts.
On the top was a green area, below it a black area and then the desktop would start. Horizontally this desktop was divided into two areas again, making the left side of the desktop appear in the middle of the monitor. Moving the mouse to the right side and of the screen, it would appear back on screen on the left side, where the right side of the desktop was placed. It was totally out of sync.

I went to the nVidia site and found this:

Goto: [http://www.nvidia.com/Download/index.aspx?lang=en-us ]()
Choose the right type, series and product and click on search
It will come back with the latest stable version 180.22 (Jan.30)
[color=blue]Step 1:[/color] Read the license
[color=blue]Step 2:[/color] Download the file (and remember where you put it)
[color=blue]Step 3:[/color] Now it gets interesting. Before trying to install the driver read and check the following info which I found in a forum-thread on the nvidia site:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490]()


**[color=red]Debian GNU/Linux or [K]Ubuntu with Xorg 7.x[/color]**

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or **Ubuntu** system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
color=blue]I used Synaptic to uninstall all I could find with the name nvidia and glx in it with the option: Mark for complete removal.[/color]

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the **/etc/default/linux-restricted-modules** or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

[color=red]What they say is: add the above line into the file /etc/default/linux-restricted-modules[/color]

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.
If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

[color=blue]Step 4:[/color] CTRL-ALT-F1
Log in with your username and password.
sudo /etc/init.d/gdm stop
password
cd /folder where nvidia driver is stored/
sh NV [TAB]  #(name will be completed when TAB is pressed)
Accept the license.
I got a message (as always) that I do not have a precompiled kernel module available and if it is okay to get it from the nvidia website. Answer yes. But, there is no module available there so it will build a new one in your computer.
Install the 32-bit libraries also and let the program change your xorg.conf file
The driver is now installed.
Start your Xserver by:
sudo /etc/init.d/gdm start

Congratulations. You now have the latest stable version of the nVidia driver installed. It worked for me, while nothing else worked so it could also work for you.

---

### Post by Beatngu on 2009-02-01
Thank you for the fast reply!!
That was the tut i was trying out yesterday,but it did still not work.
everything was working until the last part installing the drivers then i get "can't open drivers"I think i have read about umbutu  server and umbutu desktop was using diffrent kernels.Maybe this is my problem that i first installed umbutu server and after i installed desktop?The main problem is really when i try to install the drivers i downloaded i allways get can't open file.I open it like this sudo sh and then the file name am i doing something wrong?

---

### Post by Shaya on 2009-02-03
Thanks a lot, it worked for me. ;)
Everything is fine as far as I can see. But I have a question, should we NOT trust ubuntu update manager anymore? And another thing; what would happen to me without "linux-restricted-modules-2.6.24-23"? Should I install it again?

---

### Post by silentknyght on 2009-02-03
Regular updates yesterday broke my install; this fixed it.

Good find in the readme, but like Shaya, that also makes me wonder what's going on with the update manager.

---

### Post by carml on 2009-02-03
> **Shaya said:**
> Thanks a lot, it worked for me. ;)
Everything is fine as far as I can see. But I have a question, should we NOT trust ubuntu update manager anymore? And another thing; what would happen to me without "linux-restricted-modules-2.6.24-23"? Should I install it again?
The linux restricted modules are components not open source,and in  this case I think uninstalling them you uninstall a previous version of the Nvidia drivers. :)

---

### Post by Shaya on 2009-02-03
> **carml said:**
> The linux restricted modules are components not open source,and in  this case I think uninstalling them you uninstall a previous version of the Nvidia drivers. :)

So I guess it won't cause problem. Thanks Carml. ;)
I've just find out I don't have anything in my "Hardware Drivers" ! And I have a problem; when I hover through items in "System" menu (or any other long menu), items keep getting highlighted and keep being highlighted until I close menu by click in one the items or on the desktop! :D
Is there any relation among this problem and new upgrade, no Hardware Drives, and uninstalling linux restricted modules?

---

### Post by DeMus on 2009-02-03
> **Shaya said:**
> So I guess it won't cause problem. Thanks Carml. ;)
I've just find out I don't have anything in my "Hardware Drivers" ! And I have a problem; when I hover through items in "System" menu (or any other long menu), items keep getting highlighted and keep being highlighted until I close menu by click in one the items or on the desktop! :D
Is there any relation among this problem and new upgrade, no Hardware Drives, and uninstalling linux restricted modules?

Yes, I did have the same problem at first. But it disappeared "by itself", cause I didn't do anything (as far as I know of) to make it go away. I hope it will be the same for you.
I also have no listing in the hardware drivers list, but since it all runs I don't mind. I will not start tinkering again with the risk that the system falls apart (again).
I'm happy with the way it is, although I must say that I think it is strange the way nVidia wants us to update their driver.

What is installing a driver? Isn't it simply write new files to a certain folder, after having thrown away the old ones, adjusting some text files with new info and a reboot? Or is that too simple?

---

### Post by skyman11 on 2009-02-03
Hi DeMus,  Thanks for sharing your experience.  I'm going to try your method and see if it fixes my problem.  Running restricted drivers only, I have an embedded nVidia GF6150 w/mobo.  Desktop looks fine, running 1900x1200, but it runs slow and runs poorly upon changing the System->Apperance->Visual_Effects beyond normal.  If I choose other options, the graphics slows to a crawl, then I struggle to get it back to 'normal'.  In normal mode, if I try Control-Wheel to either increase or decrease font size in a browser window, it can take 5-7 seconds to respond.  Too slow.  These symptoms suggest a problem, like this thread, I've read in other threads a way to install the nVidia drivers from nVidia, so I think you might be on the right track.  I'll advise you and the others here of my results.

---

### Post by Shaya on 2009-02-03
> **DeMus said:**
> Yes, I did have the same problem at first. But it disappeared "by itself", cause I didn't do anything (as far as I know of) to make it go away. I hope it will be the same for you.

Maybe it's a bug in Compiz Fusion, because I tried anything I knew to solve the problem and finally I got the answer with shutting down the Compiz Fusion completely!
I'm gonna test all effects and components separately to find out which of them is causing the problem! :D I hope I can, 'cause I'm really addicted to changing workstations by clicking on the left/right edge of the monitor! :-\"

---

### Post by WaLshy11 on 2009-02-04
Hey,

Thx for this post. Everything worked fine but I still only get 640x480 res max. Any suggestions?

---

### Post by skyman11 on 2009-02-05
All,

   I performed all of the steps above, but after X came up, I was stuck in low resolution mode again.  And again, I was unable to access the System Menu, etc.  So I looked at the xorg-conf file, noticed it was lacking in any entries for resolution, so I was puzzled.  After some more fidgeting, powered down the system and gave up.  Next day, I groaned as I was still faced with the specter or re-visiting this issue.  But the login screen came up in higher resolution and so did my desktop!  I run at 1900x1200 on a 24" Samsung, so I was happy again.  I can't explain why a warm boot differs from a cold boot with respect to a seemingly static xorg.conf file.

Apparently I have more to learn just who is it that seems to control that file.

But, I was wrong above in respect to the Visual Effects.  They remain unfixed and all along, it was my thinking that the restricted drivers were not permitting Visual Effects to run properly.

That assumption seems to be wrong.

I've installed all of compiz packages and other dependencies with  no luck.  So, I've been searching for more entries to go into the xorg.conf file that allegedly make compiz work.

---

### Post by skyman11 on 2009-02-05
Walshy11,

   I'll send you my xorg.conf file, but will have to do that tonight as I'm at work and don't have remote access capability from here.

Even though you're running low resolution, you still have the ability to run a terminal.

When you received it my file, I suggest you do the following:

1. Make a backup of your existing /etc/X11/xorg.conf file.
2. Create a new /etc/X11/xorg.conf file from what I send you.
3. Power down your system and restart, hopefully it will work.

I'm guessing that you have an incompatible xorg.conf file.

---

### Post by skyman11 on 2009-02-06
All,

   Here's my /etc/X11/xorg.conf file from a fresh nVidia driver install. This hopefully gets you out of being stuck in low resolution more.  Please note however that I still don't have visual effects running.

--------------------------
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Dec 13 18:55:42 PST 2007


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
--------------------------

---

### Post by Antioch on 2009-02-06
Weird that you would need to do all of that.

All I did was disable the current nvidia "restricted driver," restart X to make sure it was off, then shutdown x (/etc/init.d/gdm stop) and enter "sudo sh nvidia-install-blabla.run" It compiled a kernel interface, installed the drivers - boom done. Everything works fine.

I think the trick is to make sure you DISABLE the restricted drivers that Ubuntu uses first.

---

### Post by cforput on 2009-02-10
Ahhhhhhhggggggggggg!

NVidia is SO frustrating. I followed the directions and now it looks like it wants to work. I just have one little itty bitty problem. My screen goes BLANK! I'm totally toast.

The NVidia drivers are trying to load. I can tell by the font used when I put in my ID & PW when I boot. My NVidia screen also shows up. But then poof, the screen goes blank. All I can do (that I know of anyway - newbie here) is ctrl-alt-F1 and shutdown.

Anyone have any ideas on how to help? PLEASE?

********************** Update *********************
I pressed a bunch of keys (I think ctrl-alt-F7 evenutally) and switched to xserver. I had an error message (stupid me - I didn't write it down). My NVidia is now working!!!!!!!!!!!! After a second reboot, the error didn't show up and my xserver actually loaded with NVidia drivers working properly. I'm all set to go. 

DeMus, I can't tell you how happy I found your post. I have been messing with NVidia off and on for a couple of months and it is now fixed. Thank you!

---

### Post by DeMus on 2009-02-11
> **cforput said:**
> 
DeMus, I can't tell you how happy I found your post. I have been messing with NVidia off and on for a couple of months and it is now fixed. Thank you!

Well, all I did was write down the way I installed the driver. In fact I was only copying things I found on the web.
As I wrote earlier, I also had some small problems with hovering the mouse over a pull-down menu. After going up and down a few times, all items in the menu list would be selected. Strange things is that after one or two re-starts this disappeared completely. Why? How? I have no idea.

I'm happy more people benefit from the way I installed the driver. I still think it is a bit strange how we had to do it. Compared to a Windows system where you just start the .exe file you download, this is like going through hell.

But it's working and now I keep my fingers away from it. Too scared something goes wrong again.

---

### Post by blufade on 2009-02-13
this  is what i get when i try to install the driver
> 
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.




what should i do next ?

---

### Post by alkamid on 2009-02-18
Try getting headers for your kernel
```
sudo apt-get install linux-headers
```

---

