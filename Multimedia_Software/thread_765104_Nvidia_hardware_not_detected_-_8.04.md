---
title: "Nvidia hardware not detected - 8.04"
date: 2008-04-24
forum: Multimedia Software
---

### Post by hollowroom on 2008-04-24
Hello folks. Ok, what a day.

I upgraded from 7.10 to 8.04, and the Nvidia drivers went missing.

Everything else upgraded fine, but every time I install the Nvidia drivers (either via Envy or manually) It asks me to restart the machine.

When I do, they have gone again. (at start up I get the "low graphics, no graphics card detected" spiel)

 If I go into System --> Administration --> Hardware Drivers, the Nvidia drivers are enabled and in use. If I go into Nvidia settings, I get the message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I then do this, but I notice that it makes a slight change to xorg.conf  which then disappears on reboot.

Anybody got any ideas? I have read through a few tips on the forum and tried them all, but it still loses all configuration on reboot and dumps me back to the start.

Frustrating!

---

### Post by macmasterxiv on 2008-04-24
My guess is that the drivers have somehow gotten screwed up by envy and you have leftover files somewhere. The quickest way to check would be to, if you're running nvidia-glx, to install nvidia-glx-new or vice versa. If that fails check the nvidia stuff in /lib/modules/KERNELVERSION/kernel/drivers/video/nvidia/ and possibly delete it, then reinstall the package in synaptic.

---

### Post by silverpig on 2008-04-24
I'm having a similar problem. Nvidia drivers were working beautifully then came the latest upgrade. I rebooted into low graphics mode, and can't get out of it.

sudo modprobe nvidia gives me:
FATAL: Error running install command for nvidia

I have restored an old version of xorg.conf that used to work.

The gnome hardware drivers manager doesn't even have my card listed (7900 GS) as it used to before.

I'm still troubleshooting on my own and will report back with any success.

edit: forgot to mention that my previous drivers were not installed via envy.

---

