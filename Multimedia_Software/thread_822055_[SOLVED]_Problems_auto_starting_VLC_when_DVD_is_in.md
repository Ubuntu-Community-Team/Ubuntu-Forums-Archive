---
title: "[SOLVED] Problems auto starting VLC when DVD is inserted"
date: 2008-06-07
forum: Multimedia Software
---

### Post by User3k on 2008-06-07
I am using Ubuntu 64 and I want to have VLC auto start a DVD movie when I insert a DVD. Actually I want VLC as the default DVD player.

From another thread here I tried the following and nothing worked. Is there another thread or something I am missing?

> 
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc dvd://"



> System|Preferences|Removable Drives and Media|Multimedia
Enter /usr/bin/vlc %d (or browse to your location for vlc command)

> From a terminal:

type

Code:

gconf-editor

Click on the arrow to Expand Desktop

then

Click on the arrow to Expand Gnome

Then click on Volume Manager

Look for autoplay dvd command on th right side of the screen
Double Click

The value should be

totem %M

change it to

/usr/bin/vlc dvd://


same thing for VCD

/usr/bin/vlc vcd://


etc ...


Now when ever a dvd is inserted it will start with VLC

---

### Post by wolfen69 on 2008-06-07
try system>preferences>preferred applications>multimedia and change it to vlc.

---

### Post by User3k on 2008-06-07
I gave that a try. But Totem still pops up rather then VLC.

---

### Post by mc4man on 2008-06-07
Are you using 7.10 (gutsy) or 8.04 (hardy)?

---

### Post by wolfen69 on 2008-06-07
[HERE]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD") is the answer.

---

### Post by User3k on 2008-06-07
Thank you.

---

### Post by User3k on 2008-06-07
Well. I am trying to follow the directions but I can't seem to find the vlc-dvd.desktop file anywhere. I tried to use the commands below as well as looking in that directory itself, after I clicked on view and then show hidden files. Maybe there is something I have to click that shows very, very hidden files? :lolflag:


> cp /usr/share/applications/vlc.desktop /home/yes I changed the name/.local/share/applications/vlc-dvd.desktop


---

### Post by mc4man on 2008-06-07
I'm not too keen on that method of editing mimeapps nor of the command vlc %f
Assuming you haven't done to much of that already  ck here
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by User3k on 2008-06-07
Thank you. That worked perfectly.

---

### Post by mc4man on 2008-06-07
@User3k
It's not mentioned in the link but one word of warning about defaults.list
Any one line can be edited safely _once_ and only with <app>.desktop, don't ever use commands in there or try switching apps back and forth on _one particular line_. Multiple editing of the same line can produce unexpected results

edit: 
Edited the link above with some add. info about kernel upgrades

---

### Post by User3k on 2008-06-08
> **mc4man said:**
> @User3k
It's not mentioned in the link but one word of warning about defaults.list
Any one line can be edited safely _once_ and only with <app>.desktop, don't ever use commands in there or try switching apps back and forth on _one particular line_. Multiple editing of the same line can produce unexpected results

Thanks for the heads up on that.

---

