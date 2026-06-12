---
title: "Openshot appimage does nothing ubuntu 24.04. suggestions."
date: 2024-06-19
forum: Multimedia Software
---

### Post by ojc123 on 2024-06-19
I'm an occasional user of Openshot.
i'm a reasonably competent Ubuntu user but not familiar with things too deep in the operating sytem.  
I've done a clean install of Ubuntu 24.04. 
I've installed Libfuse 2 which seemed to get Inkscape, Musescore and Audacity running really well from the appimage.
Openshot just does nothing, as far as I can tell when I click Run as a program.
I've done all the updates for the system and the appimage.

I'd appreciate any help.  Thanks in advance.

Information  about the system
- **Hardware Model:**                        Lenovo ThinkPad T440p
- **Memory:**                                      8.0 GiB
- **Processor:**                                   Intel® Core™ i5-4300M × 4
- **Graphics:**                                    Intel® HD Graphics 4600 (HSW GT2)
- **Disk Capacity:**                            128.0 GB


## Software Information:
- **Firmware Version:**                      GLETA1WW (2.55 )
- **OS Name:**                                   Ubuntu 24.04 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                        46
- **Windowing System:**                    Wayland
- **Kernel Version:**                           Linux 6.8.0-35-generic

---

### Post by 909mjolnir on 2024-06-19
did you open the 'properties' of the AppImage and select 'execute as program' ( or whatever it's called ) ?
that's necessary for AppImages to be set to executable.  ...also maybe:  (sudo chmod [thefilename] a+rx )

---

### Post by ojc123 on 2024-06-20
Thanks for those suggestions.
I did the execute as program thing from properties.  I got the others working by using that.  I've just checked that it's still enabled so as not to be overly confident.
OpenShot-v3.1.1-x86_64.AppImage is currently in my home directory.
I have just tried the chmod as suggested. The result is below.  Tried chmod help and it isn't a help to me.

"sudo chmod OpenShot-v3.1.1-x86_64.AppImage a+rx
[sudo] password for : 
chmod: invalid mode: &#8216;OpenShot-v3.1.1-x86_64.AppImage&#8217;
Try 'chmod --help' for more information"

In the meanwhile, I've added the PPA and installed Openshot from there.  It seems to work ok now.     I'd still like to know what the problem is though..

---

### Post by 909mjolnir on 2024-06-22
I think I remember this happening to me in the past once too.  
I seem to get different launch results in different Linuxes for AppImages. 
I dunno either.

---

### Post by currentshaft on 2024-06-22
> **ojc123 said:**
> 
"sudo chmod OpenShot-v3.1.1-x86_64.AppImage a+rx
[sudo] password for : 
chmod: invalid mode: ‘OpenShot-v3.1.1-x86_64.AppImage’
Try 'chmod --help' for more information"

 chmod [OPTION]... MODE[,MODE]... FILE...

The mode comes before the target file. You also don't need to use sudo to chmod a file owned by your own user.

---

### Post by Holger_Gehrke on 2024-06-23
Whenever a program does nothing when started from the GUI the next step should be starting it from the command line. That's because most programs will send some information to standard output or standard error about the problem that keeps them from running. In the GUI that information isn't shown but in a terminal it is.

Holger

---

### Post by #&amp;thj^% on 2024-06-23
Please use the daily builds found here: [https://www.openshot.org/download/](https://www.openshot.org/download/)

The working version for me is "OpenShot-v3.2.0-release-candidate-12509-3170768e-364897b3-x86_64"

---

### Post by ojc123 on 2024-06-23
Thanks.  I've just returned to say that the daily build worked first time. Just one of those things.  
Thanks for all the suggestions. I've learned things.

---

### Post by ojc123 on 2024-06-23
> **Holger_Gehrke said:**
> Whenever a program does nothing when started from the GUI the next step should be starting it from the command line. That's because most programs will send some information to standard output or standard error about the problem that keeps them from running. In the GUI that information isn't shown but in a terminal it is.

Holger

Thanks for that hint.  I'll remember for next time.  Always something to learn.


Running the Appimage that didn't work from Terminal gives:

Traceback (most recent call last):
  File "/usr/local/lib/python3.8/dist-packages/cx_Freeze/initscripts/__startup__.py", line 40, in run
  File "/usr/local/lib/python3.8/dist-packages/cx_Freeze/initscripts/Console.py", line 37, in run
  File "openshot_qt/launch.py", line 55, in <module>
    from PyQt5.QtWidgets import QApplication
ImportError: /tmp/.mount_OpenShbKcRav/usr/bin/libm.so.6: version `GLIBC_2.35' not found (required by /lib/x86_64-linux-gnu/libharfbuzz.so.0)


Something missing that's presumably not missing from the daily build which did work.   Thanks.

---

### Post by lproven on 2024-09-14
Tightened up security in 24.04 breaks all Appimages. 

The fix is to run this command first:

`sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0`

You will need to do this once every time you reboot, for now. It would be possible to make it automatic but best not undo security changes, IMHO.

---

### Post by ajgreeny on 2024-09-14
I have only one appimage on my Xubuntu 24.04, Musescore-4.4.1.242490810-x86_64.AppImage, but that worked before and still works fine without any need to run that sysctl command.

---

