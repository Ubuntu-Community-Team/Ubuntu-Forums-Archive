---
title: "How to install Adobe Flash Player 10 in Ubuntu 8.04?"
date: 2008-11-11
forum: Multimedia Software
---

### Post by csh on 2008-11-11
I'm using Ubuntu 8.04. Currently, I don't want to upgrade.

According to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), Flash Player 10 is available in Ubuntu 8.10 repositories, but not in Ubuntu 8.04 repositories. The flash player in Ubuntu 8.04 repositories is still version 9.

The Flash Player 10 downloaded from adobe.com website does not work.

How can I install Flash Player 10 **WITHOUT** upgrading to Ubuntu 8.10?

---

### Post by gandaran on 2008-11-11
> The Flash Player 10 downloaded from adobe.com website does not work
where did you find this?
every linux package you download from adobe.com works if you know how to handle/install it!
just download the .deb 8.04 package, double click the package and hit install package button, remove any other flash installed first or flash 10 won't work.

---

### Post by zwaardmeester on 2008-11-11
Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and select ".deb for Ubuntu 8.04+" this one _should_ work. 

To make firefox recognize it first uninstall the old flashplugin in Synaptic and (if necessary) under ~/.mozilla/plugins

edit: too late ;)

---

### Post by Bablefish on 2008-11-11
The reason it's not there that Flash 10 is unstable...meaning it's buggy and people have had some problems with it. I would suggest sticking with Flash 9 until the stable version of Flash 10 is finally released.

---

### Post by gandaran on 2008-11-11
> **Bablefish said:**
> The reason it's not there that Flash 10 is unstable...meaning it's buggy and people have had some problems with it. I would suggest sticking with Flash 9 until the stable version of Flash 10 is finally released.
this is not true, flash 10 is stable and a lot better the flash 9, it's just some people have problems with any flash version, I don't know why, maybe the hardware or they install a lot of crap.

---

### Post by m_l17 on 2008-11-11
Flash 10 fixed sound issues I had with 9.

I downloaded and installed the .deb file from adobe.

---

### Post by psyke83 on 2008-11-11
Flash 10 is indeed quite stable, but there are some important updates and configuration changes necessary to make it work correctly. 

If you follow [this]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") guide, you'll get the latest version of Flash (and through necessity, a properly configured PulseAudio server) from my PPA. It won't interfere with later updates or distribution upgrades.

---

### Post by csh on 2008-11-11
Before I install flash player, I upgraded firefox to version 3.03 by using update manager. Then, I installed Adobe Flash 10 again. But still can't get it to work. I can't watch youtube videos and visit flash based website at all.

Any possible solution WITHOUT reinstall ubuntu?

---

### Post by aysiu on 2008-11-11
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove mozilla-plugin-gnash flashplugin-nonfree swfdec-mozilla
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
sudo dpkg -i install_flash_player_10_linux.deb
``` Then restart Firefox.

That should pretty much do it.

---

### Post by csh on 2008-11-12
> **aysiu said:**
> Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove mozilla-plugin-gnash flashplugin-nonfree swfdec-mozilla
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
sudo dpkg -i install_flash_player_10_linux.deb
``` Then restart Firefox.

That should pretty much do it.

Followed your ways. But still not working. why? I upgraded firefox to version 3.03 with update manager.

In /usr/lib directory, I can see 'firefox' folder and 'firefox-3.03' folder.

---

### Post by aysiu on 2008-11-12
Okay, a few things:

1. It has nothing to do with what version of Firefox you have

2. You have to be more specific than "still not working." Did the commands appear to execute correctly? Did you get any error messages? How do you know Flash 10 isn't installed? What happens when you visit a Flash site?

3. How did you install Flash in the first place?

---

### Post by csh on 2008-11-12
> **aysiu said:**
> Okay, a few things:

1. It has nothing to do with what version of Firefox you have

2. You have to be more specific than "still not working." Did the commands appear to execute correctly? Did you get any error messages? How do you know Flash 10 isn't installed? What happens when you visit a Flash site?

3. How did you install Flash in the first place?

So far I didn't see any error message during the installation process. I cannot watch youtube video. Some other flash website told me to install Flash player.

In Firefox preferences -> Application tab, I don't see anything such as 'Shockwave flash....'.

---

### Post by aysiu on 2008-11-12
Can you paste these commands into the terminal and post the output back here? ```
ls -l /usr/bin/firefox
ls -l /opt
ls -l /usr/lib/xulrunner-addons/plugins
sudo updatedb
locate flash
``` The fourth command may take a few minutes to execute, so be patient.

---

### Post by psyke83 on 2008-11-12
Actually, version 10 of the Flash plugin is a lot more fragile than the previous version as it depends on more external libraries. Some users cannot get Flash working if they are using Fabien Tassin's PPA (pre-release Mozilla packages), and 64-bit users cannot use Flash 10 until they have satisfied new dependencies (extra 64-bit libraries, a newer version of nspluginwrapper).

If you follow [this]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") post as I mentioned earlier, most of these problems should get resolved.

Also paste the output of the following command:

