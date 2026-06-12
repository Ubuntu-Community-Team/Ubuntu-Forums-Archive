---
title: "Missing Edit Profiles button in soundjuicer"
date: 2012-11-06
forum: Multimedia Software
---

### Post by oakhilltop on 2012-11-06
The searching I've done shows that soundjuicer should have a button to edit profiles and allow setting the quality of ogg encoding. 

I don't have that button in the version on my system. Is this a bug, or has the application changed?

apt-cache policy sound-juicer
sound-juicer:
  Installed: 3.4.0-3
  Candidate: 3.4.0-3
  Version table:
 *** 3.4.0-3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by Yellow Pasque on 2012-11-07
Gnome3 changed the way it handles audio profiles. See if this command helps:
```
gnome-audio-profiles-properties
```

---

### Post by oakhilltop on 2012-11-08
> **Temüjin said:**
> Gnome3 changed the way it handles audio profiles. See if this command helps:
```
gnome-audio-profiles-properties
```

I don't have that command available.

gnome-calculator             gnome-screensaver-command
gnome-character-map          gnome-screenshot
gnome-contacts               gnome-session
gnome-control-center         gnome-session-cinnamon
gnome-desktop-item-edit      gnome-session-cinnamon2d
gnome-disk-image-mounter     gnome-session-fallback
gnome-disks                  gnome-session-properties
gnome-file-share-properties  gnome-session-quit
gnome-font-viewer            gnome-settings-daemon
gnome-help                   gnome-sound-applet
gnome-keyring                gnome-sound-recorder
gnome-keyring-3              gnome-sudoku
gnome-keyring-daemon         gnome-system-log
gnome-language-selector      gnome-system-monitor
gnome-mahjongg               gnome-terminal
gnome-menus-blacklist        gnome-terminal.wrapper
gnome-nettool                gnome-text-editor
gnome-open                   gnome-thumbnail-font
gnome-panel                  gnome-wm
gnome-power-statistics       gnome-www-browser
gnome-screensaver

---

### Post by Yellow Pasque on 2012-11-09
```
sudo apt-get install gnome-media-profiles
gnome-audio-profiles-properties
```

---

### Post by mc4man on 2012-11-09
```
sudo apt-get install gnome-media-profiles
```
Though I don't think it will matter. It's likely S-J is locked into the Gnome default which is a now a crappy quality of 0.3 for vorbis

I'd use any 3rd party ripper instead or even rhythmbox which can use custom quality settings thru presets (in 12.10, for 12.04 a little setup required for Custom in RB
(the default preset for RB should be 'ubuntu-default' which has a q of 0.6 or you can set a Custom q
See here for a short explain as there is a small no nothing bug
[http://ubuntuforums.org/showpost.php?p=12337687&postcount=3](http://ubuntuforums.org/showpost.php?p=12337687&postcount=3)

---

### Post by Yellow Pasque on 2012-11-10
Doug/mc4man, thanks for pointing that out. I just did a test and you're correct that sound-juicer won't even look at the media profiles anymore. I tried editing the CD, lossy profile to different quality settings and s-j still produced the same file.

Oh well, you can always use s-j to rip to FLAC and then use the oggenc command to convert or you can use a non-gnome ripper that doesn't assume you're too dumb to be playing around with vorbis quality settings. Audex is my favorite in that regard, though if you don't want Qt/KDE stuff on your system, there are others (rubyripper, asunder, ripperx).

---