### Post by hollowroom on 2008-04-24
OK, thanks for the reply, I have tried to install the nvidia drivers a few times, both manually and via Envy - same issue - xorg.conf gets reset on startup (I also get a tty screen running various scripts on startup - is this normal? it didn't used to happen)

I will try what is suggested and report back.

Cheers,

M

---

### Post by silverpig on 2008-04-24
I deleted the stuff in /var/lib/... and it didn't do anything. I uninstalled and reinstalled nvidia-new-glx and nvidia-new-kernel-source. No change.

I installed the drivers from the nvidia site. Now I can see the driver in the gnome driver manager, it is enabled, it is loaded (lsmod | grep nvidia), but glxinfo returns:

[silverpig]:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by silverpig on 2008-04-24
More info:

I just booted into the -12 kernel and it loads up okay (resolution is fine) although now compiz.real takes up 100% cpu and everything is slow unless I run metacity.

---

### Post by hollowroom on 2008-04-24
Well, I reinstalled nvidia-glx-new (after uninstalling it) and the driver is there in the gnome hardware dialogue - ticked and enabled, but the Xserver settings still returns an error, and when I restart I'm back to square one.

xorg.conf is updated now though, it has the correct settings in there (I think) but when I reboot, it doesn't seem to detect the card.

Can someone tell me how to TOTALLY uninstall the Nvidia drivers and then reinstall them, or should I just bite the bullet and reinstall ubuntu?

Must admit, I'm pretty steamed up here.

I had compiz etc working perfectly as I like it before this disaster. :mad:

---

### Post by silverpig on 2008-04-24
> **hollowroom said:**
> Well, I reinstalled nvidia-glx-new (after uninstalling it) and the driver is there in the gnome hardware dialogue - ticked and enabled, but the Xserver settings still returns an error, and when I restart I'm back to square one.

xorg.conf is updated now though, it has the correct settings in there (I think) but when I reboot, it doesn't seem to detect the card.

Can someone tell me how to TOTALLY uninstall the Nvidia drivers and then reinstall them, or should I just bite the bullet and reinstall ubuntu?

Must admit, I'm pretty steamed up here.

I had compiz etc working perfectly as I like it before this disaster. :mad:

I'm in the same boat. I've got the exact same problems.

I just did a full removal of everything nvidia and rebooted. The resolution is fine now and the 2d performance is good, but I have no 3d effects as "nvidia" is not installed at all.

I went to download the cd but the mirrors are getting hammered :P

---

### Post by hollowroom on 2008-04-24
Well, I just about give up.

Thats 6 hours now, about 12 restarts, endless messing around,:mad::mad: and still no Nvidia drivers: the upgrade has been a bit of a disaster for me!

It doesn't matter how often I reinstall / uninstall the Nvidia drivers, something somewhere is broken!

Output from **glxinfo | grep direct**


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by silverpig on 2008-04-24
I just finished downloading the 8.04 cd... I'm gonna reformat my / partition and see if that works. Not very elegant, but whatever.

---

### Post by cor2y on 2008-04-24
No go here either the closed source driver is working in the -12 kernel but the latter ones its not working correctly.
But at least now i have internet access , before i had a HAL failure in the latter kernel updates using beta hardy.

---

### Post by chris062689 on 2008-04-24
Doesn't work over here either.
Apparently it's detected, but when I enable it it says "Oh Go ahead and reboot and your restricted driver will be enabled!" when I rebooted it still showed up as disabled.

---

### Post by silverpig on 2008-04-24
I can confirm that it's a problem with the upgrade process. I just did a fresh install and it works great now. After booting it said the driver was installed and enabled, yet in reality it wasn't. I disabled the driver in gnome hardware drivers manager, then rebooted. I then enabled the driver and my system downloaded it and installed it. I then rebooted again and it worked.

---

### Post by hihihi on 2008-04-25
found solution:

---

### Post by hihihi on 2008-04-25
hello there!

today, i was about to throw the shoe on the upgrade from ubuntu gutsy to hardy,
:: first couldn't install the nvidia-glx-new drivers: dpkg would give 'exit error 2'
;;on every startup the xserver would crash and go into low-res, not recognizing hardware.
([B]SoLUtiON: $sudo dpkg-divert --remove /usr/lib/libGL.so.1
                 $sudo dpkg-divert --remove /usr/lib/libGL.so.1.2
                 $sudo rm /usr/lib/libGL.so.1
                 $sudo rm /usr/lib/libGL.so.1.2[/B])****
::installed nvidia-glx-new drivers
::I copied my backup-file of my good old working xorg.conf back:
                 $sudo cp /<your backup-path>/xorg.conf.backup /etc/X11/xorg.conf
::rebooted
;;now the nvidia-driver was recognized but still no glx:
::glxinfo | grep direct :returned:   Xlib: extension "GLX" missing on display ":0.0".
::StArtEd to mEsS aRroUnd >>>>>

**====SOLUTION======((((EASY))))=============:**

when just a view minutes ago i found the HINT, here: 
[http://forum.compiz-fusion.org/showthread.php?t=7090](http://forum.compiz-fusion.org/showthread.php?t=7090) (thanks)
!! as you can see, this threat is from February 2008, so the mentioned file 'libglx.so.169.09' is named nOw libglx.so.169.12
so i did:
               [B]$ cd /usr/lib/xorg/modules/
               $ sudo ln -s extensions/libglx.so.169.12 libglx.so.169.12[/B]
::reseting the xserver was disappointing, rebooting too, driver recognized, BUT no glx::
>>>sO whAt fiNALly HELPed me to get glx was this:
i created a symlink, which was missing (broken), like this:
             [B]  $ cd /usr/lib/xorg/modules/
               $ sudo ln -s extensions/libglx.so libglx.so[/B]
::reset xserver and:
YYYUUUUPIIIIIEEEEEEEE
IIEEEEEEEEII
WOOWOWOWOWOWOWO
it just works::
jo@jupiter:~$ glxinfo |grep direct
direct rendering: Yes


GOOD LUCK:popcorn:

---

### Post by cotcot on 2008-04-25
I upgraded from 7.10 to 8.04 without problems with the nvidia drivers. I had forced forced an older version with envy to avoid freezes with the newer versions. After upgrade the older version remained installed.

---

### Post by SveinT on 2008-04-25
I have the exact same problem as the others reported here. Things were working perfectly until an update through update manager, now I can only use the open source nv drivers. Hardware manager reports that the drivers are installed and in use, but yet I only get vesa if trying the repo drivers. Manual install works, but only for one session, then it drops back to bulletproof-x screen.

---

### Post by SveinT on 2008-04-25
Got it working.

I am not 100% what fixed it, but I believe it was this:
sudo apt-get install nvidia-kernel-source nvidia-settings

The nvidia-settings is of course optional, but it's nice to have. I think the nvidia-kernal-source will make the driver build it's own kernel module instead of using the provided one (?). I of course installed nvidia-glx-new beforehand.

---

### Post by moktor on 2008-04-25
I upgrade from 7.10 to 8.04 by means of the Update Manager yesterday and since then I had been having this same problem.

I was finally able to get it working for me.

What it seems to have ended up being in my case was the 7.10 kernel was still present on the system and grub's menu.lst also had the system loading the kernel. What I did was remove the 2.6.22-14 kernel via 'sudo apt-get remove linux-image-2.6.22-14-generic'. At that point it also gave me the option of overwriting my current menu.lst with the menu.lst that came with the 2.6.24-16 kernel, which I did.

Then I rebooted and reinstalled the nvidia drivers using Envy.

That's when I was finally able to even see the proprietary driver under the Hardware Drivers screen and check it Enabled. After rebooting again it loaded up perfectly. No kicking me back to the vesa driver, no low-graphics mode.

---

### Post by Grey Box on 2008-04-25
I can confirm that this worked for me also. I have a Dell Inspiron 9300 with a Geforce Go6800 card and did the apt-get upgrade from 7.10 to 8.04. 

The problem with the update was that I specified 'keep existing' when I was asked about Grub settings (I reckon there should be more information provided for these kinds of choices during upgrades, because I'm frequently clueless as to what the expected outcome will be from any of the choices.)

By removing the old kernel and allowing menu.lst in Grub to be overwritten, the problem was quickly solved and I now have a stable system again.

- I recommend to make sure your kernel is the correct one that applies to 8.04
- Thereafter, I used the standard 'Hardware Drivers' option under System->Administration and enabling the NVIDIA restricted driver, then rebooting as instructed. Ubuntu booted with a new splash screen (different progress bar to before) and in 1920x1200 :)
- I hope this helps someone - I kind of noticed the kernel was old and thought 'that's odd.. oh well, but I didn't realize it would break the video driver system.
- I hope the developers will one day make apt upgrade questions more verbose and helpful rather than assuming the user knows the internals of the obscure upgrade choice presented.

---

### Post by Silvanarix on 2008-04-26
I have a Geforce 8800 I have the nv-glx-new installed via synaptic package manager, but i dont see my GFX card in the drivers list, I got rid of the old kernel and its using the 24 now instead of the 22.. Im extremely lost and dont know where to go from here

---

### Post by jKeats3 on 2008-04-27
The only way I was able to get this problem solved was by completely removing the ubuntu restricted modules and installing the NVIDIA driver 169.12 manually.

---

### Post by jwrede on 2008-04-27
> **moktor said:**
> What I did was remove the 2.6.22-14 kernel via 'sudo apt-get remove linux-image-2.6.22-14-generic'. At that point it also gave me the option of overwriting my current menu.lst with the menu.lst that came with the 2.6.24-16 kernel, which I did.
This post lead me to the solution - thanks so much!  I concur that it has to do with 2.6.22-14 kernel components being left after upgrade (as well as a little prompt during the upgrade that 'restricted drivers' would need to be enabled).

Here's my story:
When I tried the 'sudo apt-get remove linux-image-2.6.22-14-generic' command, Ubuntu told me that it wasn't installed.  So I went to Synaptic and took a look at what was - it turns out that the the Linux image for 2.6.22-14-rt was installed, as were the restricted modules.  Interestingly enough, the restricted modules for 2.6.24 were not installed.  So, after marking the 2.6.22 RT image and restricted modules for removal, and marking the 2.6.24 restricted modules for installation, applying and rebooting, my driver appeared and was working correctly.

---

### Post by greenm1981 on 2008-04-27
> **jKeats3 said:**
> The only way I was able to get this problem solved was by completely removing the ubuntu restricted modules and installing the NVIDIA driver 169.12 manually.
Me too.  Once I ran: sudo apt-get install nvidia-kernel-source nvidia-settings and removed all of the restricted nvidia modules in synaptic, I was able to install the proprietary driver successfully.

---

### Post by AlecJ on 2008-04-27
Had no end of problems with my Nvidia 6600 le, from a CD install

But the simple answer, I found, was to
Install 7.10 amd64 and setup everything then do the upgrade online, via "update manager" to Hardy
Works fine and "so far" it's way faster that 7.10.

---