```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

N.B. There was a [recent]("http://ubuntuforums.org/showthread.php?t=977001") thread dealing with missing symlinks due to broken packages (though it applied to an Intrepid installation).

---

### Post by csh on 2008-11-12
Here is my output:

ls -l /usr/bin/firefox

```

lrwxrwxrwx 1 root root 11 2008-11-09 18:36 /usr/bin/firefox -> firefox-3.0
```

ls -l /opt

```
total 0
```

ls -l /usr/lib/xulrunner-addons/plugins

```
total 28
lrwxrwxrwx 1 root root    46 2008-11-12 13:08 flashplugin-alternative.so -> /etc/alternatives/xulrunner-addons-flashplugin
-rw-r--r-- 1 root root 15776 2008-09-25 19:31 libnullplugin.so
-rw-r--r-- 1 root root  3944 2008-04-21 23:08 librhythmbox-itms-detection-plugin.so
lrwxrwxrwx 1 root root    44 2008-11-09 18:18 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    45 2008-11-09 18:18 libtotem-basic-plugin.xpt -> ../../totem/default/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    46 2008-11-09 18:18 libtotem-complex-plugin.so -> ../../totem/default/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root    47 2008-11-09 18:18 libtotem-complex-plugin.xpt -> ../../totem/default/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root    43 2008-11-09 18:18 libtotem-cone-plugin.so -> ../../totem/default/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root    44 2008-11-09 18:18 libtotem-cone-plugin.xpt -> ../../totem/default/libtotem-cone-plugin.xpt
lrwxrwxrwx 1 root root    42 2008-11-09 18:18 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    43 2008-11-09 18:18 libtotem-gmp-plugin.xpt -> ../../totem/default/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    44 2008-11-09 18:18 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    45 2008-11-09 18:18 libtotem-mully-plugin.xpt -> ../../totem/default/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    50 2008-11-09 18:18 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    51 2008-11-09 18:18 libtotem-narrowspace-plugin.xpt -> ../../totem/default/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root  7736 2008-09-25 19:31 libunixprintplugin.so
```

sudo updatedb

locate flash

```
/etc/alternatives/firefox-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/midbrowser-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com/settings.sol
/home/cshong/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
/home/cshong/.mozilla/plugins/libflashplayer.so
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/root/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/root/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
/root/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
/usr/bin/btcflash
/usr/lib/adobe-flashplugin
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/adobe-flashplugin
/usr/share/doc/adobe-flashplugin/changelog.Debian.gz
/usr/share/doc/adobe-flashplugin/copyright
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_unmount.png
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-flash-video.xml
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/mimelnk/application/x-shockwave-flash.desktop
/usr/src/linux-headers-2.6.24-16/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-16/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-16/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-16/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-16/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-16/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-16-generic/include/config/mtd/scx200/docflash.h
/var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/alternatives/iceape-flashplugin
/var/lib/dpkg/alternatives/iceweasel-flashplugin
/var/lib/dpkg/alternatives/midbrowser-flashplugin
/var/lib/dpkg/alternatives/mozilla-flashplugin
/var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
/var/lib/dpkg/alternatives/xulrunner-flashplugin
/var/lib/dpkg/info/adobe-flashplugin.list
/var/lib/dpkg/info/adobe-flashplugin.md5sums
/var/lib/dpkg/info/adobe-flashplugin.postinst
/var/lib/dpkg/info/adobe-flashplugin.prerm
```

$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so

```
ldd: /usr/lib/flashplugin-nonfree/libflashplayer.so: No such file or directory
```

---

### Post by psyke83 on 2008-11-12
The path is different as you're using the partner deb:

```
$ ldd /usr/lib/adobe-flashplugin/libflashplayer.so
```

---

### Post by cafemama on 2008-12-05
I am working in a CMS which uses flash to upload photos; unfortunately, it doesn't play with adobe flash player 10 due to the above-mentioned instabilities and I have to uninstall it and install flash 9. naturally, I can't figure out *how* to uninstall it. I'm running ubuntu 8.04 and firefox 3.0.3. if anyone can offer their assitance it would be much appreciated!

---

### Post by csh on 2009-01-09
I already waited for a long time already. Does anyone have solution?

---

### Post by csh on 2009-01-09
Here are the output for ldd /usr/lib/adobe-flashplugin/libflashplayer.so

```
linux-gate.so.1 =>  (0xb7f44000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb73d4000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb73bc000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb72d4000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb72c6000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb7275000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7205000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb71db000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6e64000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb6ddf000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb6dc5000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6dad000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6da4000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb6d67000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6d05000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6cc8000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6cc4000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6cc0000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb6c0f000)
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found
	libplds4.so => not found
	libplc4.so => not found
	libnspr4.so => not found
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6be8000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6bdd000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6a8e000)
	/lib/ld-linux.so.2 (0xb7f45000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6a8c000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6a74000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6a70000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb6a68000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6a50000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6a3b000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6a1a000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6a16000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6a13000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6a0e000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6a06000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6a03000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb69fa000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb69f4000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb69eb000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb69c4000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb69a1000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb6977000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb695e000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6937000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6932000)
```

---

### Post by csh on 2009-01-09
I would like to thank you all for replying to this post. My problem get solved after installing the library file which is "not found" as showed above.

Anyway, thanks all of you very much.

---

