---
title: "Problem changing default DVD player"
date: 2009-05-05
forum: Multimedia Software
---

### Post by DiscipleRayne on 2009-05-05
First of all I'm on 8.04, for the moment, I'll be updating in the next few weeks.

I popped in a DVD, and totem opened with an error, and instead of trying to fix it, I figured I'd just use VLC, which is my preferred media player anyways. So I followed the instructions in [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) section 4. I popped in a DVD, and VLC opens up, but doesn't play anything. In the lower left corner it displays "file:///media/cdrom0". I have no clue what to do.

---

### Post by mc4man on 2009-05-05
If you followed the instructions in that thread I'd assume you have libdvdcss2 installed.

Try this - right click on Applications -> edit menus. Highlight Sound & Video and on the right side, r. click on vlc -> properties.
If the command is vlc %U change it to 
```
vlc %f
```

Otherwise start vlc from a terminal, try to open a disk and post output

---

### Post by DiscipleRayne on 2009-05-05
I do have that lib installed, and dvds play fine if I open them manually in VLC. There is no Applications -> Edit menus.

---

### Post by mc4man on 2009-05-05
> there is no Applications -> Edit menus.

If you right click on "Applications" in upper panel you don't get a "edit menus" option?

If not, in a terminal go 

```
alacarte
```

---

### Post by DiscipleRayne on 2009-05-05
Oh, never mind, you meant right click on applications. :p It works now, thanks kind sir!

---

