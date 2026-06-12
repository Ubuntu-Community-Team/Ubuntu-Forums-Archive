---
title: "NVIDIA-CURRENT driver activated but not in use???"
date: 2011-04-29
forum: Multimedia Software
---

### Post by iClouseau88 on 2011-04-29
Hi,

I just installed Natty. Installed nvidia-current via synaptic.  Then uninstalled nouveau via synaptic also.  Back to Unity desktop, I chose Additional Drivers and activated "nvidia-current".
However, after reboot, the info window says this driver is activated but not in use.

How come?

:confused:

---

### Post by casacerian on 2011-04-29
Wondering the same thing. Graphics acceleration is going on; however, the message I am getting is not in sync with what is going on.

---

### Post by Obscura on 2011-04-29
Same issue here.  Tried removing and re-installing the drivers using the utility and synaptic, no luck.

---

### Post by 1Nyco1 on 2011-04-29
Same issue.  Proprietary driver downloaded & installed, but cannot activate.  Can only see program screens in lower resolutions & that disappears on reboot.  Can we get this NVIDIA driver problem in Natty fixed?

---

### Post by Obscura on 2011-04-29
Turns out Unity did not install with the upgrade.  I installed it and everything else started falling into place.

---

### Post by thelunga on 2011-04-29
I have the same problem.

Driver is activated but not in use.

---

### Post by blup on 2011-04-29
My driver panel says exactly the same thing, but the nVidia driver is working and there are no options that I can't use. Perhaps it only says it is not in use even if it is in use?

Hope this helps.

---

### Post by 1915flyer on 2011-04-29
Same driver problem.

When I first upgraded, the desktop icons blinked on and off. No toolbars whatever. I went to classic mode, which worked.

Clean install. Desktop wallpaper only. Nothing else. Unity IS installed. Again, Nvidia driver active but not in use. I'm in the process of installing the Unity 2d drivers so we'll see.

.
.
.

Well, Unity still won't work after loading the 2d drivers.

---

### Post by violet123 on 2011-04-29
I have the same problem. Driver is activated but not in use.  I have nvidia-173 driver installed. Unity is installed but doesn't work,  I can only see wallpaper. Command: ```
 /usr/lib/nux/unity_support_test -p
```
says that my card is "unity supported" and  not blacklisted. Ubuntu Classic works but without desktop effects.

---

### Post by 1Nyco1 on 2011-04-29
> **violet123 said:**
> I have the same problem. Driver is activated but not in use.  I have nvidia-173 driver installed. Unity is installed but doesn't work,  I can only see wallpaper. Command: ```
 /usr/lib/nux/unity_support_test -p
