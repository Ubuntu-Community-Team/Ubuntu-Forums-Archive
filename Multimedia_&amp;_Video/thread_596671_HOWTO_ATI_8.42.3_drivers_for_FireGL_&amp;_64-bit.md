---
title: "HOWTO: ATI 8.42.3 drivers for FireGL &amp; 64-bit"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by pyrr on 2007-10-29
Looks like I got a bit of a chance here to give a bit back! Usually these forums are so informative I get my questions answered and really don't have much to add.

The following is the most efficient procedure for installing the 8.42.3 (the newest ATI driver that finally supports AIGLX!) on a 64-bit platform with a FireGL chipset. A Thinkpad Z61p to be specific, but it should work for other flavors of this combination. Kudos to all the folks I credited at the end, this is primarily a compilation of several sources who pieced various aspects of this together. All I've done is pulled them together in one place.

 ****

Begin by downloading the new driver from ATI. By way of some rather fundamental basics to reduce confusion or errors, $ is not part of commands, it's the prompt at a user-privileged command line. Additionally, when I start a path out with "~/...", that's starting out in your home directory (also pretty basic)

The first step is to extract it. Open a terminal in your home directory and type:
[highlight]
$ sh ati-driver-installer-8.42.3-x86_64.run --extract
[/highlight]

This creats a folder "fglrx-install.xe6355" (that last string of the folder name apparently varies) to be created.

