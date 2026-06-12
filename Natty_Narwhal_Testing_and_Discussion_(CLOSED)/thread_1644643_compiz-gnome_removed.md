---
title: "compiz-gnome removed"
date: 2010-12-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-12-13
surprise,

kde packages are installed instead :o

dont like gnome & kde mixed on a gnome installation :(

---

### Post by cariboo on 2010-12-13
It looks like some dependencies got screwed up. I'm trying the updates on a test system to see what happens. :)

---

### Post by MacUntu on 2010-12-13
This release cycle is way more fun than the ones before. :D

---

### Post by cariboo on 2010-12-13
I just ran the update, and now synaptic has marked all the QT packages as auto-removable.

The update removes Unity, compiz-gnome and ubuntu-desktop.

I'm burning a fresh Natty dvd, just in case. :)

**Update** After a reboot the Ubuntu Desktop comes up with just the background and nothing else. I'd advise using aptitude safe-upograde, or hold off until things get straightened out.

---

### Post by dino99 on 2010-12-13
i've not made the upgrades, wait for more devs comments to know if its the new design or not, seems to me that things might roll back to stay with pure gnome or with some qt packages but not a bunch of kde packages due to cross dependencies.

---

### Post by kyleabaker on 2010-12-13
> **MacUntu said:**
> This release cycle is way more fun than the ones before. :D

Indeed!

> **dino99 said:**
> i've not made the upgrades, wait for more devs comments to know if its the new design or not, seems to me that things might roll back to stay with pure gnome or with some qt packages but not a bunch of kde packages due to cross dependencies.

A few releases back I decided that updating during mid-day EST and at the start of the week are more likely to give me problems, so I tend to hold off until at least mid-week to apply updates and also usually at night. There may be no truth to that at all, but its worked for me (when I can refrain from updates and follow it). :D

---

### Post by Quackers on 2010-12-13
In synaptic I have got compiz which wants to remove compiz-gnome, but a new replacement compiz-gnome is listed for installation which would be ok I think. However compiz also wants to remove unity and there is no replacement for that on offer. I think I may wait too :-)

---

### Post by cariboo on 2010-12-13
I saw on the Natty changes list, that a newer version of Unity is coming, 3.2.6-0ubuntu2

---

### Post by Quackers on 2010-12-13
When it arrives I'll be in like Flynn :-)

---

### Post by godhika on 2010-12-13
Things seemed to be back to normal as of now. No more installing kde stuff and removing compiz unity or anything else

---

### Post by dino99 on 2010-12-13
yeah, patience is the master word when things come strange :P

---

### Post by Borgoz on 2010-12-13
But now unity is gone again...

---

### Post by Quackers on 2010-12-13
When the new Unity arrived in synaptic I ran the updates. I rebooted and although compiz started, unity was missing. I tried to start Unity in the terminal and it crashed something. One REISUB later compiz wasn't running. Another reboot and compiz was running again but no Unity.  So I went to ccsm and found the Unity plugin unchecked again. I checked that and Unity appeared in all its glory :-)
Back up and running :-)

---

### Post by Borgoz on 2010-12-13
> **Borgoz said:**
> But now unity is gone again...

My fault: just a matter of a unity --reset

---

### Post by ronacc on 2010-12-13
all the new packages are installed but compiz still segfaults on me .

---

### Post by Quackers on 2010-12-13
I just noticed wobbly windows had gone so I went to desktop effect in Appearance and it's gone! Vanished!
So I went to ccsm and enabled it - oops, windows borders disappeared, unity disappeared and cairo-dock disappeared.
Hmm so I clicked on the compiz diamond in Applications (from the Ubuntu icon, which fortunately I had already opened) and everything returned! :-) Happy again!

---

### Post by ronacc on 2010-12-13
backing up my /home right now then I'll install todays daily , half my problems may be leftovers from mangy .

---

