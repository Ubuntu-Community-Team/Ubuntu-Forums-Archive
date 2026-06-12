---
title: "Help with Hulu Desktop..."
date: 2010-02-14
forum: Multimedia Software
---

### Post by D3mon_Spawn on 2010-02-14
I am currently running Ubuntu 9.10 x64, and I'm using the third party flash script maintained by the Ubuntu community: [http://ubuntuforums.org/showthread.php?t=1358591]("http://ubuntuforums.org/showthread.php?t=1358591")  I decided one day to install Hulu Desktop since hulu.com hasn't been working for me lately (I think its most likely because of the version of flash I'm using). Anyway, whenever I start Hulu Desktop I get this error message: 

Hulu Desktop could not locate the Flash plugin.

If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so.

I found the libflashplayer.so but I don't know how to modify it. Also I don't seem to even have (or at least i couldn't find) the ~/.huludesktop folder. Any ideas??? :?

---

### Post by Tirish Anau on 2010-04-18
I have same problem and the same Error Message. My specs are
amd64 Phenom 3 with lahf support and i did the lahf workarounds still no go.

---

### Post by pme 72 on 2010-04-18
There is a hidden text file in the Home folder called .huludesktop. You need to go to your Home file and in the View menu enable Show Hidden Files. Scroll down the Home folder to .huludesktop. You need to point to the location of your libflashplayer.so file. This is what mine looks like:

[display]
fullscreen = FALSE
width = 906
height = 725
pos_x = 198
pos_y = 214

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = mceusb
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = OK
button_name_menu = Home

[flash]
flash_location = /usr/lib/mozilla/plugins/libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1

---

