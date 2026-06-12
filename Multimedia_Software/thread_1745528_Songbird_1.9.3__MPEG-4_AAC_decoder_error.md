---
title: "Songbird 1.9.3 : MPEG-4 AAC decoder error"
date: 2011-05-01
forum: Multimedia Software
---

### Post by Crucias on 2011-05-01
I installed all the codecs (Rhythmbox plays the files fine) - GStreamer good, bad and ugly

Tried [this link]("http://ubuntuforums.org/showthread.php?t=954807&page=2") but when i open the SH file it was blank, alright i enter the code, save it and try run it in terminal

```
crucias@Crucias-PC:/usr/share/applications/Songbird$ ls
application.ini  defaults     lib           searchplugins     songbird.sh
bin              extensions   LICENSE.html  songbird          TRADEMARK.txt
blocklist.xml    gst-plugins  plugins       songbird-512.png  updater.ini
chrome           gstreamer    README.txt    songbird-bin      xulrunner
components       jsmodules    scripts       songbird.ini

```

```
sudo gedit songbird.sh
```

I entered this into the blank file and closed it

```
SB_GST_SYSTEM=1 //usr/share/applications/Songbird/songbird
```

then CHMOD'd the file as suggested

```
sudo chmod 755 //usr/share/applications/Songbird/songbird.sh
```

and ran it

```
//usr/share/applications/Songbird/sh songbird.sh
```

and get this

```
 crucias@Crucias-PC:/usr/share/applications/Songbird$ sh songbird.sh
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(songbird-bin:12392): GStreamer-CRITICAL **: gst_debug_add_log_function: assertion `func != NULL' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(songbird-bin:12392): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]

```

Anyone got a clue where to start tracking my bug? When i run this script no codecs load and i cannot even play my normal files. I can play non MPEG4-AAC files without the script.

I am using Natty 11.04 x64 on an intel core2 duo architecture and using the default Unity stuff

---

### Post by Crucias on 2011-05-01
<Defunct Additional Help Request RE Hotkeys>

---

