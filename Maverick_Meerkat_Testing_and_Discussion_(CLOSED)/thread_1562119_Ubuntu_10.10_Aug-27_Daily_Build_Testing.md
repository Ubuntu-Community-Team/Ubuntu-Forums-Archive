---
title: "Ubuntu 10.10 Aug-27 Daily Build Testing"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by joshruehlig on 2010-08-27
I downloaded and installed the Aug-27 Ubuntu 10.10 Netbook daily build to test things and report bugs. I wanted to put them on launchpad but it gotten late and I wasn't able to figure out exactly how to do it. Here are the bugs so I or someone else can report them soon.

* **LiveCD would not boot, had to change syslinux.cfg file** by removing "ui"
[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

* **Cannot choose to not install bootloader**
*When installing I choose not to install a bootloader so I could just keep my Lucid install's burg.*
     - I clicked not install, next button wasn't clickable
     - I clicked back to my hard drive choices, next became clickable
     - I clicked not install, next stayed clickable
     - I clicked next, after rebooting ubuntu 10.10's grub was installed

* **Rythmbox would crash repeatedly**

* **Could not add apps to unity side bar**
right clicking running application didn't work, dragging icons didn't work (I could just not know the method, but one of these should work)

*** Could not open all the applications I had installed**
ALT+F2 did nothing
There is no terminal or nautilus file browser available under applications, or in a mutter search, (I tried uninstalling and reinstalling and still could not see them)
Nautilus couldn't be opened after I removed it from the unity side bar.

* **Couldn't remove trash from unity side bar**

* [B]eGalax Touchscreen (0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
) was not working properly upon startup[/B]
Same reaction as in Lucid where mouse is jumpy and loves to go to top left corner, this is the fix for Lucid
     - $sudo apt-get install xserver-xorg-input-evtouch
     - $sudo gedit /etc/modprobe.d/blacklist.conf
     - add "blacklist usbtouchscreen" to the end
     - $sudo gedit /usr/lib/X11/xorg.conf.d/11-touchkit.conf
     - paste in config file (check linked thread)
     - change number stightly to fix calibration
[http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877)


Sorry if this was the wrong place to put this, just needed to get this done tonight

---

### Post by donniezazen on 2010-08-27
*Installation is sluggish.
*Ethernet not recognized.
*Nothing is shown in wireless list.
*What to do of hidden networks?

---

