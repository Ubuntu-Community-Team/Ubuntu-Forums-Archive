---
title: "Ubuntu Studio Launcher and ZynAddSubFX"
date: 2006-04-22
forum: Multimedia &amp; Video
---

### Post by mGee on 2006-04-22
Ok, I'm trying to follow the QjackCtl Connections tutorial at the ubuntustudio wiki and right away I'm having trouble following it exactly, only because I cannot get ZynAddSubFX to be listed in the launcher. I've tried uninstalling and reinstalling both ZynAddSubFX and Ubuntu Studio Launcher. I've tried manually adding a new menu entry for ZynAddSubFX into the Ubuntu Applications menu and for some reason a desktop configuration file for it is never added to /usr/share/applications.

Of course I know I could launch the apps on their own and continue with the tutorial but I'd like to get ZynAddSubFX listed for future use.

Any idea what's going on? Any idea how I can perhaps alter the script and hardcode ZynAddSubFX into it?

Thanks in advance for any answers :D

---

### Post by dolson on 2006-04-22
Yes, the problem is that the script only looks in the location you mentioned (the PROPER location) for .desktop files. ZynAddSubFX's .desktop file is not put into that location. You can manually copy the file over if you like, or hope that someone in #ubuntu-motu approves my fix that I uploaded to REVU on March 6th.

---

### Post by mGee on 2006-04-23
Ok, thank you... and where is the .desktop file placed?

---

### Post by mGee on 2006-04-23
Well, I found the location of the .desktop file in ~/.local/share/applications/ and copied it to /usr/share/applications/. Yet zynaddsubfxx still doesn't show in the USL.

---

### Post by agapito on 2006-07-22
After moving zynaddsubfx.desktop from ~/.local/share/applications/ to /usr/share/applications add the line Categories=Application;AudioVideo;Audio; to it  so that the .desktop file looks like this:
```
 [Desktop Entry]
Comment=ZynAddSubFX Software Synthesizer
NoDisplay=false
Name=ZynAddSubFX
Exec=/usr/bin/zynaddsubfx
Terminal=false
Hidden=false
Type=Application
Icon=/usr/share/pixmaps/zynaddsubfx.xpm
[COLOR=Red] Categories=Application;AudioVideo;Audio;[/COLOR]
``` Then it will work.  The ubuntustudio script uses a 
```
 for i in `grep -i "^[COLOR=Red]Categories=.*Audio[/COLOR]" $DESKTOPPATH/*.desktop | awk -F: '{ print $1 }' | uniq` ; do
``` loop to identify the audio applications.
Have fun. :)

---

