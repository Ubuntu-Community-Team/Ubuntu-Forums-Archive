---
title: "Cant get flash video to play"
date: 2008-11-24
forum: Multimedia Software
---

### Post by cjohn106 on 2008-11-24
I cannot get flash videos from NBC.com to play. Go to nbc.com and videos and click a show to watch. None of the videos will load for more, but flash video loads in other sites like youtube. Anyone know how to fix this? It plays fine when I run Windows.

---

### Post by cjohn106 on 2008-11-26
Has anyone tried to watch any of these videos?

---

### Post by quazi on 2008-11-26
They don't work.  To watch nbc videos, I use wine, firefox, and adobe.

---

### Post by aysiu on 2008-11-26
> **cjohn106 said:**
> Has anyone tried to watch any of these videos?
Yes, they work fine.

Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? Warning: the first command may take a couple of minutes to execute: ```
sudo updatedb
locate flash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
cat /etc/lsb-release
uname -m
cat /etc/apt/sources.list
```

---

### Post by gandaran on 2008-11-26
are you in USA? I cant play them too! maybe they only load for USA residents

---

### Post by cjohn106 on 2008-11-30
Yeah I am in USA

---

### Post by cjohn106 on 2008-11-30
Yo i ran those commands but they didnt fix the problem. Still cant play.

---

### Post by cjohn106 on 2008-12-02
Anyone else have any ideas? I hate having to switch over to XP. Although it isnt too much trouble.

---

### Post by quazi on 2008-12-05
> **aysiu said:**
> Yes, they work fine.

Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? Warning: the first command may take a couple of minutes to execute: ```
sudo updatedb
locate flash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
cat /etc/lsb-release
uname -m
cat /etc/apt/sources.list
```

Are you sure that you're able to play the full episodes from NBC?  Some clips work under flash with linux, but the full episodes do not (as far as I know).

---

### Post by cjohn106 on 2008-12-06
? I can't play any videos at all from NBC. But I can with XP. That is what I am trying to figure out.

---

### Post by cjohn106 on 2009-01-06
This is what the terminal says when i ran those commands:




