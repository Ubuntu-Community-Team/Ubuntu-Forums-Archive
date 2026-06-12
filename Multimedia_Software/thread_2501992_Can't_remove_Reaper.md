---
title: "Can't remove Reaper"
date: 2024-10-29
forum: Multimedia Software
---

### Post by Dirk_Ouellette on 2024-10-29
sudo apt-get purge reaper
[sudo] password for XXXXXXXXX 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package reaper
 
Well, it's on the system!  Obviously I messed up when installing it.

locate reaper
/home/hapibeli/.config/REAPER/reaper-clap-linux-x86_64.ini
/home/hapibeli/.config/REAPER/reaper-fxtags.ini
/home/hapibeli/.config/REAPER/reaper-install-rev.txt
/home/hapibeli/.config/REAPER/reaper-jsfx.ini
/home/hapibeli/.config/REAPER/reaper-license.rk
/home/hapibeli/.config/REAPER/reaper-midihw-alsa.ini
/home/hapibeli/.config/REAPER/reaper-midihw-linux.ini
/home/hapibeli/.config/REAPER/reaper-mouse.ini
/home/hapibeli/.config/REAPER/reaper-reginfo2.ini
/home/hapibeli/.config/REAPER/reaper-vstplugins64.ini
/home/hapibeli/.config/REAPER/reaper-wndpos.ini
/home/hapibeli/.config/REAPER/reaper.ini
/home/hapibeli/.config/REAPER/Data/toolbar_icons/toolbar_misc_system_reaper.png
/home/hapibeli/.config/REAPER/Data/toolbar_icons/150/toolbar_misc_system_reaper.png
/home/hapibeli/.config/REAPER/Data/toolbar_icons/200/toolbar_misc_system_reaper.png
/home/hapibeli/.local/share/Trash/files/reaper
/home/hapibeli/.local/share/Trash/files/reaper724_linux_x86_64.tar.xz
/home/hapibeli/.local/share/Trash/info/reaper.trashinfo
/home/hapibeli/.local/share/Trash/info/reaper724_linux_x86_64.tar.xz.trashinfo
/home/hapibeli/Desktop/REAPER/reaper
/home/hapibeli/Desktop/REAPER/InstallData/Data/toolbar_icons/toolbar_misc_system_reaper.png
/home/hapibeli/Desktop/REAPER/InstallData/Data/toolbar_icons/150/toolbar_misc_system_reaper.png
/home/hapibeli/Desktop/REAPER/InstallData/Data/toolbar_icons/200/toolbar_misc_system_reaper.png
/home/hapibeli/Desktop/REAPER/Plugins/reaper_cd.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_csurf.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_ddp.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_explorer.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_flac.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_host_x86_64
/home/hapibeli/Desktop/REAPER/Plugins/reaper_midi.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_mp3dec.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_ogg.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_opus.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_python.py
/home/hapibeli/Desktop/REAPER/Plugins/reaper_video.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_wave.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_wavpack.so
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/basic.html
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/click.html
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/fancier.html
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/index.html
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/lyrics.html
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/main.js
/home/hapibeli/Desktop/REAPER/Plugins/reaper_www_root/more_me.html
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-backup.png
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-document.png
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-peak.png
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-template.png
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-template2.png
/home/hapibeli/Desktop/REAPER/Resources/cockos-reaper-theme.png
/home/hapibeli/Downloads/reaper_linux_x86_64
/home/hapibeli/Downloads/reaper_linux_x86_64/install-reaper.sh
/home/hapibeli/Downloads/reaper_linux_x86_64/readme-linux.txt
/usr/lib/evolution-data-server/registry-modules/module-cache-reaper.so
/usr/lib/pd/extra/jmmmp/live2reaper-help.pd
/usr/lib/pd/extra/jmmmp/live2reaper.pd

---

### Post by Bashing-om on 2024-10-29
Dirk_Ouellette; Hello

What release are you on ? As I find no listing in the repo nor a snap on Ubuntu 24.04.

Maybe you installed from a PPA ? As such then apt has no track on the package.

[INDENT]a bit to try and help
[/INDENT]

---

### Post by ajgreeny on 2024-10-29
Almost all those files are in your home so this is certainly not an application installed using normal package management tools.

Let's see the output of commands ```
history | grep -i reaper
which reaper
```

Did you install it running the script spoken about at:-
[https://gist.github.com/wcoastsands/406bd892465a2334f4eff89204149451](https://gist.github.com/wcoastsands/406bd892465a2334f4eff89204149451)

---

