---
title: "used auto updates, cant play video now!"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by h2z on 2007-11-15
I've booted into gutsy after not using it for approximately 2 weeks (could be less) and the auto updates manager popped telling me there are 40 new updates so I let it do its thing and rebooted after the update (I'm still used to the windows way hehe) but now I just cant seem to play any video files (the program just quits briefly after I press "play") with any of the programs I have (totem, mplayer, vlc). I've tried reinstalling the players with no luck. I have no idea where to look for any update history or how to revert back to the point where everything was working. What do I do now?

EDIT: found a way to show update history;

```

stefan@stefan-linux:~$ ls -tr /var/cache/apt/archives/*.deb
/var/cache/apt/archives/libtar_1.2.11-4_i386.deb
/var/cache/apt/archives/libvcdinfo0_0.7.23-3_i386.deb
/var/cache/apt/archives/libxosd2_2.2.14-1.3_i386.deb
/var/cache/apt/archives/libiso9660-4_0.76-1ubuntu2_i386.deb
/var/cache/apt/archives/libsdl-image1.2_1.2.5-3_i386.deb
/var/cache/apt/archives/compiz-compcomm-plugins-main_0.0.0+git20070612-0ubuntu1_i386.deb
/var/cache/apt/archives/libgnome-compiz-manager0_0.10.3-0ubuntu2_i386.deb
/var/cache/apt/archives/libwxgtk2.6-0_2.6.3.2.1.5ubuntu12_i386.deb
/var/cache/apt/archives/libwxbase2.6-0_2.6.3.2.1.5ubuntu12_i386.deb
/var/cache/apt/archives/python-compizconfig_0.5.2+git20070912-0ubuntu1_i386.deb
/var/cache/apt/archives/compizconfig-settings-manager_0.5.2+git20070912-0ubuntu1_all.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2+git20070928-0ubuntu1_i386.deb
/var/cache/apt/archives/libcompizconfig0_0.5.2+git20070919-0ubuntu3_i386.deb
/var/cache/apt/archives/vlc-nox_0.8.6.release.c-0ubuntu5_i386.deb
/var/cache/apt/archives/vlc_0.8.6.release.c-0ubuntu5_i386.deb
/var/cache/apt/archives/libvlc0_0.8.6.release.c-0ubuntu5_i386.deb
/var/cache/apt/archives/libcompizconfig-backend-gconf_0.5.2+git20071010-0ubuntu1_i386.deb
/var/cache/apt/archives/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gtkhtml3.14_3.16.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libgtksourceview2.0-common_2.0.1-0ubuntu1_all.deb
/var/cache/apt/archives/libgtksourceview2.0-0_2.0.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gcalctool_5.20.2-0ubuntu1_i386.deb
/var/cache/apt/archives/file-roller_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/epiphany-browser_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/eog_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/python-gmenu_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libgnome-menu2_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gnome-menus_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gnome-system-monitor_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libgnomeui-common_2.20.1.1-0ubuntu1_all.deb
/var/cache/apt/archives/libgnomeui-0_2.20.1.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libwnck-common_2.20.1-0ubuntu1_all.deb
/var/cache/apt/archives/libpango1.0-common_1.18.3-0ubuntu1_all.deb
/var/cache/apt/archives/libwnck22_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/evince_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libpango1.0-0_1.18.3-0ubuntu1_i386.deb
/var/cache/apt/archives/sound-juicer_2.20.1-0ubuntu1_i386.deb
/var/cache/apt/archives/libc6-i686_2.6.1-1ubuntu10_i386.deb
/var/cache/apt/archives/libc6-dev_2.6.1-1ubuntu10_i386.deb
/var/cache/apt/archives/libc6_2.6.1-1ubuntu10_i386.deb
/var/cache/apt/archives/python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb
/var/cache/apt/archives/bittorrent_3.4.2-11ubuntu3~7.10_all.deb
/var/cache/apt/archives/libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu11.1_i386.deb
/var/cache/apt/archives/hwdb-client-gnome_0.6.11.1_all.deb
/var/cache/apt/archives/hwdb-client-common_0.6.11.1_all.deb
/var/cache/apt/archives/linux-restricted-modules-common_2.6.22.4-14.10_all.deb
/var/cache/apt/archives/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_i386.deb
/var/cache/apt/archives/libdecoration0_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb
/var/cache/apt/archives/cupsys-common_1.3.2-1ubuntu7.1_all.deb
/var/cache/apt/archives/libcupsys2_1.3.2-1ubuntu7.1_i386.deb
/var/cache/apt/archives/libcupsimage2_1.3.2-1ubuntu7.1_i386.deb
/var/cache/apt/archives/cupsys-client_1.3.2-1ubuntu7.1_i386.deb
/var/cache/apt/archives/cupsys-bsd_1.3.2-1ubuntu7.1_i386.deb
/var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.1_i386.deb
/var/cache/apt/archives/libflac8_1.1.4-3ubuntu1.1_i386.deb
/var/cache/apt/archives/poppler-utils_0.6-0ubuntu2.1_i386.deb
/var/cache/apt/archives/libpoppler2_0.6-0ubuntu2.1_i386.deb
/var/cache/apt/archives/libpoppler-glib2_0.6-0ubuntu2.1_i386.deb

```

EDIT 2: It seem a mere reboot fixed it and all is back to normal (I hope) :)

---

