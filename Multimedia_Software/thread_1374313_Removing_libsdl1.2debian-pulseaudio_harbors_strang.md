---
title: "Removing libsdl1.2debian-pulseaudio harbors strange removal dependencies"
date: 2010-01-06
forum: Multimedia Software
---

### Post by Obi-Wan Jerkobi on 2010-01-06
:(

Hello, everyone.

I am using Ubuntu 9.10 karmic with the PAE kernel and have just finished moving from Gnome to KDE. Since I uninstalled Pulseaudio and would like to get back to working with Kdenlive, I am trying to change libsdl1.2debian from pulseaudio to alsa. Whenever I try to install a different libsdl1.2debian or try to remove the pulseaudio version, it harbors strange dependencies to remove! :o It tries to remove most of KDE and some other programs. Here's a list.
> The following packages will be REMOVED:
  acidrip akregator apport-kde apturl-kde ark chromium chromium-bsu divxconverter dolphin ffmpeg gdebi-kde gimp gstreamer0.10-plugins-bad-multiverse gwenview hatari install-package
  jockey-kde k3b kaddressbook kamera kate kcm-gtk kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebluetooth kdegraphics-strigi-plugins kdemultimedia-kio-plugins kdenlive kdepasswd kdepim-groupware kdepim-kresources
  kdepim-runtime kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb kscd ksnapshot ksysguard ksystemlog ktimetracker ktorrent
  kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libcegui-mk2-1 libdevil1c2 libgegl-0.0-0 libk3b6 libkabcommon4 libkcddb4
  libkdepim4 libkleo4 libkonq5 libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksieve4 liblancelot0 libmimelib4 libmjpegtools-1.9 libmlt++2 libmlt1
  libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev libsdl1.2debian libsdl1.2debian-pulseaudio libsmokekde4-2
  libsmpeg-dev libsmpeg0 libxine1 libxine1-x lmms melt mencoder mplayer mplayer-nogui okular okular-extra-backends openoffice.org-kde phonon-backend-xine plasma-dataengines-addons
  plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel
  plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace printer-applet python-kde4
  smc software-properties-kde system-config-printer-kde systemsettings update-manager-kde update-notifier-kde usb-creator-kde userconfig winff zsnes
Is there no way to seamlessly put the libsdl1.2debian-alsa in place of the pulseaudio version without ruining my whole kde install? Is there maybe a different package manager that will be less hectic with dependencies? :(

---

### Post by Obi-Wan Jerkobi on 2010-01-06
Nevermind, I've found the solution.

I did an apt-get update, apt-get clean, and apt-get check as root and then the dependencies were normal. I managed to install libsdl1.2debian-alsa and remove the pulseaudio variant. I then removed whatever was left of the pulseaudio plugins and now my audio works in Totem, Kdenlive, Cheese, etc.! :D

Looks like everything can be solved with a little bit of dabbling in the terminal. :P

---

### Post by tmray on 2010-01-10
I'm having this same problem. Sadly the thing Obi-Wan Jerkobi did to fix it didn't work for me.

Any thoughts?

---

