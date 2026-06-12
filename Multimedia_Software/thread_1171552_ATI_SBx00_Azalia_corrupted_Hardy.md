---
title: "ATI SBx00 Azalia corrupted Hardy"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Jason124 on 2009-05-27
Hello, I have a problem with a Toshiba A215 laptop.

When I installed Hardy, it had sound, however, the mic didn't work. Upon trying to get it working, it seems to have caused everything to stop working.

I've tried reinstalling ALSA to no avail, it just errors out.

Running lspci | grep -i audio results in:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon 2400 PRO]
```

The volume control icon also has a red x on it and says:
"No volume control GStreamer plugins and/or devices found."

---

### Post by markbuntu on 2009-05-27
First do this, it will give you a clean alsa driver

(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

After you reboot edit your /etc/modprobe.d/alsa-base file and add this at the end of the file

options snd_hda_intel model=toshiba

If that does not work you should consider upgrading alsa to a later version. There is directions for that here

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Please let us know how that works out for you.

---

### Post by Jason124 on 2009-05-28
Sweet! That fixed it, thank you so much.

---