```
says that my card is "unity supported" and  not blacklisted. Ubuntu Classic works but without desktop effects.
Same problem.  Tried to upgrade, then a clean install.  No difference.  There appears to be a problem with nvidia drivers (173).  Mine is installed, but can't be activated.  Reboots sometimes eliminate graphics.  Anyone have a solution?

---

### Post by blocks on 2011-04-29
Same issue here. Unity installed with 11.04, but upon activating the nVidia drivers with the "Additional Drivers" utility and rebooting, Ubuntu reverted to Classic mode and under the utility it says the nVidia drivers are activated but not in use.

I have the NVIDIA® GeForce GT 525M if that matters.

---

### Post by iClouseau88 on 2011-04-29
Hello everyone,

I was the original poster.  Today after rebooting and checking out "Additional Drivers", I found that the dialog window no longer list "nvidia-current" driver.  Instead, I saw:

Broadcom STA wireless driver: this driver is activated and currently in use.

Strange indeed!

---

### Post by iClouseau88 on 2011-04-29
Hi Moderator,

Please withdraw this Post #12 because what I found on screen actually refers to a laptop running Ubuntu 11.04 with ATI Radeon Express 200M, not NVIDIA GeForce 7300GT as in my desktop PC.  Sorry for my confusion.

---

### Post by sdb2028 on 2011-04-29
Anyone got a fix for this problem yet? Would like to see how Unity functions and have my Nvidia card in full use. Meanwhile I'll use classic.

---

### Post by blocks on 2011-04-29
> **1Nyco1 said:**
> Same problem.  Tried to upgrade, then a clean install.  No difference.  There appears to be a problem with nvidia drivers (173).  Mine is installed, but can't be activated.  Reboots sometimes eliminate graphics.

Now on second reboot, x can't start at all. startx says "no screens found."

---

### Post by spikoley on 2011-04-30
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207") on this issue.  Add your details to the bug report, so it will get fixed sooner.

It looks like this issue is caused by jockey (Additional Drivers).

---

### Post by Imago Maeror on 2011-04-30
Hi!

Just if it matters, I have the same problem here when i use the additional drivers. I run Ubuntu 11.04 on a Dell Vostro 3750 with NVIDIA GT525M.

I think for the moment the best thing is to use the standard chipset grafics, unity works with them, and wait for a fix of NVIDIA-Current.

I will take a look at the bugreport, too.

---

### Post by blocks on 2011-04-30
> **Imago Maeror said:**
> Hi!

Just if it matters, I have the same problem here when i use the additional drivers. I run Ubuntu 11.04 on a Dell Vostro 3750 with NVIDIA GT525M.

I think for the moment the best thing is to use the standard chipset grafics, unity works with them, and wait for a fix of NVIDIA-Current.

I will take a look at the bugreport, too.

I have the exact same video card...Yeah, I guess I'll just keep an eye on the bug report and stick with my Intel graphics until this is resolved. Thanks for your response.

---

### Post by jimmybond on 2011-05-01
I'm having the same problem as someone in the bug report listed above after the Natty upgrade.  The desktop does some flashing when using the default Unity desktop.  I'm using the 173 drivers on an old Geforce 5200 FX card and the same message says the driver is not currently in use.

Ubuntu classic works fine though.

---

### Post by xeddog on 2011-05-01
Remove/Install didn't help me.  I deactivated "current", installed 173 and that didn't work.  So I re-installed current (twice) and that didn't work, and I went to Nvidia and downloaded their current drivers for my GeForce 6200 and installed them.  Still poopoo.  

Worst of all is that I still don't have a window manager working.  I can open a terminal and issue "unity &" command and get Unity working, but I still have to find why no window management.


Wayne

Edit:  I just tried it again and maybe I was a bit hasty.  When I start Unity manually I DO have window management.  I didn't before.  I could open a terminal and there was no window around it.  I couldn't resize or even move the session.  Maybe things are "healing" themselves.  :-)

---

### Post by 1Nyco1 on 2011-05-01
[QUOTE=iClouseau88;10735874]Hi,

I just installed Natty. Installed nvidia-current via synaptic.  Then uninstalled nouveau via synaptic also.  Back to Unity desktop, I chose Additional Drivers and activated "nvidia-current".
However, after reboot, the info window says this driver is activated but not in use.

How come?

This problem with nvidia video drivers is plaguing everyone who upgraded to 11.04 I've tried deleting & reinstalling both drivers (in sequence) to no avail. I can get my programs to appear in 1360X768 resolution, but not in any other. I've scanned dozens of posts on Ubuntuforums & other sites about this. No solutions are working, but a bug report has been filed (Medium importance!). There are several extremely complicated recipes posted. None work and most result in other functional problems. And it's affected several other popular graphics chips.
Hey, I'm not a programmer. I've used Ubuntu for two years and loved it. I've recommended it to many of my friends & colleagues. I deeply resent Cannonical releasing a major upgrade with a serious flaw. There are thousands of Ubuntu users who cannot use their computers because of this highly touted "upgrade". GET IT FIXED! Linux/Ubuntu's reputation for device driver problems will be further degraded the longer this goes on. If you want to gain user base with casual Windows users this is NOT the way to do it.

---

### Post by iClouseau88 on 2011-05-02
Hi everyone,

I just logged in launchpad.net.  Apparently Bug#771788 is confirmed but has NOT been assigned. The more people report and post comment in launchpad, the sooner it get fixed, hopefully!

---

### Post by NadirPoint on 2011-05-02
I see this reported in drivers dialog, but that is all.  I mean nothing logged, Unity running fine, wicked fast and absolutely gorgeous actually.  GE460.

Dunno.  Maybe the only bug at least as far I am concerned is what's being reported in the dialog.  :confused:

---

### Post by mc4man on 2011-05-03
There are multiple bugs here, not the same - 

For some cards, typically fx 5200 or 5000 series and some others
With the nvidia-current drivers (173.XX
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178)

Same cards with the nouveau 3d drivers
[https://bugs.launchpad.net/unity/+bug/762478](https://bugs.launchpad.net/unity/+bug/762478)

Bug where jockey reports nvidia-current drivers not activated but really are (ie. doesn't matter much except for confusion
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

And there may be some newer cards using nvidia-current that aren't working - should be another different bug

---

### Post by Seti on 2011-05-03
same problem here with my GeForce GTS 250
aww shucks Ubuntu too bad you're the worst distro evar.
good thing I still have Debian Stable on another partition where I don't have any of this kind of nonsense going on.
FAIL

---

### Post by KVZTA on 2011-05-03
I only got my problem after the last set of updates that were pushed out. Surprised when I JUST reached home from a hard exam to see the message saying that I do not meet the hardware requirements while I've been using Unity for the longest while [after finally getting accustomed to it]. This issue is irritating. Using a GeForce 7300 SE/7200 GS <hand me down xD> ...Just set the recommended driver (version current) instead of the version 173 I was using. Hoping this fixes the issue.

-Didn't work. waiting to see if updates fix the problem

---

### Post by bigfootnmd on 2011-05-03
Last night when I shut down my 11.04 desktop I had the same problem.

This afternoon I watched a video clip off of CNN and the colors were perfect? I do not recall any updates coming down.  So, I put in the same DVD that I had yesterday (with 1965 quality colors) and all the colors today are great.  So, I checked a few things.
Additional drivers still tells me that the 4/15 driver is activated but not in use.  The previous version 173 is also there  but not active.  So, for now at least the colors are fine.

Update:

I forgot about the Nvidia settings manager.  I ran it.  It shows 
System Information
Operating System Linux-x86
NVIDIA Driver version 270.41.06

So, despite what Additional drivers may say, at least for me 270.41.06 (which is the version that was installed when I upgraded from 10.10 to 11.04) is indeed running and the colors in DVD's and other video files could not look better (well if I had an HD video card and HD monitor).

Go figure

---

### Post by Chilongola on 2011-05-03
On my first install I loaded the "recommended" drivers.  Everything just froze.

I then Install the "173" and it flew like a kite.

For another reason I had to do a clean re-instal and this time I loaded the "173" and it works beautiful.  In the meantime will avoid loading updates.

By the way Loading drivers from synaptec did not work.

---

### Post by gwoodruff on 2011-05-03
I had the same driver issue using Nvidia-current. I believe the bug is in reporting as the driver is being used. If you can launch the Nvidia settings manager it will confirm the driver version and if it is in use or not.

Nvidia Driver Version = 270.41.06

---

### Post by forkd on 2011-05-05
Have you tried this solution?

[http://ubuntuforums.org/showthread.php?p=10773905#post10773905](http://ubuntuforums.org/showthread.php?p=10773905#post10773905)

I now have the nvidia-current driver working well and VDPAU is cranking great.

---

### Post by winchendonsprings on 2011-05-06
Same issue.

10.10 > 11.04 is my worst upgrade since 8.04. This amongst 3 other major issues.

I haven't even tried to use unity yet, still using gnome classic and having major flickering issues.

[IMG]http://dl.dropbox.com/u/545099/driver.png[/IMG]

---

### Post by vishnumrao on 2011-05-07
> **1Nyco1 said:**
> 
How come?

This problem with nvidia video drivers is plaguing everyone who upgraded to 11.04 I've tried deleting & reinstalling both drivers (in sequence) to no avail. I can get my programs to appear in 1360X768 resolution, but not in any other. I've scanned dozens of posts on Ubuntuforums & other sites about this. No solutions are working, but a bug report has been filed (Medium importance!). There are several extremely complicated recipes posted. None work and most result in other functional problems. And it's affected several other popular graphics chips.
Hey, I'm not a programmer. I've used Ubuntu for two years and loved it. I've recommended it to many of my friends & colleagues. I deeply resent Cannonical releasing a major upgrade with a serious flaw. There are thousands of Ubuntu users who cannot use their computers because of this highly touted "upgrade". GET IT FIXED! Linux/Ubuntu's reputation for device driver problems will be further degraded the longer this goes on. If you want to gain user base with casual Windows users this is NOT the way to do it.

Not sure the rant is appropriate. Ubuntu's 6 monthly releases are not as stable as their LTS releases. The normal releases are more like the Debian unstable branch. No warranty! If you are looking for absolute stable system, then use 10.04 LTS. 

I too am affected by this bug. If Ubuntu were to cause such a mess in a LTS release, I too would have been very upset. But for now, its ok! Unity is a big leap and a strong change of direction. Though lacking in features and stability, its good to show desire for change and risk. That is precisely why Ubuntu is where it is today. The most popular Linux distro!

---

### Post by 1Nyco1 on 2011-05-07
> **vishnumrao said:**
> Not sure the rant is appropriate. Ubuntu's 6 monthly releases are not as stable as their LTS releases. The normal releases are more like the Debian unstable branch. No warranty! If you are looking for absolute stable system, then use 10.04 LTS. 

I too am affected by this bug. If Ubuntu were to cause such a mess in a LTS release, I too would have been very upset. But for now, its ok! Unity is a big leap and a strong change of direction. Though lacking in features and stability, its good to show desire for change and risk. That is precisely why Ubuntu is where it is today. The most popular Linux distro!
The specific differences between a LTS release and the regular 6 month releases escape the casual user.  Cannonical itself and through the online reviews over the last 6 months have touted 11.04 and its Unity interface as the Next Step.  The Beta reviews were glowing and nowhere did I read cautions about 11.04 being incomplete or inappropriate for everyday use.  My rant was in the frustration of 11.04 making my computer unusable.  I have since calmed down, a little.  I see by your hardware list that you probably have the same Nvidia driver problem as me.  Since you are a more experienced user have you come up with any solution/workaround?  I've managed to get 1920X680 screen resolution, but in a short while my Unity sidebar icons and the top banner become unreadable.  When do you see a solution forthcoming and how will it be made known?

---

### Post by polka123 on 2011-05-07
Hi, I have a related problem so can anyone please advise what graphics card/s will work with 11.04?
I am having problems with my geforce 7300le using the 270.41.06 driver, the cursor works but nothing on screen works i.e. the icons in the side bar do nothing if you double click them. I have searched the forums and lots of people appear to have similar problems but sadly there are no real answers yet. So I want to look at changing my graphics card to resolve the problem. 

Thanks
Rod

---

### Post by spikoley on 2011-05-07
> **1Nyco1 said:**
> When do you see a solution forthcoming and how will it be made known?

You can follow the [bug report here]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Make sure that you mark it as effecting you.  It will help them know it is widespread and needs to be fixed ASAP.

---

### Post by vishnumrao on 2011-05-07
> **polka123 said:**
> Hi, I have a related problem so can anyone please advise what graphics card/s will work with 11.04?
I am having problems with my geforce 7300le using the 270.41.06 driver, the cursor works but nothing on screen works i.e. the icons in the side bar do nothing if you double click them. I have searched the forums and lots of people appear to have similar problems but sadly there are no real answers yet. So I want to look at changing my graphics card to resolve the problem. 

Thanks
Rod


I installed Ubuntu 11.04 for a friend of mine. It had a onboard graphics ( 4200 series) on the MSI 880G-E45 motherboard. Unity works like a charm. I think AMD's opensource drivers and their proprietary drivers have matured quite a bit. Since you ask what graphics cards work with 11.04, I suggest you definitely try an AMD/ATI card!

---

### Post by polka123 on 2011-05-07
Thanks a lot Vishnu I will give that a try.
 
Rod

---

### Post by sstvinc2 on 2011-05-11
Having the same problem.  Tried the /etc/default/grub fix, but to no avail

---

### Post by qva5 on 2011-05-18
I'm having similar problem with 11.04, nvidia-current drivers and GT 525M card.  I've tried several solutions, modifying GRUB, installing experimental nvidia drivers, and re-installing kernel headers, so far nothing has helped.    With every unsuccessful attempt I'm more convinced that this is general problem with nvidia drivers.    Surprisingly Unity works just fine when I launch Ubuntu 11.04 from live CD. Does somebody know why it's working just fine when running from CD, but not from installed system????

---

### Post by Mia1990 on 2011-05-19
I have this problem as well no unity driver showing installed but not in use or something like that.I installed the nouveau Gallium3D driver then unity showed up the driver is fast but the launcher has no icons on it so now i am going to install the driver i downloaded from nvidia's website the only problem is it is a run file and i don't know how to install it so if anybody has done this could you help me and if this didn't help let me know so i don't try to do this.

Thank you

---

### Post by UniverseA7X on 2011-05-23
I'm running Kubuntu here, and I'm stuck in the same situation as well: no 3D and low resolution on a computer that functioned with earlier versions.

What I did want to mention though was that an experimental free driver popped up on the additional drivers utility, so I decided to try it out. Some 3D function was restored, such as fading windows and an animated menu, but I'm still stuck at the same resolution. Thoughts on this?

---

### Post by vikashiiitdm on 2011-06-08
/usr/lib/nux/unity_support_test -p

gives  Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context


what should i do?

---

### Post by obvious_hat on 2011-07-19
I had the same problem, however, I managed to fix it by firstly trying to use
```
sudo apt-get install nvidia-current
```
I'm not sure this did anything as I used a combination of things, it might have, though.

Then I used synaptic package manager to search for the unity things. I found that the already installed unity things had exclaimation marks in the boxes, as opposed to the green already installed button. I then selected the upgrade option and restarted.

This seemed to fix it.

Hope it works for you!:)

---

### Post by Club17 on 2011-07-28
Same trouble here on my ASUS N53S

Kernel 2.6.38-10-generic

x86_64

GNOME 2.32.1

> club17@N53SV-LM ~ $ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.

And the xorg.conf appears:

> 
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


What can I do?

---

### Post by venik212 on 2011-07-30
I have the very same ridiculous problem-- I am told I already have the current version of the Nvidia driver, but it is not in use.  I have no idea how to get it to be used.  XP never looked more robust than since Natty appeared...

---

### Post by qva5 on 2011-07-30
Have you tried using bumblebee? I hope it will help.

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

Apparently there is a problem with latest nvidia cards with optimus support and linux.

---

### Post by NoCupLoser on 2011-08-01
Okay so I too am having issues with this. Today marks my 3rd day of use with Ubuntu (or any other Linux bases OS). A lot of what has been stated within this forum is still a little foreign to me, though I'm learning fast. I primarily switched to Ubuntu for the purpose of being able to play a few of my (semi-low-fi) games (yes they are Windows-PC games that I'm attempting to run with Wine 1.2) without having to deal with all the excess useless processes Windows OS' try running in the background. In the last month I have switched from Win XP Pro sp3 to Win 7 sp1 to Ubuntu Natty 11.04.
My experience with Win 7 was about all I could take and after 10+ yrs of running Windows OS' I'm SICK of MS. I have an older laptop with crappy on-board nvidia graphics and the processes in Windows xp make it slower...then come to find out in Win 7 they fixed the redundancy of requests for ram for certain processes by ONLY requesting ram once...porting it through my already taxed graphics card....

So now I'm learning an entirely new and semi-overwhelming new OS....and find that although it is confusing, I do understand to an extent how it works. I love the fact that it doesn't load a ton of crap dll's and processes such as having 5 processes for internet access only 2 of which are even needed to access the internet the others are just monitors not even related to security ect..... Overall I'm liking alot about Ubuntu however, atm my laptop is a fancy paperweight that i can still watch movies on,  but gaming is out...and I still wanna give ubuntu a fair shake and learn  more rather than installing yet again another OS

okay so now that I'm done babbling...this bug is listed as "Medium" Importance....what does that mean...1 month for a fix? 3 months? any ideas?

---

### Post by NikS on 2011-08-21
Same problem.. My card is nVidia GT 430. One thing I just noticed, there is an option under 'system-->administration' by name 'NVIDIA X Server settings'. It doesnt seem to show any issues in the card or the driver! :confused:

---

### Post by John_T on 2011-08-21
I have the same (or certainly related) issue, but with a new installation.

Brand new MSi laptop with GT540M (1 GB)and 8GB regular RAM. 64 Bit Ubuntu 11.04

I tried running "NVIDIA XSERVER SETTINGS" from the system menu, and received the following dialog.

[IMG]http://img808.imageshack.us/img808/3687/nvidiaxservermessage.png[/IMG]

I tried the suggestion from the dialog, but it doesn't work, and may also break your X startup. If the latter happens, you'll have to copy the backup xorg.conf back over the previous one.  It's in "\etc\X11\".  I did the following:

```
cd /etc/x11
sudo cp xorg.conf xorg.conf.broken
sudo cp xorg.conf.backup xorg.conf
```

and I could boot with a GUI again.

---

### Post by theappe on 2011-08-29
Having the same issue as well. Driver installed, but says its not active. NVIDIA doesnt work

---

### Post by northd_tech on 2011-11-11
There is a good NVIDIA writeup that covers removing the **nouveau** open-source module here:
[B]
BinaryDriverHowto[/B]
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I was looking for some info on blacklisting the **nouveau** module and discovered that it has no 3D acceleration anyway (so I'm opting for the "--purge remove xserver-xorg-video-nouveau" method).  I've tried blacklisting **nouveau** in a few places and it seems to keep interfering with my much more recent updated NVIDIA 280.13 driver for whatever reason(s).

Edit:  You can see which combination of module(s) you have loaded with this terminal command:

```
lsmod | egrep 'nv|nou'
```

Also, you can check for NVIDIA and nouveau blacklisting with this command (so long as your system follows the 'blacklist.' convention):

```
 egrep 'nvid|nouv' /etc/modprobe.d/black*.*
