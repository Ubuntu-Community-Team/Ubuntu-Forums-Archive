---
title: "Fresh natty install - two big problems"
date: 2010-11-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-11-30
I just did a fresh install of Natty (Nov 30 ISO) in my testing partition. The install itself went well, but i have two problems.

1) The reason I did the fresh install was because every time I updated grub from my prior Natty install, it would not detect my Maverick installation on a separate partition and I would have to boot to a Live CD and reinstall grub (Maverick's version). That would detect and configure both Maverick and Natty. It was a pain and I hoped a fresh Natty install would handle it, correctly. But, at the end of the fresh installation, it informed me that it did not detect any other OS's and gave me the option to not install grub. I took that option, but it installed Natty's grub, anyway. I had to do the Live CD grub-install, again.

I can find no bug reports on launchpad that match this problem. Am I the only one having it?

2) In Natty, I added the xswat ppa and installed nvidia-current. It installed, successfully, but when I rebooted, it comes up with a desktop background, only. No panels or other controls. Is Natty incompatible with nvidia-current?

Tim

---

### Post by ronacc on 2010-11-30
I don't know about #1 but as to #2 I updated this AM and lost part of my desktop , I have background and panels but no DT icons , nautilus wont run from menu or term , installed pcmanfm for a filemanager while I straighten things out . probably a later update will clear things , until then run things from the menu or term .

---

### Post by mc4man on 2010-11-30
> Is Natty incompatible with nvidia-current?
fully updated, works fine w/ nvidia-current from ubuntu repo - don't know why you'd want to use xswat for this anyway.

---

### Post by Harry33 on 2010-11-30
> **mc4man said:**
> fully updated, works fine w/ nvidia-current from ubuntu repo - don't know why you'd want to use xswat for this anyway.

That is correct.
The xswat nvidia-current version is 260.19.21-0ubuntu1~xup
and Natty repos version is 260.19.21-0ubuntu1.
Basically they are the same.

And yes Natty is fully compatible with nvidia-current and has been compatible all the time.

---

### Post by ratcheer on 2010-11-30
> **Harry33 said:**
> That is correct.
The xswat nvidia-current version is 260.19.21-0ubuntu1~xup
and Natty repos version is 260.19.21-0ubuntu1.
Basically they are the same.

And yes Natty is fully compatible with nvidia-current and has been compatible all the time.

No, I got some higher version from xswat, but I don't remember what it was. Anyway, after I installed that driver, my desktop stopped working. All I had was a background and a cursor pointer. To fix it, I reinstalled Natty and installed the nvidia-current from the Ubuntu repository. So, my original question #2 is solved, in a way.

On the other problem, I have created bug 683355 on launchpad. The problem has something to do with os-prober 1.41. Once I determined that the problem was os-prober instead of grub2, I can see that lots of people are having the same problem. Question #1 remains open.

Thanks,
Tim

---

### Post by terry_gardener on 2010-12-01
i dual boot between win 7 and natty. my grub seems to be working ok, detected win 7 and never lost it. 

i installed maverick and then upgraded from there, haven't installed fresh yet.

---

### Post by ronacc on 2010-12-01
your problem with no panels or desktop are really 2 seperate problems , the no desktop is due to nautilus failing to start , the only current way around that is to use unity or gnome-shell , the no panels is due to the panels being deselected by default ,the cure for that is here .
[http://ubuntuforums.org/showthread.php?t=1634486](http://ubuntuforums.org/showthread.php?t=1634486)
see post #10 for a permenent fix .

---

### Post by Harry33 on 2010-12-02
> **ratcheer said:**
> No, I got some higher version from xswat, but I don't remember what it was.
...
Thanks,
Tim

There were no higher version in X Updates (xswat) than in Natty official repos:
nvidia-graphics-drivers - 260.19.21-0ubuntu1~xup.

Now, since today (6 hours ago), there is a new beta version in X Updates (xswat)
nvidia-graphics-drivers - 260.19.26-0ubuntu1~xup.

Here is the link to this xswat PPA (Natty):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)

