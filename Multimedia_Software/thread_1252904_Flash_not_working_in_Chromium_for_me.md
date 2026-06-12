---
title: "Flash not working in Chromium for me"
date: 2009-08-29
forum: Multimedia Software
---

### Post by snaga on 2009-08-29
I don't seem to be able to get flash to work in chromium. I installed chromium from the chromium-daily repo on launchpad. I'm currently using: 4.0.204.0 (Ubuntu build 24734). Using Jaunty.

I have tried launching with --enable-plugins on the command line, and am currently using /etc/chromium-browser/default , but there is no difference in result.

See the attached screenshot of my about:plugins screen. It looks like chromium is trying to load a Crossover Office version of the flash plugin first. I think I installed Google Chrome on Crossover a few months ago, but un-installed it.

I have tried a couple of times to uninstall and remove all config files, and then re-install. No Joy.

Any thoughts on this? I love Chromium otherwise. FAST.

---

### Post by snaga on 2009-09-01
I think I've managed to solve this. I located the file called dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so , which was located in ~/.cxoffice/winxp/desktopdata/cxnsplugin/linux . I removed it. Chromium will now display flash movies. I think I have probably made it so IE 6 cannot show flash, but thats not important to me!

---