### Post by garvinrick4 on 2010-12-14
Updates from Dec 14th=Mirror.pnl.gov=has lost unity interface for me. Is it a fix coming
in updates for those that seem to have had same yesterday or was there a fix? Am I
behind on any updates:
```

rick@rick-laptop:~$ sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@rick-laptop:/# aptitude show unity
Package: unity                           
State: installed
Automatically installed: no
Version: 3.2.6-0ubuntu2
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 717 k
Depends: libbamf0 (>= 0.2.60), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib2 (>= 0.3.90), libgcc1 (>=
         1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libgl1-mesa-glx | libgl1,
         libglew1.5 (>= 1.5.2), libglib2.0-0 (>= 2.26.0), libgtk2.0-0 (>=
         2.18.0), libindicator1 (>= 0.3.15), libnux-0.9-0 (>= 0.9.10),
         libnux-0.9-0 (< 0.9.12), libpango1.0-0 (>= 1.14.0), libsigc++-2.0-0c2a
         (>= 2.0.2), libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.5),
         libunity3 (>= 3.2.6), libx11-6, gconf2 (>= 2.28.1-2), unity-common (=
         3.2.6-0ubuntu2), compiz-core, compiz-core-abiversion-20101111,
         libglib2.0-bin, python, nux-tools, unity-asset-pool (>= 0.8.18)
Recommends: unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2)
Breaks: compiz-core (< 1:0.9.2.1+glibmainloop3)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2)
Provides: indicator-renderer, netbook-launcher
Description: Interface for Ubuntu Desktop Edition
 Unity is a graphical interface designed for Ubuntu Desktop Edition
Homepage: https://launchpad.net/unity

root@rick-laptop:/# aptitude show compiz-gnome
Package: compiz-gnome                    
State: installed
Automatically installed: yes
Version: 1:0.9.2.1+glibmainloop3-0ubuntu2
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 561 k
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.2.4),
         libdecoration0 (>= 1:0.9.2.1), libgconf2-4 (>= 2.31.1),
         libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.12.0), libgtk2.0-0
         (>= 2.18.0), libmetacity-private0 (>= 1:2.26.0), libpango1.0-0 (>=
         1.14.0), libwnck22 (>= 1:2.22), libx11-6, libxrender1, gconf2 (>=
         2.28.1-2), compiz-plugins (= 1:0.9.2.1+glibmainloop3-0ubuntu2),
         compizconfig-backend-gconf (>= 0.9.2.1git101213)
Suggests: gnome-themes
Replaces: compiz-plugins (<= 1:0.8.6-0ubuntu12)
Description: OpenGL window and compositing manager - GNOME window decorator
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users with
 special needs. 
 
 This package contains files needed to integrate compiz with the GNOME desktop
 environment.

root@rick-laptop:/# aptitude show ubuntu-desktop
Package: ubuntu-desktop                  
State: installed
Automatically installed: no
Version: 1.209
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 61.4 k
Depends: alacarte, alsa-base, alsa-utils, anacron, baobab, bc, ca-certificates,
         checkbox-gtk, cups, cups-bsd, cups-client, dc, desktop-file-utils,
         doc-base, eog, evince, file-roller, foomatic-db-compressed-ppds,
         foomatic-filters, gcalctool, gconf-editor, gdm, gedit, genisoimage,
         ghostscript-x, gnome-about, gnome-applets, gnome-control-center,
         gnome-icon-theme, gnome-media, gnome-menus, gnome-nettool, gnome-panel,
         gnome-power-manager, gnome-screenshot, gnome-search-tool,
         gnome-session, gnome-session-canberra, gnome-system-log,
         gnome-system-monitor, gnome-terminal, gnome-themes-selected,
         gnome-themes-ubuntu, gstreamer0.10-alsa,
         gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio,
         gtk2-engines, gtk2-engines-pixbuf, gucharmap, indicator-applet-session,
         inputattach, language-selector, launchpad-integration, lftp,
         libgd2-xpm, libpam-ck-connector, libsasl2-modules, libsdl1.2debian,
         libsdl1.2debian-pulseaudio, libxp6, metacity, nautilus,
         nautilus-sendto, notify-osd, openprinting-ppds, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screensaver-default-images,
         seahorse, smbclient, software-center, software-properties-gtk,
         ssh-askpass-gnome, synaptic, system-config-printer-gnome,
         ttf-dejavu-core, ttf-freefont, ubuntu-artwork, ubuntu-extras-keyring,
         ubuntu-sounds, unity, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl,
         xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, branding-ubuntu, brasero, brltty, brltty-x11,
            compiz, computer-janitor-gtk, empathy, espeak, evolution,
            evolution-couchdb, evolution-exchange, evolution-indicator,
            evolution-plugins, evolution-webcal, example-content, firefox,
            firefox-gnome-support, foo2zjs, gbrainy, gcc, gdm-guest-session,
            gnome-accessibility-themes, gnome-bluetooth, gnome-codec-install,
            gnome-disk-utility, gnome-mag, gnome-mahjongg, gnome-orca,
            gnome-screensaver, gnome-sudoku, gnome-user-guide, gnomine,
            gvfs-fuse, hplip, ibus, ibus-gtk, ibus-pinyin,
            ibus-pinyin-db-android, ibus-table, im-switch, indicator-messages,
            jockey-gtk, kerneloops-daemon, laptop-detect, libgail-gnome-module,
            libnss-mdns, libpam-gnome-keyring, libwmf0.2-7-gtk,
            linux-headers-generic, make, min12xxw, mousetweaks, nautilus-share,
            network-manager-gnome, network-manager-pptp,
            network-manager-pptp-gnome, onboard, openoffice.org-calc,
            openoffice.org-gnome, openoffice.org-help-en-us,
            openoffice.org-impress, openoffice.org-math,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            pitivi, plymouth-theme-ubuntu-logo, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox,
            rhythmbox-ubuntuone-music-store, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, tsclient, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei, ubufox,
            ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk, vinagre, vino,
            xcursor-themes, xdg-utils
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

root@rick-laptop:/# aptitude show compiz
Package: compiz                          
State: installed
Automatically installed: no
Version: 1:0.9.2.1+glibmainloop3-0ubuntu2
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 49.2 k
Depends: compiz-core (>= 1:0.9.2.1+glibmainloop3-0ubuntu2), compiz-plugins (>=
         1:0.9.2.1+glibmainloop3-0ubuntu2), compiz-gnome | compiz-kde,
         compiz-fusion-plugins-main (>= 0.9), libcompizconfig0 (>= 0.9)
Suggests: compizconfig-settings-manager
Provides: x-window-manager
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users with
 special needs. 
 
 This metapackage provides the components necessary for running compiz. It
 provides the compiz core, a set of standard plugins, a window decorator using
 the Gtk toolkit and the files necessary to integrate compiz with the GNOME
 desktop environment.

root@rick-laptop:/# aptitude show compizconfig-settings-manager
Package: compizconfig-settings-manager   
State: installed
Automatically installed: no
Version: 0.9.2.1-0ubuntu1
Priority: extra
Section: universe/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,898 k
Depends: python, python-central (>= 0.6.11), python-compizconfig (>= 0.9.0),
         python-gtk2
Description: Compiz configuration settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
 
 This package contains the compizconfig settings manager.

root@rick-laptop:/# 

```

---

### Post by cariboo on 2010-12-14
Did you try logging into the Classic Desktop and running compizconfig-settings-manager (ccsm) and enabling the unity plugin?

---

### Post by garvinrick4 on 2010-12-14
#That was it she is running, thank you Sir.
## What is the sexy-python package? Never mind googled and read about.
```

rick@rick-laptop:/$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Loading icons...
Initializing compiztoolbox options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing detection options...done
Initializing session options...done
Initializing staticswitcher options...done
Initializing regex options...done
Initializing decor options...done
Initializing scale options...done
Initializing opengl options...done
Initializing fade options...done
Initializing snap options...done
Initializing place options...done
Initializing ezoom options...done
Initializing composite options...done
Initializing unityshell options...done
Initializing bailer options...done
Initializing resize options...done
Initializing animation options...done
Initializing vpswitch options...done
Initializing expo options...done
Initializing workarounds options...done
rick@rick-laptop:/$ 

```

---

