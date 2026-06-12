---
title: "[INFO] HP 2133 Netbook Wireless"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by slumbergod on 2009-12-17
Just a posting of what I did to fix the Broadcom wireless (BCM4312) on my HP 2133 netbook. I set up a Xubuntu partition and like so many others, discovered that wireless wouldn't work. Without a wired connection on the machine it meant using another and transferring the files by USB flash drive.

After following lots of threads this is the only thing that worked:
Grab the tar file and follow the readme on the webpage. I had no other wireless modules loaded previously so most of the readme did not apply.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

That got me connected. If you use wicd as I do, you might need to install python-urwid *first* then refresh, then insall wicd. There is a strange behaviour in Ubuntu where if you download them together uninstalls network-manager first (while you are still using it!) then complains that python-urwid is missing and you are left with no internet.

The problem is that after each reboot you will need to issue the two commands from the readme again. That is a pain. If you go into Hardware Drivers and search for hardware it'll probably find that the Boradcom STA driver is needed but when you click install, it complains you need to remove the current wireless modules you are using before downloading...why oh why can't it download first *then* install. Another strange behaviour.

I added "lib80211" and "wl" to /etc/modules to make sure they were loaded on boot but there is still the question of the wl.ko module that we made in the broadcom download. To avoid having to manually load it each time or add it to a boot script I wanted to try and force Karmic to grab the correct modules as it was supposed to in the first place.

I updated synaptic then install all the updates that were pending. That gave me the latest kernel too. I rebooted then loaded the wl.ko module manually again.

Once connected I uninstalled these:
# apt-get remove dkms bcmwl-kernel-source

Then I reinstalled them to make sure they loaded correctly. I just installed bcmwl-kernel-source and it grabs the correct dkms for you:
# apt-get install bcmwl-kernel-source

Then I went back to the hardware drivers window and clicked activate. This time it actually worked. Reboot again and wireless is working and connected. 

New issue: the panel size is now incorrect for the default resolution of the netbook - everything is crisp and clear but only some of the screen is visible.




I have to say this:
Shame on the Ubuntu devs for screwing up the wireless drivers so completely! Maybe it is time to rename Ubuntu as Ubuntu Regression 9.10. Seriously, these sort of sloppy mistakes do not inspire much confidence in the linux flagship.

---

### Post by slumbergod on 2009-12-18
Finally, after two days of trying to sort out the problem of the Broadcom wireless driver screwing up the display resolution I did find a fix. Logging out of one user account into another gives the correct resolution too.

The problem is a combination of Grub2 and xorg changes. There is no xorg,conf file created now - the system relies on the autodetection correctly setting everything up. Well, guess what?! It obviously doesn't work on all hardware. The solution is to add the following and reboot.

Create an xorg.conf file:
# nano /etc/X11/xorg.conf

In it, paste the following:

  Section "Device"
      Identifier "Configured Video Device"
      Option "PanelSize" "1024x600"
  EndSection

---

