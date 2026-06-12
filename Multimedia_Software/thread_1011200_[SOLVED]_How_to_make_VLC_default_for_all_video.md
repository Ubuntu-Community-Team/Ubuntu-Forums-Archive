---
title: "[SOLVED] How to make VLC default for all video"
date: 2008-12-14
forum: Multimedia Software
---

### Post by residualbit on 2008-12-14
Just wondering if there was a way to make VLC the default video player without selecting for each different file type as i get them...

Also, if I change the properties for one .avi to open with vlc, will it affect all future avi files?

---

### Post by mc4man on 2008-12-14
For the left click or double left click on files you'll need to set each file extension once thru it's properties -> open with.

From then on all files with the same ext. will open with what you set.

You also have available the r. click 'open with', you add choices to that menu by contining on to 'open with other application' and picking apps.

All apps you pick (thru repeating the process) will start showing up on the r. click 'open with' menu.

You can also create custom commands to be available in the r. click 'open with.


edit: the right click is a much more useful tool, the left click is a one shot deal

---

### Post by Izek on 2008-12-14
>> Answered Above <<

---

### Post by u-slayer on 2009-10-29
> **mc4man said:**
> For the left click or double left click on files you'll need to set each file extension once thru it's properties -> open with.

From then on all files with the same ext. will open with what you set.

You also have available the r. click 'open with', you add choices to that menu by contining on to 'open with other application' and picking apps.

All apps you pick (thru repeating the process) will start showing up on the r. click 'open with' menu.

You can also create custom commands to be available in the r. click 'open with.


edit: the right click is a much more useful tool, the left click is a one shot deal


There is a much faster way do set this for ALL file types:

```
cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```

---

### Post by x7q on 2009-10-31
> **u-slayer said:**
> There is a much faster way do set this for ALL file types:

```
cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```
That's kind of ugly, don't you think?

User's file associations are stored in ~/.local/share/applications/mimeapps.list

You can make VLC your default player instead of totem for all media files by editing it with a command like this:
```
F=~/.local/share/applications/mimeapps.list 
if [ ! -f $F ]; then echo '[Added Associations]' >$F; fi
grep '=totem.desktop$' /usr/share/applications/defaults.list | sed -e 's/=totem.desktop$/=vlc.desktop;/' >> $F
```

---

