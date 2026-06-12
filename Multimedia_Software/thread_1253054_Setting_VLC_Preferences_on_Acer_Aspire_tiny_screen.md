---
title: "Setting VLC Preferences on Acer Aspire tiny screen!!!"
date: 2009-08-29
forum: Multimedia Software
---

### Post by qprfact on 2009-08-29
My son has an Acer Aspire running Ubuntu. Although it has only a small screen, that's not usually a problem.

However, for some reason we've noticed recently that VLC quits unexpectedly when trying to play MPEGs and AVIs. A forum post here ([http://ubuntuforums.org/showthread.php?t=962291](http://ubuntuforums.org/showthread.php?t=962291)) suggests a solution, but when I call up the Preferences window in VLC, I can't get to the bottom of the window to click confirm to my changes!!!

Is there an alternative route I can take, either via terminal or by changing the config file? I see video output in the latter, but nothing I could see defaults which video output it should be (and indeed all the text in the file is hashed out)

Thanks in advance!

---

### Post by mc4man on 2009-08-29
if you can't see the bottom of the preferences window then just press the "Enter" key on keyboard after making change(s), the changes will be saved. Then close and restart vlc to load change(s)

(thinking you are trying to change the video output to X11 video output

Ex. (showing that 'enter' saves changes


> [0x8051140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x80ffd98] main interface debug: looking for interface module: 4 candidates
[0x80ffd98] main interface debug: using interface module "qt4"
[0x80ffd98] main interface debug: TIMER module_need() : 91.875 ms - Total 91.875 ms / 1 intvls (Avg 91.875 ms)
[0x80ffd98] main interface debug: thread started
[0x80ffd98] main interface debug: thread ended
[0x80ffd98] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x80ffd98] qt4 interface debug: Saving the simple preferences [COLOR="Blue"]<- from pressing enter[/COLOR]
[0x80ffd98] main interface debug: opening config file (/home/doug/.config/vlc/vlcrc)


---

### Post by qprfact on 2009-08-29
Blimey, I never knew that!!! Thanks very much!

---

### Post by mc4man on 2009-08-29
If for some reason you bork up the settings and can't see the 'reset preferences' button than this from terminal will set back to default
```
vlc --reset-config
```

or if vlc suddenly misbehaves
```
vlc --reset-plugins-cache
```
or combine the 2 
```
vlc --reset-config --reset-plugins-cache
```

---

### Post by qprfact on 2009-08-30
As ever, very helpful response from this forum, thanks very much!

This may solve an issue - both sons have Acer Aspires running Ubuntu. Both run VLC. Both have copies of the same files to play. On one, they load first time, no issues, on the other, they very often just quit out.

I'll try your suggestion and see what happens!

Thanks again

---