---

### Post by dino99 on 2010-12-02
have deactivated x-swat ppa on my end because it dont upgrade all the nvidia packages at once (only current & current-modaliases) and there is no improvement with the newest .26 package anyway.

---

### Post by ratcheer on 2010-12-02
> **ronacc said:**
> your problem with no panels or desktop are really 2 seperate problems , the no desktop is due to nautilus failing to start , the only current way around that is to use unity or gnome-shell , the no panels is due to the panels being deselected by default ,the cure for that is here .
[http://ubuntuforums.org/showthread.php?t=1634486](http://ubuntuforums.org/showthread.php?t=1634486)
see post #10 for a permenent fix .

After the second fresh install that day, everything on the desktop is now working, properly.  The bug with os-prober is still open.

Tim

---

### Post by BobCFC on 2010-12-02
[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355)

---

### Post by ratcheer on 2010-12-03
> **BobCFC said:**
> [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355)

Yes, that is the bug report I filed.

Tim

---

### Post by BobCFC on 2010-12-04
Heh it wasn't aimed at you.;) I had to google search your bug I was saving time for the others.

I got around it so far by copying the menuentry from my Maverick grub.cfg to the /etc/grub.d/40_custom section of the Natty instally and running sudo update-grub

Hopefully the 40_custom file will remain intact when grub updates.

---

### Post by ratcheer on 2010-12-04
Oh, sorry.

So, did copying the Maverick grub.cfg file work? I never would have thought of that.

Tim

---

### Post by zenarcher on 2010-12-04
> **mc4man said:**
> fully updated, works fine w/ nvidia-current from ubuntu repo - don't know why you'd want to use xswat for this anyway.

What series Nvidia card are you using?  I'm wondering if all is working with the Nvidia 8xxx series cards.  Maverick has not worked with them for me.

Cheers,
zenarcher

---

### Post by cariboo on 2010-12-05
I have Natty running on 5 systems, all but one have Nvidia graphics cards. The oldest system has a 6600GT AGP card, I'm running the whole testing cycle using the nouveau drivers on this one. The other 3, 8400GS, 9400GT and 210GT all use nvidia-current with no problems. All cards are from different manufacturers.

---

### Post by na5m on 2010-12-05
Your #2:  I had a similar problem after I installed the ATI
proprietary drivers. When I rebooted, only a blank desktop
& mouse pointer appeared. I waited ~30 second for the panel
 and some icons to show up, but they never did. Maybe a wait
of around 1 minute would have helped. Anyway, I didn't wait.
I Ctrl+Alt F1, got a root shell & **# reboot**
When I got to the login screen, I chose "Ubuntu Classic" as
my default session. When I logged in, I still got a blank
desktop, but after around 20 agonizing seconds, the panel & icons
began to show up. Things have been fine ever since.

Your #1:  Natty's grub2 detected my Win7 install and my Linux Ultimate
Edition with no problem (they are both installed on primary partitions).
Maybe you have a tricky partition scheme going on on
your machine.

ubuntu_natty_amd64_alternate

---

### Post by mc4man on 2010-12-05
> **zenarcher said:**
> What series Nvidia card are you using?  I'm wondering if all is working with the Nvidia 8xxx series cards.  Maverick has not worked with them for me.

Cheers,
zenarcher
I'm surprised to here that, both for maverick and natty. (if you're referring to card in your sig.
Have a 7800 OC AGP and 8400m GS. While the desktop ( p4, AGP) could certainly use replacing, both perform reasonably well. Actually atm natty runs a bit better on the desktop than maverick.
You should take a look at your 'method'(s) to try enabling nvidia-current, no reason for it not to work on any 8xxx card, maverick or natty.

---

### Post by zenarcher on 2010-12-05
> **mc4man said:**
> I'm surprised to here that, both for maverick and natty. (if you're referring to card in your sig.
Have a 7800 OC AGP and 8400m GS. While the desktop ( p4, AGP) could certainly use replacing, both perform reasonably well. Actually atm natty runs a bit better on the desktop than maverick.
You should take a look at your 'method'(s) to try enabling nvidia-current, no reason for it not to work on any 8xxx card, maverick or natty.

Well, I haven't been alone with the issue involving the Nvidia 8xxx cards and Maverick.  Several people have had the same problem.  I tested Maverick (Kubuntu 63 bit), starting with Alpha 1.  Everything was fine all the way through the testing process until the Final Release. Even the RC was fine.  No problems at all.  Then came the final release.  Everything was fine with the Nouveau driver, but when the Nvidia proprietary driver was installed, the problem came in.  When you would reboot, following the installation of the proprietary Nvidia driver, all you get is a sleeping monitor.  I get the BIOS splash screen and following that, the monitor merely goes to sleep.  Nothing further.  Same situation after several fresh install attempts on four of my systems with the same Nvidia card.  Did an install with the older Nvidia FX 5xxx card and all is fine.  Only seems to affect the Nvidia 8xxx series cards.  

I've followed the same procedure as I have for the past three or four Kubuntu releases and the same procedure on Maverick from Alpha 1 through RC without problems.  I did note some work arounds people have tried for the problem, but none of those seemed to work for me.  In the end, I had to switch my systems over to Debian Squeeze, which works fine, but I would prefer to be using Kubuntu again, as I have for the past three or four years.

BTW:  I should have mentioned that Kubuntu continues to load, although the monitor is sleeping, at least from what I see from the light for hard drive activity.

Cheers,
zenarcher

---

### Post by sonicb00m on 2010-12-05
How do we fix the Desktop wallpaper only showing with no panels? This happened as soon as I installed the ATI Prop. driver.

I'm desperate to play with gnome shell but now nothing works at all.

I installed gnome-shell on my meerkat installation but it's slow and unusable and I read in the bug report this should have been fixed in the Natty alpha.

---

### Post by dino99 on 2010-12-05
old method (without unity): metacity --replace &

with unity: compiz --replace &

---

### Post by dino99 on 2010-12-05
> **zenarcher said:**
> Well, I haven't been alone with the issue involving the Nvidia 8xxx cards and Maverick.  Several people have had the same problem.  I tested Maverick (Kubuntu 63 bit), starting with Alpha 1.  Everything was fine all the way through the testing process until the Final Release. Even the RC was fine.  No problems at all.  Then came the final release.  Everything was fine with the Nouveau driver, but when the Nvidia proprietary driver was installed, the problem came in.  When you would reboot, following the installation of the proprietary Nvidia driver, all you get is a sleeping monitor.  I get the BIOS splash screen and following that, the monitor merely goes to sleep.  Nothing further.  Same situation after several fresh install attempts on four of my systems with the same Nvidia card.  Did an install with the older Nvidia FX 5xxx card and all is fine.  Only seems to affect the Nvidia 8xxx series cards.  

I've followed the same procedure as I have for the past three or four Kubuntu releases and the same procedure on Maverick from Alpha 1 through RC without problems.  I did note some work arounds people have tried for the problem, but none of those seemed to work for me.  In the end, I had to switch my systems over to Debian Squeeze, which works fine, but I would prefer to be using Kubuntu again, as I have for the past three or four years.

BTW:  I should have mentioned that Kubuntu continues to load, although the monitor is sleeping, at least from what I see from the light for hard drive activity.

Cheers,
zenarcher

try: sudo grub-mkconfig && sudo update-grub

---

### Post by zenarcher on 2010-12-05
> **dino99 said:**
> try: sudo grub-mkconfig && sudo update-grub

Thanks for that info, dino.  I'll probably try a fresh install on my test system and give your suggestion a try.  When I get time, I'll do so and let you know how that works out.

Thanks,
zenarcher

---

### Post by zenarcher on 2010-12-05
> **dino99 said:**
> try: sudo grub-mkconfig && sudo update-grub


Okay, obviously, I'm doing something wrong in trying to get the proprietary Nvidia drivers working with Natty....and with the final release of Maverick, as well.  Since all was fine to that point, I'm not sure where I went wrong.

I just did a fresh install of Kubuntu Natty, followed by all available updates.  All works fine with the nouveau video driver.  I then installed the proprietary Nvidia driver (recommended one) and rebooted.  I'm back to the same point I was at with the final release of Maverick.  At boot, I get the BIOS splash....then I get a large, blocky Kubuntu splash for a couple of seconds, then my monitor goes to sleep.

I then ran sudo grub-mkconfig && update-grub which seemed to work properly.  I rebooted and still have the same situation.  I get the BIOS splash, followed by a second or two of Kubuntu splash...then, a sleeping monitor.  If I push and hold the power button to shut the computer down, right before it shuts off, I see a second or two of the screen again, as the monitor wakes up right before going to sleep.

I'm going to leave the system sitting like this for a bit and see if anyone has any suggestions.  I'd really like to get Kubuntu working again, as it is my favorite distro, but since the final release of 10.10, it's been impossible.  I get the same situation with 4 different computers and a fresh install.  Yet, everything worked fine on one system using an Nvidia FX5200 video card with the proprietary driver.

I'm at a loss.  Any help would be appreciated.

The video card and hardware are correct in my signature.

Cheers,
zenarcher

---

### Post by mc4man on 2010-12-05
If you're doing a power button shutdown then I'd cut the power to the machine for 30 sec's (either a switch on back of the case or pull the power cord.
If you can get to any prompt (recovery mode) then try 

sudo nvidia-xconfig or nvidia-xconfig

Or ```
sudo apt-get install --reinstall nvidia-current
```
And look if the kernel module is being built, then follow with the xconfig command

Ex. - something like this when nvidia-current is either being installed or re-installed
> Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-current (260.19.06-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-260.19.06 DKMS files...
Building only for 2.6.35.7-ck1-wellsee
Building for architecture i686
Building initial module for 2.6.35.7-ck1-wellsee
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35.7-ck1-wellsee/updates/dkms/

depmod....

DKMS: install Completed.


---

### Post by zenarcher on 2010-12-05
Well, I don't know if this is any help or not in troubleshooting, but here is what I have discovered.  Someone on the Kubuntu forum insisted that it was due to my running my computers through a KVM switch, although that has never been a problem before.

It's not a simple matter of merely routing around the KVM switch, as that would require a couple of hours of moving equipment.  So, I took a different approach.

I removed the test computer from the system and set it up with a separate monitor, keyboard and mouse.  Just to give it a try.

Using a separate monitor, keyboard and mouse, I get exactly the same situation.  The monitor immediately goes to sleep.  This particular computer also has onboard video, which I do not use, since the other computers do not and all have the same Nvidia card in them.

I changed the video in the BIOS to use the onboard video, which is an Nvidia 6150SE chipset.  I rebooted the system using the onboard video and everything works perfectly....Nvidia proprietary driver is working as it should.

Now, I switch back to the PCI-E Nvidia 8XXX series card and I'm back to a sleeping monitor, right after the BIOS splash screen.  

So, quite obviously, it has nothing to do with the KVM switch being in the system.  Everything works fine, with the Nvidia 6150 Graphics card in use with the Nvidia proprietary driver installed.  Yet, the monitor immediately goes to sleep, once I activate the Nvidia 8xxx video card.

Any thoughts from there?

Cheers,
zenarcher

---

### Post by zenarcher on 2010-12-05
> **mc4man said:**
> If you're doing a power button shutdown then I'd cut the power to the machine for 30 sec's (either a switch on back of the case or pull the power cord.
If you can get to any prompt (recovery mode) then try 

sudo nvidia-xconfig or nvidia-xconfig

Or ```
sudo apt-get install --reinstall nvidia-current
```
And look if the kernel module is being built, then follow with the xconfig command

Ex. - something like this when nvidia-current is either being installed or re-installed

I followed your instructions here...got exactly where you show I should get.  But, when I reboot, I'm back to the same issue.  BIOS splash screen....then the monitor goes back to sleep.

Incidentally, these are two different sizes of monitors I'm trying.  My main one is a 21 inch widescreen LCD and the one I'm testing with is a 19 inch widescreen LCD.

Cheers,
zenarcher

---

### Post by cariboo on 2010-12-05
Is you monitor being detected properly, because thats what it sounds like the problem is. I use a KVM on one of my systems, and monitor detection was iffy  at times

Could you post a copy of your /etc/X11/xorg.conf

---

### Post by zenarcher on 2010-12-05
> **cariboo907 said:**
> Is you monitor being detected properly, because thats what it sounds like the problem is. I use a KVM on one of my systems, and monitor detection was iffy  at times

Could you post a copy of your /etc/X11/xorg.conf

At the moment, I don't even have the KVM switch in the system.  I have removed the computer from my regular system, which uses the KVM switch and I'm running it with it's own monitor, keyboard and mouse...and still have the same problem.  I'll see if I can get a copy of the xorg.conf file and copy it here.  Just a couple of minutes.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-12-05
> **cariboo907 said:**
> Is you monitor being detected properly, because thats what it sounds like the problem is. I use a KVM on one of my systems, and monitor detection was iffy  at times

Could you post a copy of your /etc/X11/xorg.conf

Okay, here is a copy of my /etc/X11/xorg.conf file.......

Section           "Screen"
                  Identifier     "Default Screen"
                  Default Depth   24
EndSection

Section           "Module"
                  Load   "glx"
EndSection

Section           "Device"
                  Identifier       "Default Device"
                  Driver           "nvidia"
                  Option           "NoLogo"   "True"
EndSection


Cheers.
zenarcher

---

### Post by cariboo on 2010-12-05
I would suggest you start in recovery mode and run:

```
nvidia-xconfig
```

Just to see if it makes a difference. 

I know with my previous crt monitor , I had to run the above command, and then manually set the horizontal and vertical refresh rates in order for things to work the way they should.

---

### Post by zenarcher on 2010-12-05
Okay, here we go with the latest attempt.  

I connected the computer back up in it's normal configuration, through the KVM switch and back on the main 21 inch monitor, shared keyboard and mouse.

This time, I removed the Nvidia 8xxx PCI-E video card and connected to the onboard graphics, which is an Nivida GeForce 6150SE graphics chip.

I did a fresh install of Natty Kubuntu Alpha 1 and ran all available updates.  I then installed the current recommended Nvidia driver.

I rebooted the system and had nothing but a black screen.  Restarted in Recovery Mode and ran sudo grub-mkconfig && sudo update-grub.

Following this, I rebooted the system and everything started up normally, with the Nvidia proprietary driver working as it should, and all working properly.

Likewise, my xorg.conf file is identical to what it was with the Nvidia 8xxx card installed, but I could not get anything but a sleeping monitor.

As such, I think this shows that my KVM switch is not the problem.  Neither is a faulty xorg.conf file.  Everything is working perfectly with the Nvidia GeForce 6150SE onboard video.....and with the Nvidia 8xxx series PCI-E card, nothing but a sleeping monitor.  I don't see the Nvidia 8xxx card as being an issue, since it works perfectly with Debian Squeeze and other distros.

So, now I'm back to the Nvidia 8xxx card being the problem, for some unknown reason, since everything is normal with the Nvidia 6xxx graphics.

I'm open to ideas.  Seems to me I have two choices.  Either use another distro, or invest in three new Nvidia graphics cards for my three systems I use with Kubuntu, unless someone has a solution.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-12-05
> **cariboo907 said:**
> I would suggest you start in recovery mode and run:

```
nvidia-xconfig
```

Just to see if it makes a difference. 

I know with my previous crt monitor , I had to run the above command, and then manually set the horizontal and vertical refresh rates in order for things to work the way they should.


I'll let you take a look at my latest post and attempt, then see if you think this might help my problem, before I try it.

Thanks for the help,
zenarcher

---

### Post by cariboo on 2010-12-05
It wouldn't hurt to try the command, as it creates a backup of the current xorg.conf file. So if it doesn't help, you can always revert to the original.

BTW I have the same motherboard as you on two systems, one with X2 240 CPU and 210GT graphics card, and the other, that is connected to my KVM, with a X2 3800+ CPU and 9400GT.

I also have a system with a HP branded MSI motherboard AMD 3200+ and 8400GS graphics card, it started out with the netbook edition, but has since been updated to the latest version of Unity. None of the systems have given me any problems as far as graphics have been concerned.

---

### Post by zenarcher on 2010-12-05
> **cariboo907 said:**
> It wouldn't hurt to try the command, as it creates a backup of the current xorg.conf file. So if it doesn't help, you can always revert to the original.

BTW I have the same motherboard as you on two systems, one with X2 240 CPU and 210GT graphics card, and the other, that is connected to my KVM, with a X2 3800+ CPU and 9400GT.

I also have a system with a HP branded MSI motherboard AMD 3200+ and 8400GS graphics card, it started out with the netbook edition, but has since been updated to the latest version of Unity. None of the systems have given me any problems as far as graphics have been concerned.

I really like the MSI motherboards.  I try to use them in everything I have.  And, I do like the dual core AMD processors.  I've not had more than maybe one problem with them out of the past eight years or so.  I build my own systems here and have for many years.  Eons ago, I worked in hardware design...back in the late 60's and early 70's.  I'm retired, so I have a lot of time to mess with this stuff.  I'm not so sharp on Linux, but have learned a lot over the past 5 years or so that I've played with it.  I don't run anything but Linux here, except for my tablet, which runs on Android.

I'll give your suggestion a try.  I'll have to put the Nvidia 8xxx card back in the system to do that.  Might take me awhile to get to it, but I will post back with the result.  I really do want to resolve this problem.  Do you have any suggestions as to what might be appropriate for the horizontal and vertical refresh rates?  Or, would I be better off to use the ones which work with Debian Squeeze on my other system?

Oh, I might ask where I can find the refresh rates and such on my working Debian Squeeze system.  Also, how is the best way for me to run nvdia-xconfig.  Should I boot into the recovery mode and run it from there?  I'm assuming as sudo.

Cheers,
zenarcher

---

### Post by cariboo on 2010-12-05
You only need to set the horizontal and vertical refresh rates for crts, I was using a 15 year old KDS 19" crt up until it finally died a month ago. :)

---

### Post by zenarcher on 2010-12-05
> **cariboo907 said:**
> You only need to set the horizontal and vertical refresh rates for crts, I was using a 15 year old KDS 19" crt up until it finally died a month ago. :)

I would set the horizontal and vertical for CRT's, even though I'm using an LCD display?  Just want to be sure of what I'm doing. :P  And, should I run that command while in recovery mode, or just from a terminal, while I have the desktop running?  And, run it as sudo, I would guess.  Is that correct?

Cheers,
zenarcher

---

### Post by cariboo on 2010-12-05
I you're running an LCD, don't worry about the refresh rates.

---

### Post by zenarcher on 2010-12-06
Okay, thanks.  I guess I'm back to square one then with this problem, if there is no reason to mess with the refresh rates.  Yes, I have only LCD displays around here.  My 19 inch test display is the same display I use for my wife's computers, where I have also experienced this issue.  I'm running the Dell LCD display on my system, which appears in my signature file.  Both are widescreens.  Then, I have a couple of other spare LCD displays here, as well, but no CRT displays around at all.

NOTE:  Checking back in on the Kubuntu Forum, I see that this is a very common issue with the Nvidia 8xxx cards and there seems to be no solution for it, but to replace the Nvidia cards.  I'm not real excited about having to replace 3 Nvidia video cards, as that whacks the Social Security retirement budget, but it's apparently that, or have to switch to a different distribution and I'd rather stay with Kubuntu.  The next move, I suppose, is to find out if the same issue exists with the Nvidia 9xxx series cards.

Just out of curiosity, does anyone know if there are problems with the Nvidia GeForce GT210 video card?  My hardware requires that I use low profile video cards in two of my machines, which make them more expensive to get and these seem to be fairly reasonable.  But, I don't want to replace problem video cards with new problem video cards.

Regards,
zenarcher

---

### Post by cariboo on 2010-12-06
What were the results when you ran:

```
sudo nvidia-xconfig
```

I have a 210GT low-profile card made by BFG, and using the restricted driver it works flawlessly. The system it is installed in is connected to an Acer 17" LCD. I was getting the occasional lock up when running the nouveau drivers.

I can't really recommend BFG, as their fans only seem to last for a couple of months, I've replaced two fans I picked up on Ebay for $4.00CDN including shipping that have been running for over a year now with zero problems, and temps are in the low 40's.

---

### Post by ronacc on 2010-12-06
Have you tried hand installing the nvidia driver ? also if you have an  old install that has an xorg.conf that your 8xxx card was working with , try that .

---

### Post by ratcheer on 2010-12-06
I am starting to make some headway on the os-prober / grub2 issue (see post #1 and relevant follow-ups).

Today, there was a new kernel for Natty. When it installed, it gave a grub2 syntax error. I got around the error by running install-grub, which ran without error, but again failed to detect Maverick on the other partition. When I rebooted to Natty, it was using the new kernel.

But, as Maverick is my main-use installation, I have to be able to boot to it. So, once again, I booted to the Maverick Live DVD and installed Maverick's grub2. That detected both Maverick and Natty. Maverick booted fine, but when I booted Natty, it was back on the previous kernel version.

So, on a hunch, I manually ran os-prober in Natty, then ran grub-install, again. That did the trick. I can now selectively boot Natty or Maverick, and when I boot to Natty, it runs the current latest kernel.

This is all to say, things are still quite a mess, but I have learned how to force them to work. I will update my bug report (683355) with this same info.

Tim

---

### Post by zenarcher on 2010-12-07
> **cariboo907 said:**
> What were the results when you ran:

```
sudo nvidia-xconfig
```

I have a 210GT low-profile card made by BFG, and using the restricted driver it works flawlessly. The system it is installed in is connected to an Acer 17" LCD. I was getting the occasional lock up when running the nouveau drivers.

I can't really recommend BFG, as their fans only seem to last for a couple of months, I've replaced two fans I picked up on Ebay for $4.00CDN including shipping that have been running for over a year now with zero problems, and temps are in the low 40's.

Thanks for the great info!  I managed to get sidetracked yesterday and ended up reformatting my test computer and installing a copy of Windows 7.  The first time I've installed or used Windows in about 5 or 6 years.  Made me even happier I use Linux.  I should get a fresh Natty install back in the test system tomorrow.  As of now, I can't remember exactly what I got when I ran sudo nvidia-xconfig, but as I recall, it seemed to run normally, however did not do anything about the issue.  I will try it again, once I have Natty reinstalled.

Thanks for the video card info.  I think I will look into card replacement with the 210's.  That will probably take me a couple of weeks.  I've also had fan problems on a couple of video cards in the past, so will keep that in mind.

Thanks again,
zenarcher

---

### Post by zenarcher on 2010-12-07
> **ronacc said:**
> Have you tried hand installing the nvidia driver ? also if you have an  old install that has an xorg.conf that your 8xxx card was working with , try that .

No, I haven't tried hand installing the Nvidia driver.  I am trying to avoid that, if I can, since I maintain systems for several non-technical people around where I live and don't want to get into a problem with updates, since a few of them also use Nvidia 8xxx series cards.  I'd rather replace the cards for them, if this is going to be an ongoing issue, which it appears to be.

As for the xorg.conf, I have checked the xorg.conf file in my main system, which is currently running Debian Squeeze and an Nvidia 8xxx card (same one) quite well.  It is identical to the xorg.conf file in the Maverick and Natty installs, where the Nvidia 8xxx is causing a problem.  Very odd, to me.  It had to be some change which took place with Maverick Final Release.  Even with the Maverick RC, everything was fine.  The issue only began with Maverick Final.  It's not been a problem for the past two years or so that I've had the 8xxx card in my system.

Cheers,
zenarcher

---

### Post by Amroozy on 2010-12-07
> **ratcheer said:**
> 

2) In Natty, I added the xswat ppa and installed nvidia-current. It installed, successfully, but when I rebooted, it comes up with a desktop background, only. No panels or other controls. Is Natty incompatible with nvidia-current?

Tim
i had the same issue .. installation went fine then after update nvidia driver got only background no panels..
rebooted @ grub menu i chose recovery option and selected "package check" option "sorry i don't remember the full option name.. anyway it made some updates and now it working so fine ...

---

### Post by ronacc on 2010-12-07
> **zenarcher said:**
> No, I haven't tried hand installing the Nvidia driver.  I am trying to avoid that, if I can, since I maintain systems for several non-technical people around where I live and don't want to get into a problem with updates, since a few of them also use Nvidia 8xxx series cards.  I'd rather replace the cards for them, if this is going to be an ongoing issue, which it appears to be.

As for the xorg.conf, I have checked the xorg.conf file in my main system, which is currently running Debian Squeeze and an Nvidia 8xxx card (same one) quite well.  It is identical to the xorg.conf file in the Maverick and Natty installs, where the Nvidia 8xxx is causing a problem.  Very odd, to me.  It had to be some change which took place with Maverick Final Release.  Even with the Maverick RC, everything was fine.  The issue only began with Maverick Final.  It's not been a problem for the past two years or so that I've had the 8xxx card in my system.

Cheers,
zenarcher

I wasn't suggesting that as a solution but as a troubleshooting method , If your card works with the hand installed driver that eliminates both your hardware and the driver itself as the problem and points you at the process jockey ( or whatever ubuntu is using this time around ) uses to install the driver . of course you need to use the same version of the driver that hardware drivers is installing . If it does not work try a different version of the driver , its sure cheaper and easier than a bunch of new cards .

---

### Post by zenarcher on 2010-12-10
> **ronacc said:**
> I wasn't suggesting that as a solution but as a troubleshooting method , If your card works with the hand installed driver that eliminates both your hardware and the driver itself as the problem and points you at the process jockey ( or whatever ubuntu is using this time around ) uses to install the driver . of course you need to use the same version of the driver that hardware drivers is installing . If it does not work try a different version of the driver , its sure cheaper and easier than a bunch of new cards .

Ah, I understand now.  Well, I think I've come up with a solution here.  I ordered new Nvidia cards today, so they should be here at the first of the week and I can replace the Nvidia 8xxx cards which are giving me the problem.  I'll see how that works out.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-12-15
Well, the problem is resolved.  My Nvidia GeForce 210 cards arrived yesterday, so I installed them, removing the Nvidia GeForce 8400 cards, did a fresh install of both Maverick and Natty and now everything is working again as it always did, prior to the Final Release of Maverick, when I lost the monitor immediately following the BIOS splash screen.  

Cheers,
zenarcher

---

### Post by pedja_portugalac on 2011-04-21
Grub problem for me as well after installing Natty (daily alternate image). I have 2 separate disks, sda 320GB and sdb 1000GB. I have my encrypted ubuntu 10.04 LTS on sdb and win7 and Natty 11.04 on sda. After installing Natty I can't boot 10.04 anymore, it's not on the grub list. I was trying to reinstall 10.04s grub from the alternate install CD but it wasn't possible. I can't even mount any of the partitions on sdb except sdb1 (ext2). Any idea or help will be very, very much appreciated.:(

---

### Post by cariboo on 2011-04-21
You need to boot from a Live CD in order to repair grub2.

@pedja_portugalac, it isn't a good idea to add your post to a solved thread as most people will pass it by if it's marked solved.

---

### Post by pedja_portugalac on 2011-04-22
> **cariboo907 said:**
> You need to boot from a Live CD in order to repair grub2.
In the past I have done this even with alternate CD but I'll give it a try. Thank you for the response.
> @pedja_portugalac, it isn't a good idea to add your post to a solved thread as most people will pass it by if it's marked solved.
You're right. :)

---

