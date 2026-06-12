---
title: "Toshiba Satellite U925t Touchscreen Ultrabook w/ Ubuntu/Kubuntu- Thoughts and issues"
date: 2013-09-13
forum: Mobile Technology Discussions (CLOSED)
---

### Post by cypher_zero on 2013-09-13
.. I recently purchased a [TOSHIBA Satellite U925t]("http://www.amazon.com/Toshiba-Satellite-U925T-S2120-12-5-Inch-Touchscreen/dp/B00AY1FIGG") after deciding against the Toshiba Yoga line (mostly due to price vs specs).  I got it on Wednesday (11Sept2013) and so far I've been fairly pleased with how well Touchscreen has been supported.  It worked immediately from the ([Kubuntu]("http://www.kubuntu.org/")) 13.04 Live USB without additional drivers.  The Ubnuntu 13.04 Live USB worked as well, but I was having quite a bit of trouble with it being very slow for some reason.  

**Initial Setup:**
.. As this is a Windows 8 laptop, I had to disable Secure Boot and UEFI in the bios before I could install to the hard drive (or even run some of the Live USBs I tested) as well as set USBs to boot before the internal SSD. 
.. Due to wanting to setup Xen Hypervisor, I wound up installing Ubuntu first, then Kubuntu desktop on top of that (sudo apt-get install kubuntu-desktop) as there is apparently a bug causing an issue with installing Xen or LVM on Kubuntu that isn't there in Ubuntu for some reason...  When I first booted into Ubuntu after installing it, it wouldn't even boot all the way into Ubuntu so I had to get into shell (Ctrl+Alt+F2) to install Kubuntu.  After a reboot, I was able to get into the KDE Plasma desktop by selecting the dropdown for it from the login screen.  

**KDE/Kubuntu:** 
.. Kubuntu works fairly well with the touchscreen though there are a few issues I'm currently trying to resolve.  There does not appear to be a way to set the mouse to do a right-click on a long-press as you can under Ubuntu which is my biggest issue.  There is a bit of a workaround using the onscreen keyboard however (see below). 
.. There is also an issue with interacting with plasma widgets, including the Panel.  The first tap on a widget will move the mouse and activate a mouse-click as expected, but if you click on something other than the same plasma widget, the cursor will no longer click on plasma widgets when you tap on them.  The cursor will move and the Task Manager will act as if you're hovering on the widget allowing you to tap on the preview and bring a window to the the forefront or minimize it, but this is an odd quirk.  If anyone has any suggestions on why this is working inconsistently or can offer advice on getting it to work, I'd very much appreciate it.  

**Unity:**
.. Unity was giving me some trouble initially during my first boot until I installed Kubuntu-desktop and started booting into the Xen hypervisor.  I haven't used it extensively as my personal preference is toward KDE and I will likely go about removing unity from my system completely at some point.  I'm not exactly sure why Unity started behaving after installing Kubuntu and Xen Hypervisor, but it appears to be mostly functional.  I was getting the occasional pop-up about an error and stating that apps had crashed (Chrome most recently) even though they weren't running but aside from that all else appeared to be working fine.

**Touchscreen Keyboard:** 
.. There is a touchscreen capable keyboard already installed in (K)Ubuntu called Onboard that you can have launch on login and will minimize to a small square icon that you can move anywhere on your screen and will stay on top of other programs (very nice!).  Onboard also includes mouse click control functions so that you can tap on the icon for right-click or double-click and your next tap on the touchscreen will be interpreted as such.  Far from ideal, but it works consistently.  
.. I had originally installed KDM as my default display manager as I like the simplified look of it, but after discovering that there a reliable way to pull up an onscreen keyboard, I switched back to lightdm and the easily accessible onscreen keyboard via the accessibility options.  However, once the screen locks from KDE, I don't have the ability to pull up an onscreen keyboard.  I have yet to find a fix for this.

**Multitouch:** 
.. Multitouch on the touchscreen was working and I was actually able to resize and twist some plasmids with it.  I cannot confirm that it detects more than 2 fingers, though the specs for my model say the screen can detect up to 5.  

**Gestures:** 
.. Not working out of the box as far as I can tell and I do not have a solution at this time, though some of my searches have yielded some possibilities.  It's not been my priority though so I haven't tried much thus far, but I am hopeful since the screen does support multi-touch.

**Screen Rotation:** 
.. Automatic screen rotation was not working out of the box.  Again, haven't looked too deeply but did notice some possible solutions while looking for fixes for other things.

**Other Thoughts:** 
.. I have a personal preference towards KDE, but I believe that Unity may be a better for Touchscreens.  Kubuntu/KDE works fairly well and I suspect that most of my issues will be solvable though one means or another.  There is also ([Kubuntu Active]("http://cdimage.ubuntu.com/kubuntu-active/releases/precise/")) which appears as though it may be much better and is designed to be touchscreen centric, however I did not test it extensively.  If the Onboard keyboard is not installed by default for some reason, a simple "sudo apt-get install onboard" (or use a package manager) should set you right.
.. Another minor issue I've had is that pressing the power button immediately shuts off the machine no matter what I change the power management options to.  I'm hoping to find a fix for this as I'd much prefer to be given the option to lock the screen or reboot, but for now I'm just not pressing that button.

**_TL;DR:**_ 
.. Kubuntu works OK.  Unity would not run well for me initially, though it seems to be running fine now.  Touchscreen use is passable, not great at the moment, but some tweaking and downloading programs to fill missing gaps should make it reasonably usable.

.. I'll try to update this post as I go along with my solutions to the above problems or anything else I encounter.  If anyone has any suggestions, ideas, or related experience, I would love to hear it.

-cypher

---

