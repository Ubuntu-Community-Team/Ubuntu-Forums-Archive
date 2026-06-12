---
title: "Flash becomes purple/green on upgrade to Raring"
date: 2013-04-04
forum: Multimedia Software
---

### Post by rob0214 on 2013-04-04
Flash was working fine on quantal.  When I upgraded to raring, flash videos are about half the size they should be and sort of a purplish green color.

I've tried the various hacks (editing mms.cfg, deselecting hardware acceleration in flash), but nothing seems to work. This happens in both chrome and firefox (which is weird since chrome has it's own built in flash IIRC).  

It's an old Dell Dimension 2400, so it's an integrated Intel graphics chip.

Looking back at my logs, my last update of flash was 3/14, and it went to 

flashplugin-downloader:i386 11.2.202.275ubuntu0.12.10.1
and flashplugin-installer was the same version

currently, it's at 11.2.202.275 on raring also.

---

### Post by rob0214 on 2013-04-14
Well, I've tried every possible combination of [FONT=verdana][COLOR=black]EnableLinuxHWVideoDecode and OverrideGPUValidation in /etc/adobe/mms.cfg, and even every combination with enabling and disabling hardware decode in flash, and still no go.  Not even with the latest flash and xorg updates.

Anyone have any other suggestions? (besides go back to 10)?[/COLOR][/FONT]

---

### Post by user_of_gnomes on 2013-05-09
I have the same problem with a Dell Dimension 3100, have you found a solution yet?
Also uses an Intel chipset. I did not upgrade, I installed 13.04 directly (today) which worked out of the box. 12.10 did not work for me at all, giving me a black screen after booting.

I haven't tried anything to resolve the problem, I wouldn't know where to start. Maybe we should file a bug report?

---

### Post by jasper39 on 2013-05-10
I have the same problem: half-sized video/flash all green/purple. Dell Dimension B110, Intel 82865G graphics. Lubuntu 13.04. I did find the following workaround. When booting, I choose the Advanced Ubuntu options and pick either Linux 3.5.0-27-generic or Linux 3.2.0-40-generic. With either, the video/flash is fine. The default kernel is Linux 3.8.0-19-generic, and that is the version where it does not work.

---

### Post by user_of_gnomes on 2013-05-11
I created a bugreport: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1178982](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1178982)

I have never done so before but hopefully that won't prevent it from being taken seriously.

---

### Post by rob0214 on 2013-05-16
Hadn't thought about the fact that the kernel was upgraded.  I'm also getting weird color transitions (i.e. what used to be a smooth transition from say, white to grey, is more like steps in colors than a gradual transition).

You might want to change the bug to say it's kernel, not gvfs.

---

### Post by user_of_gnomes on 2013-05-16
What do I fill in there? When I type "Kernel" it says "too many results"

---

### Post by rob0214 on 2013-05-16
No clue, never submitted a bug before.

Found a workaround, though.

From [http://ubuntuforums.org/showthread.php?t=2115355](http://ubuntuforums.org/showthread.php?t=2115355) post #9

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format, should be a tab before each line except the first and the last).

Section "Device"
    Identifier    "Intel Graphics"
    Driver        "intel"
    Option        "AccelMethod"    "uxa"
EndSection


Restart X (reboot, restart your display manager, whatever).  Colors are back to the way they used to be and flash works.

---

### Post by user_of_gnomes on 2013-05-16
Does this permanently resolve the problem? Unfortunately, the computer in question is no longer in my possession so I can not test any of this but I'll update the bug report with new information regardless.

---

### Post by rob0214 on 2013-05-18
So far it's working between reboots.  It is a workaround though, since the acceleration method has been changed to SNA in the intel drivers, and I assume that's what's going to be used going forward.

---

### Post by user_of_gnomes on 2013-05-18
Thanks for the update.

Managed to change the affected package to "Linux". I figured that's as close to "Kernel" as it'll get.
Somewhere on that website there's a duplicate of this report but I can't find it. I'll keep an eye out for it so I can merge 'm or whatever it is called.

---

### Post by user_of_gnomes on 2013-05-18
Rob0214,

Could you run the command 
**apport-collect 1178982** and post the outcome here?

Perhaps with the old method of acceleration enabled. 

I got the following message when I updated the bugreport but I can not comply with the request, unfortunately.

> This bug is missing log files that will aid in diagnosing the problem.
>From a terminal window please run:

apport-collect 1178982

and then change the status of the bug to 'Confirmed'.

If, due to the nature of the issue you have encountered, you are unable
to run this command, please add a comment stating that fact and change
the bug status to 'Confirmed'.

This change has been made by an automated script, maintained by the
Ubuntu Kernel Team.

** Changed in: linux (Ubuntu)
       Status: New => Incomplete

** Tags added: quantal

---

### Post by ron16 on 2014-04-16
Have exactly this problem. But I am running12.04.4.   Added as directed  Xorg.conf and now get message on boot "could not write bytes: broken  pipe" .  On a black screen, locked can't do anything, turn off manually.   Don't know what to do.  I can boot to command line.  Did delete  Xorg.conf (I think) but noticed there are several similar files in that  directory.  also posted on [http://ubuntuforums.org/showthread.php?t=2115355](http://ubuntuforums.org/showthread.php?t=2115355) post #9.  Any help would be appreciated.

---

### Post by mörgæs on 2014-04-16
Please post only once. I have jailed the repeat posts. 

The drivers for Intel graphics are much improved in 14.04. I suggest a clean install of this one when people have the purple/green Flash problem.

---

### Post by William_Spickler on 2014-04-16
I have the same problem.  Flash doesn't work correctly in Firefox or Chromium but it does work okay with Google Chrome.  I believe Google Chrome downloads it's own version of Flash so I assume the problem is with Adobe Flash not with the system.  My work around is to use Google Chrome, at least until Adobe gets Flash working.  Unfortunately that may never happen since they are not supporting Flash on unix anymore.

---

### Post by William_Spickler on 2014-04-25
I found a simple solution to this problem,  I think.  I removed Flash in Software Center.  I opened YouTube and did NOT install Flash when it asks. the videos play without the new install of Flash. I don't know what it is using to play the videos but it works!

---

