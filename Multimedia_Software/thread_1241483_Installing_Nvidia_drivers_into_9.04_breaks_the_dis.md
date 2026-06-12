---
title: "Installing Nvidia drivers into 9.04 breaks the display more than my hammer did."
date: 2009-08-16
forum: Multimedia Software
---

### Post by BigBananaMan on 2009-08-16
It's strange how such a great OS has always been crippled by xorg which I've always had bad experiences with.
After my crappy Biostar mobo finally died I installed an Asus M4N82 to go with my two Nvidia 8800GT video cards (we'll just say I only have one since I'm not going to even touch SLI).  The system is running on two drives in hardware RAID 0.  The version of Ubuntu is 9.04.  

The problem is that whenever I try to install Nvidia drivers, the display breaks and I must reinstall the OS (8 times in one night).  I have tested this on my desktop as well as my Dell C840 laptop so it seems to be like this on 2/3 computers I've tested.

I installed the Nvidia drivers 173 and 180 from both the normal proprietary driver installer and envyng.  I even tried manually installing the 185.18.31 drivers from Nvidia and allowing nvidia-configure to run.  GDM appears to start but does nothing and startx displays the following:
```
primary device is not PCI
(EE) No devices detected.
Fatal server error:
no screens found

bla bla bla

 ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno 3): Server error
```

Installing through the normal proprietary driver installer does update the xorg.conf but it's very sparse:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```
I recall there being a little more to xorg.conf like a "display" section and there was a lot more to the "screen" section.



