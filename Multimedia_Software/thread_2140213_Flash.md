---
title: "Flash"
date: 2013-04-29
forum: Multimedia Software
---

### Post by rs91 on 2013-04-29
I recently just switched an old dell that was on win xp with sp3 to Lubuntu 13.04 i believe. And go on chrome and then youtube when I pick any video to play and play it the sound is good but the video is all purple and green like a visualization in windows media player or like im on acid haha. Can I still go into the hard drive and check if some windows files are still there that might be causing this? Any ideas or suggestions

---

### Post by Bucky Ball on 2013-04-29
*Thread moved to **Multimedia & Video***

Welcome to the forums. You might have more luck here. 

Sound like you have the flashplugin missing. Doubt Win files will have anything to do with it. If you did a clean install of Ubuntu (formatted the drive to EXT4) there will be no Windows files so would change direction there.

---

### Post by rs91 on 2013-04-29
I'm pretty sure I installed the flash plugin

---

### Post by mmortal03 on 2013-04-29
I'm having the same problem, and also do have the flash plugin installed. My integrated graphics chipset is the Intel 855GM. 

According to the following page, unchecking hardware acceleration in Flash should solve the problem, but it doesn't for me: [https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Adobe-Flash-Player:-wrong-colours-blue-pink-or-purple-or-browser-crash](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Adobe-Flash-Player:-wrong-colours-blue-pink-or-purple-or-browser-crash)

I've thought that the problem is with our graphics chipset drivers not being properly loaded, because they have been blacklisted in more recent versions, but I haven't yet been able to resolve this (if this is, indeed, even the problem).

I created and edited an xorg.conf file to specifically load the proper intel driver, but it doesn't seem to solve this particular issue.

---

### Post by mmortal03 on 2013-04-30
I think I've found the solution. Along with having /etc/X11/xorg.conf reference the Intel driver (see below), you also need to explicitly define the DefaultDepth and Depth values to be either 16 or 24. (24-bit obviously looked better on my machine when looking at the desktop wallpaper. Whether or not it will affect performance is to be determined.)

You probably won't have an xorg.conf file in this recent version of Lubuntu, so create it as a blank file with root privileges if it isn't present, and add the following:

```
[FONT=arial]Section "Screen"
[/FONT][FONT=arial]Identifier "Default Screen"[/FONT]
[FONT=arial]Monitor "Configured Monitor"[/FONT]
[FONT=arial]Device "Configured Video Device"[/FONT]
[FONT=arial]DefaultDepth 24[/FONT]
[FONT=arial]SubSection "Display"[/FONT]
[FONT=arial]Depth 24[/FONT]
[FONT=arial]EndSubSection[/FONT]
[FONT=arial]EndSection[/FONT]

[FONT=arial]Section "Device"[/FONT]
[FONT=arial]Identifier "Configured Video Device"[/FONT]
[FONT=arial]Driver "Intel"[/FONT]
[FONT=arial]EndSection[/FONT]
```

Before rebooting, you'll also need to edit, with root privileges, the following line in /etc/default/grub to match following, or you'll likely get a blank screen on reboot:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```
After editing and saving it, run update-grub afterwards, then reboot.

---

### Post by rob888 on 2013-06-18
> **mmortal03 said:**
> I think I've found the solution. Along with having /etc/X11/xorg.conf reference the Intel driver (see below), you also need to explicitly define the DefaultDepth and Depth values to be either 16 or 24. (24-bit obviously looked better on my machine when looking at the desktop wallpaper. Whether or not it will affect performance is to be determined.)

You probably won't have an xorg.conf file in this recent version of Lubuntu, so create it as a blank file with root privileges if it isn't present, and add the following:

```
[FONT=arial]Section "Screen"
[/FONT][FONT=arial]Identifier "Default Screen"[/FONT]
[FONT=arial]Monitor "Configured Monitor"[/FONT]
[FONT=arial]Device "Configured Video Device"[/FONT]
[FONT=arial]DefaultDepth 24[/FONT]
[FONT=arial]SubSection "Display"[/FONT]
[FONT=arial]Depth 24[/FONT]
[FONT=arial]EndSubSection[/FONT]
[FONT=arial]EndSection[/FONT]

[FONT=arial]Section "Device"[/FONT]
[FONT=arial]Identifier "Configured Video Device"[/FONT]
[FONT=arial]Driver "Intel"[/FONT]
[FONT=arial]EndSection[/FONT]
```

Before rebooting, you'll also need to edit, with root privileges, the following line in /etc/default/grub to match following, or you'll likely get a blank screen on reboot:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```
After editing and saving it, run update-grub afterwards, then reboot.

Great stuff, that seems to have worked here, thanks!

---

### Post by claracc on 2013-06-19
As you got fixed your problem, please, mark the thread as solved:[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by monkeybrain2012 on 2013-06-19
> **claracc said:**
> As you got fixed your problem, please, mark the thread as solved:[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

That wiki doesn't work. You go to Edite > Go advanced as shown but there is no box called "Prefix"

---

### Post by Bucky Ball on 2013-06-19
Apologies. You need to change to Solved on the first thread. Done now. ;)

---

