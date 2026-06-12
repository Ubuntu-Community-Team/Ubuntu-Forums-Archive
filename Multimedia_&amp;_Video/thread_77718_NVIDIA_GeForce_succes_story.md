---
title: "NVIDIA GeForce succes story"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by woopud on 2005-10-17
Just installed the NVIDIA driver succesfully using the following instructions.

How to install Graphics Driver (NVIDIA)?

   1. Read General Notes
   2. Read How to add extra repositories?
   3.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

   4. Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

   5. Save the edited file (sample)
   6. Read How to restart GNOME without rebooting computer?
   7. Applications -> System Tools -> NVIDIA Settings

---