corey@corey-laptop:~$ sudo updatedb
[sudo] password for corey: 
corey@corey-laptop:~$ locate flash
/etc/alternatives/firefox-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/midbrowser-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/home/corey/.icons/Aero-stlxv/scalable/apps/flash.png
/home/corey/.icons/Aero-stlxv/scalable/devices/gnome-dev-flashkey.png
/home/corey/.icons/LiNsta-0.3/scalable/apps/flash.png
/home/corey/.icons/LiNsta-0.3/scalable/devices/gnome-dev-flashkey.png
/home/corey/.icons/black-white_2-Gloss/scalable/devices/256/media-flash.png
/home/corey/.icons/black-white_2-Gloss/scalable/mimetypes/application-x-flash-video.png
/home/corey/.icons/black-white_2-Gloss/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.png
/home/corey/.icons/black-white_2-Gloss/scalable/mimetypes/maybe soon/flash (fla).png
/home/corey/.ies4linux/downloads/swflash.cab
/home/corey/.ies4linux/ie6/drive_c/windows/inf/swflash.inf
/home/corey/.ies4linux/ie6/drive_c/windows/profiles/corey/Local Settings/Temporary Internet Files/Content.IE5/0XAJGL2N/flashwrite_1_2[1].js
/home/corey/.ies4linux/tmp/swflash.inf
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/flash.quantserve.com
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/flash.quantserve.com/com.quantserve.sol
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.soapbox.msn.com/flash
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.soapbox.msn.com/flash/soapbox1_1.swf
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.soapbox.msn.com/flash/soapbox1_1.swf/CountryCode.sol
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.video.msn.com/flash
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.video.msn.com/flash/soapbox1_1.swf
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/images.video.msn.com/flash/soapbox1_1.swf/CountryCode.sol
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/www.americafree.tv/flash
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/www.americafree.tv/flash/vplayer.swf
/home/corey/.macromedia/Flash_Player/#SharedObjects/FSZ6D8QM/www.americafree.tv/flash/vplayer.swf/userData_aftv.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/##
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#aka.zero.jibjab.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#as1.suitesmart.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn1.ustream.tv
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#d.yimg.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#dsp.imageg.net
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#images.soapbox.msn.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#images.video.msn.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#include.classistatic.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#interclick.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#it.qoob.tv
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#l.yimg.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#lads.myspace.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#login.yahoo.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.ign.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.mtvnservices.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.scanscout.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#pagead2.googlesyndication.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p1.imeem.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p2.imeem.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#secureinclude.ebaystatic.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#slide.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#void.snocap.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#widget-83.slide.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#wp.vizu.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.adultswim.com](www.adultswim.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.americafree.tv](www.americafree.tv)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.biglots.com](www.biglots.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.bombaysapphire.com](www.bombaysapphire.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.cn.edu](www.cn.edu)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.justin.tv](www.justin.tv)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.mynetworktv.com](www.mynetworktv.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.nbc.com](www.nbc.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.theonion.com](www.theonion.com)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/##/mogulus-system.s3.amazonaws.com
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/##/mogulus-system.s3.amazonaws.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#aka.zero.jibjab.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#as1.suitesmart.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn1.ustream.tv/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#d.yimg.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#dsp.imageg.net/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#images.soapbox.msn.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#images.video.msn.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#include.classistatic.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#interclick.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#it.qoob.tv/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#l.yimg.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#lads.myspace.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#login.yahoo.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.ign.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.mtvnservices.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.scanscout.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#pagead2.googlesyndication.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p1.imeem.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources-p2.imeem.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#secureinclude.ebaystatic.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#slide.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#void.snocap.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#widget-83.slide.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#wp.vizu.com/settings.sol
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.adultswim.com/settings.sol](www.adultswim.com/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.americafree.tv/settings.sol](www.americafree.tv/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.biglots.com/settings.sol](www.biglots.com/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.bombaysapphire.com/settings.sol](www.bombaysapphire.com/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.cn.edu/settings.sol](www.cn.edu/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.justin.tv/settings.sol](www.justin.tv/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.mynetworktv.com/settings.sol](www.mynetworktv.com/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.nbc.com/settings.sol](www.nbc.com/settings.sol)
/home/corey/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.theonion.com/settings.sol](www.theonion.com/settings.sol)
/home/corey/ies4linux-2.0.5/lib/flash.sh
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.24-22-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-22-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-22-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-22-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/usr/bin/btcflash
/usr/lib/adobe-flashplugin
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/app-install/desktop/flash10.desktop
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flash.png
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/adobe-flashplugin
/usr/share/doc/adobe-flashplugin/changelog.Debian.gz
/usr/share/doc/adobe-flashplugin/copyright
/usr/share/games/alien-arena/data1/gfx/flash.tga
/usr/share/games/alien-arena/data1/particles/aflash.tga
/usr/share/games/alien-arena/data1/particles/bflash.tga
/usr/share/games/alien-arena/data1/particles/cflash.tga
/usr/share/games/alien-arena/data1/particles/dflash.tga
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
/usr/src/linux-headers-2.6.24-21/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-21/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-21/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-21/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-21/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-21/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-21/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-21-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-21-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-21-generic/include/config/mtd/scx200/docflash.h
/usr/src/linux-headers-2.6.24-22/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-22/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-22/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-22/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-22/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-22/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-22/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-22-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-22-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-22-generic/include/config/mtd/scx200/docflash.h
/var/cache/apt/archives/adobe-flashplugin_10.0.15.3-1hardy2_i386.deb
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
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.postrm
corey@corey-laptop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok config-files
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Config-Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
corey@corey-laptop:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
corey@corey-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
corey@corey-laptop:~$ uname -m
i686
corey@corey-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) hardy multiverse
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) hardy main
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) hardy main
deb http:ppa.launchpad.net/corenominal/ubuntu gusty main
deb http:ppa.launchpad.net/corenominal/ubuntu gusty main
deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gusty main
deb-src [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gusty main
corey@corey-laptop:~$

---

### Post by wolfen69 on 2009-01-06
> **cjohn106 said:**
> ? I can't play any videos at all from NBC. But I can with XP. That is what I am trying to figure out.

short clips work for me, but not full episodes. oh well.

---

### Post by cjohn106 on 2009-01-06
This is also true for me.

---

### Post by cjohn106 on 2009-02-02
Can anyone get the full episodes from NBC.com to play? is strange that so many people are having the same problem.

---

### Post by Marplot on 2009-03-17
Wow, I've been trying forever to get videos from NBC.com to play with no luck. But guess what? Quazi was correct. Use wine with firefox. Then install the adobe flash player that is suggested by the NBC.com site and your good to go. I'm happily watching my favorite shows now!

---

