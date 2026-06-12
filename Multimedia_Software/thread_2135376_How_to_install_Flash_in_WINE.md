---
title: "How to install Flash in WINE"
date: 2013-04-14
forum: Multimedia Software
---

### Post by treacl on 2013-04-14
With reference to a couple of recent threads, I am trying to install Flash in Wine so that I can watch Amazon instant video. But every time I try to run the Flash installer, it crashes. Here's what I am doing:

1. Open Firefox in Wine.
2. Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
3. Adobe autodetects my system as "Windows 64-bit , English, Firefox."
4. Uncheck the McAfee Security Scan box.
5. Click Download.
6. install_flashplayer11x32_mssd_aih.exe is saved to ~/Downloads, but does not run automatically.
7. I open ~/Downloads and double-click on the executable.
8. The executable vanishes from the directory listing (!).
9. At this point, top shows install_flashpl as taking up 18% of CPU capacity.
10.  The installer then crashes with an "Unhandled exception: page fault on  write access to 0x334f3800 in 32-bit code (0x02b0a12f)."

OS: Ubuntu 12.04 64-bit (fully updated 2 days ago)
Wine: 1.4-0ubuntu4.1
Windows FF: 20.0.1
Flash: 11.7.700.169

Any suggestions?

---

### Post by treacl on 2013-04-14
Got it working using this link: [http://download.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin.exe](http://download.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin.exe)

---