Download the driver patch from a fellow who goes by Kano on the Phoronix.com forums from [http://xtruder.homelinux.net/~ambro/ati.firegl-8.41.7.patch](http://xtruder.homelinux.net/~ambro/ati.firegl-8.41.7.patch).

Copy the patch file into the fglrx-install directory:
[highlight]
$ patch -p1 < ~/ati.firegl-8.41.7.patch
[/highlight]

Navigate to ~/fglrx-intall.xe6355/common/lib/modules/fglrx/build_mod and create the following softlink:
[highlight]
$ sudo ln -s ~/fglrx-install.xe6635/arch/x86_64/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC4 libfglrx_ip.a.GCC4
[/highlight]

This link appears in the current working directory and allows our "make" command in the next step to find this build library.
[highlight]
$ cd 2.6.x
$ sudo make
[/highlight]

If this build succeeds, there will be a new file created in the ~/fglrx-intall.xe6355/common/lib/modules/fglrx/build_mod/2.6.x directory, "fglrx.ko". Copy this to a convenient location such as your home directory.

Download the new ATI control file from [http://xtruder.homelinux.net/~ambro/control](http://xtruder.homelinux.net/~ambro/control), or if you have the older "official" FireGL driver, find and copy that control file, it apparently also works. Save it in the same convenient location. Both of these files will need to be copied after the new driver is installed for it to work with the FireGL chipset.

This is also a good time to prepare a likely-to-work xorg.conf file. I don't know what this step might be if the system was previously running xserver-xgl. I'd recommend either uninstalling XGL and running Envy or something, or just finding a good generic xorg.conf somewhere. I just took one that had been working for me with the driver Envy installed (and I'd made a few modifications to) and made sure the following values appeared in these particular sections (in addition to other stuff, this is stuff that needs to be added if it's not already there):
 
[highlight]
Section "Module"
  Load "dri"
  Load "v4l"
  Load "dbe"
  Load "glx"
EndSection 

Section "Device"
  Driver "fglrx"
  Option "AIGLX" "true"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection
[/highlight]

Save the new xorg.conf file in the home directory with the other 2 files that will be copied over. As a precaution, save a copy of the current xorg.conf file too, and stash it out of harm's way in a folder you can find easily or rename it to something you'll recognize as the "last known good config" that worked with your current drivers, should something go wrong and you need to reinstall them.

Now, to fix the idiotic ATI driver so it'll build the modules correctly for the 64-bit architecture. Time to download the patch from [http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2](http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2).

Now here comes a step I'm not sure if it's necessary or not, which is re-extracting the ATI driver to a new folder, one from which I built .deb packages packages from. Who knows, it all might actually work to just extract this patch into the existing ~/fglrx-install.xe6635 folder, but I started out on this step, so I had a pure extraction into a new folder that I named "ati": 

NB: I'm uncertain if the softlink and patches created in the previous extraction directory would contaminate this or cause the package building process to fail, or if the patch from that step would contaminate this one. The odds are very good that it would work just fine to use that first fglrx-install extraction, perhaps even better if it created a "fixed" FireGL compatible package. If someone tries that method and is successful, please post!
[highlight]
$ sh ati-driver-installer-8.42.3-x86_64.run --extract ati
[/highlight]

Extract the patch file into "~/ati", it'll replace the things it needs to, and then built the packages. I was already up-to-date on all the other things that are essential for the build, but here's the way to make sure:
[highlight]
$ sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic
[/highlight]

...and when that either installs those modules or confirms they're already installed, it's time to build with
[highlight]
$ sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
[/highlight]

Four new .deb packages should have appeared in the ~/ folder now.

Time to kill-off the existing fglrx drivers and XGL server (if applicable)...
[highlight]
$ sudo apt-get remove xorg-driver-fglrx xserver-xgl
[/highlight]

...and make sure the fglrx driver is blacklisted so it won't attempt to start on reboot:
[highlight]
$ sudo kate /etc/default/linux-restricted-modules-common
[/highlight]

There should be a line in this file that reads:
[highlight]
DISABLED_MODULES="fglrx"
[/highlight]
and if it doesn't, add fglrx between the quotes.

NB: I don't delete any of the older fglrx packages. They might come in handy if there's a problem with the new module, and at worst, they're just sitting around unused and taking up less than 10MB of disk space.

Reboot. The system will not boot into X now, since all the ATI display drivers you'd been running on are completely borked, so don't be surprised. :)

Login to the console.

Now, install the new driver packages (if they're not in your home directory, navigate to the folder they are in).
[highlight]
$ sudo dpkg -i fglrx-kernel-source_8.42.3-1_i386.deb xorg-driver-fglrx_8.42.3-1_i386.deb
[/highlight]

The other two packages aren't needed. The -dev one is probably more developer-oriented, and the "fglrx-amdcccle-..." package is for the Catalyst Control Panel, and at best, it's only middlingly informative, at worst, it'll probably be broken and will create headaches.

Compile kernel module:
[highlight]
$ sudo m-a prepare,update
$ m-a build,install fglrx-kernel
$ sudo depmod
[/highlight]

Now, copy the replacement driver, control, and xorg.conf files to the appropriate directories:
[highlight]
$ sudo cp xorg.conf /etc/X11/xorg.conf
$ sudo cp fglrx.ko /lib/modules
$ sudo cp control /etc/ati
[/highlight]

Now it's a matter of rebooting ("sudo telinit 6", or just "sudo reboot") and hoping it all comes up in a functional state. If not, it'll probably be necessary to rebuild the xorg.conf file, which I seem to recall is something like "sudo dpkg --reconfigure xserver.xorg". What I did if I hit too many problems during this process was to either use Envy (with my LKGC copy of xorg.conf, which I'd send a copy back to the /etc/X11 directory if needed) to reinstall the older ATI drivers that had been working, and research from there. Envy is handy like that.

If X does come up correctly, then Compiz probably needs to be started the following way in a prompt (assuming it's installed along with a control panel):
[highlight]
$ SKIP_CHECKS=yes compiz
[/highlight]

If all's well and you want to run Compiz all the time, then it's a matter of creating startup scripts and such, or just type in that command to start Compiz every time.

I pieced together this mess from the following sources:
ATI AIGLX howto post on the Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=593348](http://ubuntuforums.org/showthread.php?t=593348)
FireGL hack from the Phoronix forums: [http://www.phoronix.com/forums/showthread.php?t=6091](http://www.phoronix.com/forums/showthread.php?t=6091)
64-bit driver repair (linked in one of the Ubuntu forum posts) from a bugtracker: [https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325/comments/8](https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325/comments/8)

And to top that off, most of them cite yet more sources for their fixes. It suffices to say that the ATI 8.42.3 FireGL 64-bit driver is a bit of a disaster. But it's an interesting challenge nonetheless. But for those who want things to "just work" under ATI or nVidia with minimal fuss, there's Envy, at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). This is an easy way to recover from being stuck at a commandline because the display drivers are broken, I've been there, done that, and it's substantially more of a hassle without Envy to do the work.

I of course wasn't aware of all these issues when I started, so my install meandered a bit and had a few false starts where I had to search out more info. Since I took a bit of a roundabout course myself, there may be some things that don't work quite as well as I'm envisioning them in retrospect. Please post corrections or shortcuts.

---

### Post by bmwman91 on 2007-12-10
Thanks for the tutorial.

I followed it all the way through, but wound up formatting & reinstalling.  All of the steps worked and I was able to start Compiz.  However, as soon as I did, the whole screen went solid white.  The mouse cursor would change as it passed over text boxes, indicating that there were some major issues with the drivers drawing to the surfaces, However, Compiz DID start up with NO (crappy) XGL, and no FGLRX installed.

So, I tried my (noob) best to roll everything back to no avail.  After reinstalling, I ran Compiz just fine off of the Mesa drivers included with the fresh install (FireGL T2).  However, Google Earth and most screensavers respond pitifully to this, so I had to reinstall the restricted ATI drivers.

The main importance is that my CAD and other various apps run.  Compiz will be missed for sure.  Do you have any suggestions on how to successfully do this?  I would really love to get this working with my Thinkpad's video card since holding my breath for ATI to release drivers that support Workstation cards seems like a bad idea.  Honestly, what kind of company drops support for all of their workstation cards?  I guess they just want to go after the "easy" money that flows out of the gamer types.  Google searching has left pretty pissed at ATI's corporate attitude.  Amazingly, rather than AMD making them better, they seem to have made AMD worse!  Boo!

---

