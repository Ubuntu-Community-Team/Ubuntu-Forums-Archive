---
title: "Playing video issues"
date: 2010-12-15
forum: Multimedia Software
---

### Post by Cpierce on 2010-12-15
Running 10.04 with "restricted extras" installed. When I receive an email with a video attached, when I open it, I get a flash of video then just a blank screen. The audio keeps working fine. If I choose the save/download the video, the same thing happens when I open it in my home folder. However if I go to the video file in home folder and choose to open it with VLC, then it works. The video file was WMV format. 
I have uninstalled/re-installed both movie player and restricted extras, but I still have the problem. Does anyone know how to fix this or just make VLC the default ? 

I would sure appreciate some help.

---

### Post by Cpierce on 2010-12-15
I found this, but don't if this is what I should do.

[http://ubuntuforums.org/showthread.php?t=1276575](http://ubuntuforums.org/showthread.php?t=1276575)

should [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop' be ran in terminal ? 


[/FONT][/FONT][/COLOR]

---

### Post by tudor117 on 2010-12-15
Yes, it should be ran in the terminal. What it does is replaces the launcher of the default movie player (totem) with the VLC launcher.
If that's what you want, go for it.
I'd recommend backing up the old one. By the way, run as sudo.
```

sudo cp '/usr/share/applications/totem.desktop' '/usr/share/applications/totem.desktop.bak'
sudo cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'

```
To restore the old movie player (totem) do
```

sudo cp '/usr/share/applications/totem.desktop.bak' '/usr/share/applications/totem.desktop'

```

---

### Post by Cpierce on 2010-12-15
Thank you Tutor117, I will do that if I have to. 

I tried the right click on the file and "open with vlc" and check to remember file type, but that didn't work. Next time I opened the file, Totem opened it again. 

I also went to preferred applications>multimedia and selected "custom" and put "vlc %U" in the command, however that didn't work either. I don't mind totem, just want to be able to run wmv files, and right now VLC seems to work and totem doesn't. 

really appreciate any help

---

### Post by Cpierce on 2010-12-16
I went ahead and ran the above terminal commands to switch vlc with mplayer. I had issues with vlc running in fullscreen, but after going through tools and setting the video output to X11, all is good now. 

Marking this one solved.

---

