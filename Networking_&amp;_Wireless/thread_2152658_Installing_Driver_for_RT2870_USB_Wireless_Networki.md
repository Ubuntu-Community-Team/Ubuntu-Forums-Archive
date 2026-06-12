---
title: "Installing Driver for RT2870 USB Wireless Networking Device"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by DoomDahDoomDoom on 2013-06-08
I hope these steps will save somebody else the trouble of googling around in case they are having trouble getting a no-name brand USB wireless adaptor to work.  I bought an el-cheapo model from [www.dx.com](www.dx.com) for about $9 with free shipping to Canada.  It's just a USB plug with an antenna on it and it calls itself "EDUP".  Plugging it into my WinXP netbook, it worked right away and used a driver from RaLink called "RT2870".

Anyway, using the steps from this old thread: [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)  does not quite work, because as of a couple versions of Ubuntu ago a couple of functions have changed names.  As per this thread: [http://www.linuxcrew.de/en/blog/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10](http://www.linuxcrew.de/en/blog/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10)

So here's my revised step-by-step based on those two.

1. Downloading the latest drivers [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5021](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5021)
(you have to give them your name and email and then the driver will download)

2. Extract the archive you downloaded.

3. Open a terminal.

4. Go into the folder you extracted (For me 2010_0709_RT2870_Linux_STA_v2.4.0.1)

5. Change directory into os/linux/ (cd os / linux)

6. Open config.mk (with the text editor you like: e.g. gedit)

7. Changing these from

# Support wpa_supplicant
HAS_WPA_SUPPLICANT = n

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = n


to


# Support wpa_supplicant
HAS_WPA_SUPPLICANT = y

# Support for Native WpaSupplicant Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

8. Save and Close.

9. Go to 2010_0709_RT2870_Linux_STA_v2.4.0.1/includes/os

10. Open rt_linux.h with your favorite text editor (e.g. gedit)

11. Changing all occurances of these function calls (two important functions were renamed in the newer versions of Ubuntu):
usb_buffer_alloc  CHANGES TO usb_alloc_coherent
usb_buffer_free  CHANGES TO usb_free_coherent

12. Return to 2010_0709_RT2870_Linux_STA_v2.4.0.1
13. Run the following two commands (wait a minute for the first one to complete before running the second) 
sudo make 
sudo make install
 
14. Visit the os / linux (cd os/linux)
15. And finally, run this command:
sudo insmod rt2870sta.ko

16. Now at this point it should work.  In my case I rebooted a couple of times and tinkered with network interface config files until I realized that the stupid device was actually plugged in backwards... Anyway, then it just worked like it was supposed to.... come to think of it... maybe it I'd plugged it in correctly the first time, maybe it just work have worked out of the box...

---

