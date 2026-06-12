---
title: "How to play VCD for Windows?"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by swamytk on 2007-01-23
Recently I bought a multimedia education VCD for my child. I am not able to play this VCD in my Ubuntu 6.10 (I don't have any other OS in my machine). I browsed the VCD directory, and found that the entire content of the VCD is not more than 10MB. But it has a lot of multimedia content, which was played in Shop's Windows machine. It has an .exe file also in main directory. I don't want to try wine for this, since my system is a bit legacy, it would be slow if load wine. I could not identify the format of VCD. 

Please let me know how to play this kind of *made for windows* VCDs. It has label of "Windows PC/VCD/DVD". My daughter too disappointed because of this. Help please!!

---

### Post by tagra123 on 2007-01-23
Install vlc

Open a terminal:

```
sudo aptitude install vlc gconf-editor
```

To play a vcd

```

vlc vcd://
```


To make it autoplay

```
gconf-editor
```


Cick on desktop 

Click on gnome

Click on volumemanager

On the right look for autoplay_vcd_command

Click on it and change from totem to  /usr/bin/vlc vcd://

You can also add vlc to autoplay dvd's

Change autoplay_dvd_command to /usr/bin/vlc dvd://


You can add the gconf-editor to the menu by right-clicking on the Applications menu and selecting menu editor. Find "Configuration Editor" -- it will be in Applications - System Tools  and enable the menu item.

---

### Post by swamytk on 2007-01-23
Thanks tagra123, But I had tried already all major Media Players like totem, xine, vlc and mplayer. Pl. let me know any other suggestion.

---

