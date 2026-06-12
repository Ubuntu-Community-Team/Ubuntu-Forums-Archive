---
title: "Upgraded to 8.04, nvitia drivers not showing"
date: 2008-04-26
forum: Multimedia Software
---

### Post by muso on 2008-04-26
Yesterday I upgraded to 8.04 from Gutsy.  Everything went smoothly, apart from one hiccup - I accidentally pressed cancel to the option to upgrade Samba (I thought it was a popup on another program I was running; I have 2 monitors).  So, when it finished, it said that:

samba-common, smbfs, samba, smbclient, ubuntu-desktop, kubuntu-desktop and smb4k

couldn't be updated (due to dependencies).  It also said that the system might become unstable, so I googled a bit to find a way to update those packages that were missed, and ended up putting:

```
sudo apt-get install -f
sudo dpgk --configure -a
```

Which I think updated Samba.  When I check for updates, however, I get "current dist not found in meta relase".  Anyway, as far as I can tell, everything is working okay - this is just to give some background to where I'm at.

The problem I'm having is:

I have a XFX GeForce FX 5200 Nvidia, and have always had it dual-screen.  Now it's not showing at all.  I have tried installing nvidia-glx and nvidia-glx-new, and nothing seems to register (when I check for proprietary drivers, nothing is in the list).  When I try nvidia-settings, I get "Tou do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server" - when I run the command (using sudo), it does nothing.

I have also tried envyng.  If I try through the GUI version, it eventually returns with "apt API not stable yet".  If I try from the command line (without X running), it seems to run through okay (using:
```

sudo envyng -uninstall-all
sudo envyng -t
>> install nvidia drivers
```

), but there is still no sign of the nvidia drivers.  I seem to recall some error about uvcvideo when shutting down, but didn't get to see it.

Also, whenever I make a change, my screen reverts to 640x480, and my monitor isn't detected correctly, and I have to change it.

I'm running out of ideas to Google, and not sure what else to try.  I am aware that proprietary drivers will need setting up again, but everything I try seems to be even failing to register that nvidia is installed.

I don't really think it's connected to my upgrade experience, but I thought I should add it into this post in case there was something relevant.

Many thanks to anyone who may be able to help!

---

### Post by verysimple on 2008-04-26
I had some issues with nvidia after upgrade to hardy. However, when I boot with the generic kernel, it works fine, so i have edited my /boot/grub/menu.lst to move it up before the 386 one.

---

### Post by muso on 2008-04-27
> **verysimple said:**
> I had some issues with nvidia after upgrade to hardy. However, when I boot with the generic kernel, it works fine, so i have edited my /boot/grub/menu.lst to move it up before the 386 one.

Thanks for that, I may try that out soon...

Hmm... the kernel is worth a thought.  Stupidly I'd changed the grub.lst to only show the latest kernel, so I only have the 386 one in the list (I changed it to 5, but can't remember how to repopulate it).

I'm not sure that using the generic kernel should be the correct way to go - surely it's something they should fix in the 386 version too?

I saw this thread that got the restricted drivers installed:
[http://ubuntuforums.org/showthread.php?t=761476](http://ubuntuforums.org/showthread.php?t=761476)

So now, at least, nvidia shows in the third party drivers window, and I can enable it.  Not sure if it's being used, as if I go in to the screen and display settings I can't select "proprietary", only Nvidia FX (generic).  I notice that the display and screen settings now allow selection of more than one monitor, with options for "clone" and "dual screen".  However, if I test any of them it fails, and I'm not convinced that it's using the real nvidia driver anyway.

Do I really need to use the generic kernel?

---

### Post by Pablo Pablovski on 2008-05-03
> **verysimple said:**
> I had some issues with nvidia after upgrade to hardy. However, when I boot with the generic kernel, it works fine, so i have edited my /boot/grub/menu.lst to move it up before the 386 one.

Yep, that works for me too, with both 2.6.24.15 and .17. Dunno why this step is required, but I get no video if boot with the 386 kernel (although the system boots - I can VNC in from my mac). 

I'm running an AMD3500+, rather than an Intel processor, with an nVidia GTS8800 (640Mb) so maybe it's related to the CPU.

---

### Post by Zorael on 2008-05-03
Non-envy solution would be this.

[list][*]Make sure you're running the kernel you want it to work on, even if it means booting up in recovery mode and doing this in a terminal.
[*]If you have used envy, start it up and pick Uninstall Nvidia Driver to get rid of the changes it made.
```
$ sudo envy -t
```
[*]Then enter these commands. Replace nvidia-glx-new with nvidia-glx-legacy if you have a very old card, etc.
```
$ sudo su
# aptitude **purge** nvidia-glx-new nvidia-settings
# mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
# dpkg-reconfigure xserver-xorg
# aptitude install nvidia-glx-new nvidia-settings
# nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
[*]Reboot, pick same kernel.[/list]

---

### Post by MatthewAPeters on 2008-05-03
Zorael said: "Then enter these commands. Replace nvidia-glx-new with nvidia-glx-legacy if you have a very old card, etc."

Zorael,

Is there a list of what drivers are considered legacy, new, and regular?  The glx package descriptions sounded like they were somewhat backwards compatible, but I didn't see a list of drivers that they supported.

For example - I am having very similar issues using NVIDIA GeForce 6600GT with two 19" panels.  Where would I go to find the correct packages to support my system?

TIA

---

### Post by muso on 2008-05-03
Thanks for the help, I finally got it working.  I didn't change the kernel in the end, but uninstalled all the drivers I had, and ran

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall
```

And after that, I noticed that my driver was finally showing in the restricted hardware section, and that I could enable it.  Then it was just a matter of changing to Twinview, and disabling Xinerama.

One other thing that was odd was that although my main monitor was detected correctly as an ACER AL1714, it kept defaulting to a stupid resolution of 1400 by something.  My monitor can't handle that, so it ended up scrolling.  I had to change it to Generic 1280x1024 to get the resolution to work correctly.

Anyway, it's working now :)

---

### Post by Zorael on 2008-05-03
See [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html). :>

---