Whenever I attempt to start the system after installing the driver through any method, after the splash screen it goes back to tty1 and I get the following: (the uuid was too long to type so I just replaced it with the variable [longnumber]
```
Starting up ...
Loading, Please wait...
no block devices found
no block devices found
no block devices found
no block devices found
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/[longnumber]) = dev(252,4)
kinit: trying to resume from /dev/disk/by-uuid/[longnumber]
kinit: No resume image, doing normal boot...
Ubuntu9.04 Monolity tty1
Monolith login:_
```

I cd into /dev/disk/by-uuid and what do I find?  3 numbers, one of which is the [longnumber].  This seems unrelated but since it only occurs when I install the drivers it most likely is associated in some way.

I have attempted xfix
attempted to roll back to original (blank) xorg.conf
attempted to roll back to previously made xorg.conf from nvidia-configure, sudo X -configure, and sudo dpkg-reconfigure -phigh xserver-xorg.  All of the xorg.conf files that were generated were very sparse compared to my previous install(8.04)  I worked on this all through the night and tried many other fixes that I cannot remember until Google ran out of ideas.

Today I tried a couple last things.  I installed the xorg.conf from a known good setup.  This did nothing.

I tried completely removing the Nvidia drivers so I wouldn't have to reinstall the OS.
```
 sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
```
No dice.

```
sudo rmmod nvidia && modprobe nvidia
ERROR: Module nvidia does not exist in /proc/modules
```
hmm, I may check that out later

I checked /var/log/Xorg.0.log and found the line "(EE) No devices detected." and figured this is because I have two cards in the system.  I got this idea from the second link at the bottom of this post.  I looked up the address of the two cards with ```
sudo lshw -businfo | grep -i display
``` got the addresses 0000:04:00.0 and 0000:06:00.0 and manually inserted one at a time into the "device" section of xorg.conf ```
"PCI:0000:04:00.0"
``` and of course since I'm still typing, that was fruitless as well.

I didn't expect it to work right off the bat as Ubuntu is usually buggy and you always need to fix something or other, usually the display but I always managed to do a patch work job to eventually get it to do what I want.

I couldn't find any real information to any of the symptoms and what I did find was solutions that worked for other people but not me.
A few of the pages I've looked at with similar problems are at the bottom if you're curious.  I have not tried installing the third party nouveau drivers but they aren't really usable yet, don't support CUDA(something I'm specifically after), and will probably break the system anyway.  The biggest setback is that I'm out of coffee, don't want to take more caffiene pills after what happened last time(actually I ground a half dozen of them up and mixed it with my coffee grounds, still don't want to touch those things again for a while).  I should probably go sleepy time now.

I won't be throwing any more rocks at it anymore any time soon as I'm tired, so very tired.  If you know what this could be or have seen it before, please let me know.  Perhaps I forgot to do something important and it's staring me right in the face, jumping and shouting "down here stupid!"  If else, I can wait to see if they fixed this in 9.10 this October or try another distro like arch or dare I try gentoo(eventually will try it out anyway) when I have the time half way through the next year.

1.[http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html](http://www.detector-pro.com/2009/04/how-to-install-nvidia-linux-display.html)  His problem was similar but would hang on "checking battery state" and I'm only using one monitor unlike him so changing the way my monitors are configured won't help.

2.[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  The troubleshooting section seemingly had the solution to my problem but as with anything, there can be 101 different things causing the same symptom.

3. [www.iforgottherest.com](www.iforgottherest.com)  Yeah I don't really remember the rest of the places I went.  Just google the problem, pick all the pages that seem to apply, and those are probably the ones I checked.

---

### Post by Mud.Knee.Havoc on 2009-08-16
You don't need to reinstall the OS every time.  Just back up your xorg.conf and restore it later.  If you can't get in, just use a rescue disc (or even another distro like Puppy linux) and copy the old file back.

---

### Post by llamatron on 2009-08-17
I'm having this same issue with any version of NVIDIA drivers that I install. I've tried from inside GNOME, from the command line after it won't boot to GNOME after installing the drivers, from Envy. I'm a complete n00b when it comes to Linux and wanted to try to install this as an alternative to Windows and to try running games in WINE. Could someone post a detailed explanation how to fix this?

---

### Post by BigBananaMan on 2009-08-18
> **Mud.Knee.Havoc said:**
> You don't need to reinstall the OS every time.  Just back up your xorg.conf and restore it later.  If you can't get in, just use a rescue disc (or even another distro like Puppy linux) and copy the old file back.

It would be nice if it were so simple.  I tried using several backup xorg.conf files.  The original blank one, the sparse one, and the one from a known good computer with the drivers installed.  It's as if the xorg.conf is depreciated or just plain broken because it seems to be completely irrelevant no matter what I put in it.  I'm assuming that's not the case and something else  gets changed aside from the xorg.conf that I don't know about.  
I could probably find every change that gets made when I install the drivers by scouring through the numerous log files but I don't want to waste so many manhours shaking trees to see if something will fall out if at best it will leave me with the same system that has no CUDA, 3D games, and cool compiz stuff.

Maybe later I'll set up a partition or extra drive to test on if anybody can come up with ideas.  

llamatron, have you tried most of the things I have and got the same results to confirm it is in fact the same issue?  What hardware do you have?
Also, don't let this discourage you from Linux.  I've only been using it for 1.5 years.  Ubuntu and most other distros usually work out of the box unless you have fun taking it apart until it breaks like me :-k. With all the problems I've had, I still think FOSS is a world ahead of that dinosaur Microsoft.

---

### Post by llamatron on 2009-08-18
My hardware consists of an Intel Quad Core Q6700, 4 gig ram, 2x NVIDIA 8600GT cards in SLi, Asus Striker Extreme motherboard.

Last night I played around in the wee hours. I decided to nix Ubuntu 9.04 and go back to 8.04 as that's what my laptop is running. No problems. Install the update packages, install the hardware drivers, reboot, fantastic! So, I'm excited and think maybe if I upgrade to 8.10 then 9.04, things will be fine. I start the upgrade process to 8.10 and go to bed. Wake up, reboot, same problem as before. Very sad :(

I've tried installing the drivers through the hardware driver manager, from downloaded packages (even tried 185 drivers), tried using Envy from both the command line and from GNOME and tried command line installing from the NVIDIA repositories. Same results. Won't let me edit the xorg.conf file once I reboot, but maybe I'm not doing it right, I am very new.

I'm not giving up, but my knowledge of what to do is 0.

Thanks for the help guys.

---

### Post by dagrump on 2009-08-18
Okay, I think this will fix you up. With both cards installed & bridged (does your mobo require a card flipped or jumper switched?) I'm assuming & you know how dangerous that is, that if you reboot you get a terminal type login. then try the following.
After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
This is what my xorg.conf looks like, yours will be different due to detected hardware.

---

### Post by llamatron on 2009-08-18
I'll try that on the morrow once I'm a bit more awake. I decided to try Linux Mint which I realize is essentially the same and had the same issue after installing the 180 drivers.

---

### Post by llamatron on 2009-08-18
Holy crap on a cracker that worked!

---

### Post by dagrump on 2009-08-19
What did you think I'd lie to you? :)

---

### Post by BigBananaMan on 2009-08-19
I think I see what happened.  If you look in my original post around the last two code boxes you can see that I did essentially what dagrump said except I made sure to do it all wrong.  Instead of typing ```
"PCI:x:x:x"
```  I should have typed ```
BusID "XX:YY:ZZ"
```  Technically on the help.ubuntu.com page I referenced, it said to use ```
BusID    "PCI:x:x:x"
``` but if BusID "XX:YY:ZZ" worked for llamatron, I'll try that out as soon as I can pop an extra drive into the case.  I have a pile of drives but many are broken or need data recovery/bubble gum removal/ duct tape replacement, so I'll probably finish tomorrow.

---

### Post by BigBananaMan on 2009-08-19
dagrump, I did just what you said on an extra drive and it worked.  Tried it again on my system and it ended with a resounding success.  You sir are an asset to the community.  Thank you.

I checked around some other pages and found references to this which confirmed what was said on help.ubuntu.com that the correct format for my card's address at 04:0.00 was ```
BusID "pci:4:0:0"
``` but BusID "XX:YY:ZZ" works just the same since they made xorg.conf somewhat flexible knowing humans will be editing it.

---

### Post by anitagraser on 2009-09-02
Thanks so much for the great step-by-step solution. Worked like a charm. :KS

---