```

---

### Post by beew on 2011-11-11
I think that is old info, since 10.10 I don't remember having to remove nouveau, if the Nvidia closed source driver is present it will get loaded automatically. I have no issue activating Nvidia in 10.10, 11.04 and 11.10 without going out of my way to blacklist or remove nouveau.

---

### Post by northd_tech on 2011-11-11
**nouveau** was and possibly is still giving me fits with 2 of my 3 installed kernels under Lucid Lynx 10.04.3 LTS this very evening- I used the Synaptic method to remove **nouveau**, but I still need to restart and test all 3 kernels more extensively to see if the NVIDIA Driver(s) and X Server Settings are working properly.

---

### Post by beew on 2011-11-11
> **northd_tech said:**
> **nouveau** was and possibly is still giving me fits with 2 of my 3 installed kernels under Lucid Lynx 10.04.3 LTS this very evening- I used the Synaptic method to remove **nouveau**, but I still need to restart and test all 3 kernels more extensively to see if the NVIDIA Driver(s) and X Server Settings are working properly.

Yeah, in 10.04 you may have to blacklist/remove it. I think starting with 10.10 that was no longer the case.

---

### Post by preserve on 2012-04-16
Tried many of the options but this was the only one that worked for me in Natty:
Edit the file for nvidia in /etc/modprobe.d

sudo vi /etc/modprobe.d/nvidia-graphics-drivers.conf   # it's a soft link

Original file reads:

blacklist nouveau

Added these lines:

blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
alias nvidia nvidia-current

Reboot and Nvidia becomes activated! Note: that file is replaced with a nvidia upgrade without the "alias nvidia nvidia-current" line.

---

### Post by bear_out_there on 2012-11-17
So after the last set of updates on 12.04 my displays went to 640x480. Following many uninformed suggestions on this forum I've done all of the following:
1.  Removed all of nvidia drivers:  sudo apt-get purge nvidia-173 nvidia-173-updates nvidia-current nvidia-current-updates nvidia-settings nvidia-settings-updates
2.  Removed jockey and reinstalled it through the software center
3. Installed all of the nvidia drivers in different combinations: sudo apt-get install nvidia-173 etc.
4.  Tried removing blacklisting of different drivers
5.  Updated xorg.conf by sudo nvidia-xconfig until i was blue in the face

All of that lead to the same 2 problems:
1.  Driver is activated but not in use in jockey
2.  You don't appear to use nvidia driver in nvidia-settings

I was about to give up when i came across a mention of nvidia-common.  Installing it, sudo apt-get install nvidia-common, at first added descriptive text to the driver listings in jockey.  Activating driver in jockey went without any problems.  And the proper resolution was restored after the very next reboot.  Nvidia settings worked like magic as well.

So don't forget to install / re-install nvidia-common package.

Good luck.  Hope this saves someone 2 hours.  I'll sure never get them back.

---

### Post by sam1948 on 2013-04-13
in ubuntu 12.10 this one solved my problem
[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

* install glxgears with "apt-get install mesa-utils"
* start nvidia in openGL uncheck "synch to vblanc"
* run "glsgears" in command line and wait for retes to show on the terminal. it should be few thousends

---

