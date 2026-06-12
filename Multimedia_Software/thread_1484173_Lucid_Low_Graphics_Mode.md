---
title: "Lucid Low Graphics Mode"
date: 2010-05-15
forum: Multimedia Software
---

### Post by gdonwallace on 2010-05-15
This started yesterday.  I have been running Lucid since the Beta release with no problems.  Yesterday, I found about 20 or so updates ready for 10.04.  I looked them over, mostly lib files, so I decided to go ahead and let them update.  That evening I rebooted my machine before I left for the night, and it came up with the error "Ubuntu is running in Low Graphics Mode".  In a word X is totally hosed.  The display is cut just left of center, with part of the windows on the right carrying off the screen to come back onto the screen to the left.  

I thought maybe Xconf might have been messed up, but not sure how.  The updates I applied did not do anything to Xorg; and my understanding was that I didn't need that file because I am running with an Nvidia card.

I tried to "reconfigure" the X settings from the error message, that did not work.  I logged into a text only terminal, and copied a good backup of Xorg.conf back into place and rebooted.  Same thing, still running in Low Graphics mode.  



Any thoughts???

---

### Post by Praetor77 on 2010-05-15
I am having the exact same problem, check out my post, almost at the same time you posted, lol:

[http://ubuntuforums.org/showthread.php?t=1484137](http://ubuntuforums.org/showthread.php?t=1484137)

Maybe you can try some of the stuff I posted, enabling/disabling KMS, updating to mainstream rc7 kernel, updating xserver-xorg-intel to 2.11, but nothing worked... although, something that boosted my "low-graphics-mode" performance in the meanwhile is changing xorg.conf.failsafe driver from VESA to intel, although I just opened that file for editing and noticed the driver has changed to fbdev... :confused:

---

### Post by gdonwallace on 2010-05-15
I looked through Your thread, seems that we had at least on problem in common.  My card was defaulted to VESA as well.  I changed it to Nvidia, but have not had a chance to test that fix.  As it is my work computer.  Will test that on Monday.

I looked though the Xorg.0.log and it is loading everything as NVIDIA, so I am not sure if the change I made above to the xorg.conf.failsafe will fix the problem or not.

Will post on Monday and let You know what happens.

---

### Post by lidex on 2010-05-16
I'm using nvidia-current and every kernel upgrade borks it. I would simply boot into low graphics mode and run jockey (hardware drivers). Enable the correct driver there and reboot. Any issues on reboot run in a terminal:
```
sudo nvidia-xconfig
```
and restart X.

---

### Post by gdonwallace on 2010-05-17
Didn't work, still running in low graphics mode.  

lidex: I ran jockey, and made sure that I am running the latest drivers for Invdia.  There are two entries, version 173 and version current.  Version current is currently installed.  Ran the sudo nvidia-xconfig and rebooted.  Still wanting to come up in low graphics mode.

---

### Post by lidex on 2010-05-17
OK. I had issues too. Trying to remember exactly how I did it.
Remove any / all drivers in jockey. Remove xorg.conf:
```
sudo mv /etc/X11/xorg.conf xorg.conf.old
```
Reboot. You'll come back in low graphics mode and at the desktop open jockey and enable nvidia-current. Reboot. Check status in jockey. If enabled and in use run:
```
sudo nvidia-xconfig
``` and reboot again. Now enable desktop effects.

---

### Post by gdonwallace on 2010-05-17
Lidex: Tried that, it was hell trrying to get the drivers activated through jockey.  My screen is totally jacked.  The jockey display goes off the bottom, which I cannot see.  And where the edge is supposed to be, is about 4 or 5 inches in, so I move my mouse all the way to the right, it will go off one side of the screen and come back on the other side.  

I just decided to re-install.  I don't really have time to mess around with this, as this is happening on my work computer.  I have all my important things backed up, so no issues with that.  My passwords and web-site URLS are stored in Xmarks for Firefox, so I can get that back up and running.  My only problem will be email.  I had a lot of filters made to move emails around, will have to recreate the folders and filters to get that back and running properly.  That will be the only headache.  

Thanks for the help guys.  

I am not marking this one as solved, as it is not.  Maybe we can keep this one going as I have noticed a few other threads about the same thing.

---

### Post by andthewicked on 2010-08-10
I've been seeing this everywhere and I haven't found a good fix for it just some questionable work around s This needs to be sent back to the developers to be fixed in some update or something, it sucks I can't run any graphics dependent program, pluss there is no easy way to downgrade back to 9.10 without having to back up and do a clean reinstall, I hate back ups so I try to stay away from them but I might not have a choice. As far as I've read this is not a driver problem but a linux kernal problem or something I'm not really sure just that its on the linux side not the nvidia side. So we'll see

---

### Post by Zarckon on 2010-08-11
I've just developed the problem as well. Not at all sure what's happened. Kind of discouraging that it's been happening to people since about May and no solid fixes yet.

---

### Post by Termaim on 2010-09-12
I have run into the same issue on boot up in Kubuntu 10.04 after a recent install of it.  Sometimes I can reboot from gdm w/out logging in and it solves it (for some reason it loads gdm instead of kdm when it gives me this error), and other times I have to log into kde and then uninstall/reinstall the nvidia driver and reset all my effects settings...  If anyone has a good solution, please post it :)  It gets really old resetting my advanced desktop and xorg settings all the time...

---

