---
title: "Set VLC as the default DVD player on Kubuntu"
date: 2008-05-10
forum: Multimedia Software
---

### Post by TWO on 2008-05-10
Hi

Does anyone know how to set Kubuntu up so that it uses VLC as the default DVD player?

When I insert a DVD, a window pops ups asking me which action I should take, but even after going through the configure option and selecting VLC, VLC is marked as 'unknown' and on clicking the option, it tells me that it can't open the disc drive.

Yet, if I open VLC and select the disc drive through that, it plays the DVD.

This is happening on Kubuntu Hardy Heron 8.04 with KDE 3.5.9. 

Thanks in advance

TWO

---

### Post by mc4man on 2008-05-10
I've only had kubuntu for a couple of days so i know almost nothing about how it and kde work. While it's pretty simple to add vlc thru notifications (if you want a name just remove unknown and type one in), as you posted it can't play the disk. The problem (in regards to commercial dvds) seems to be vlc is trying to access an unmounted disk which it obviously can't. (hence the error- 'unable to open system:/media/scd0') If the disk was mounted before vlc started it would probably work, the 2 obvious choices being having vlc mount the disk then access it or kde mount it before calling vlc. As far as the latter i know nothing about kde so that's an unknown here. Trying some different commands for vlc was basically fruitless though vlc %m (in autoplay comm. only) did cause the disk to be mounted (first ?) but causes a kioexec error - '/media/cdrom0 is a folder, but a file was expected'. If vlc autoplay is possible maybe someone who knows kubuntu/kde can sort it out for you.

Ot. the whole notifications, file associations thing is very cool, to bad gnome doesn't have something like that. (or if it does not so obscure)

---

### Post by TWO on 2008-05-11
> **mc4man said:**
> 
Ot. the whole notifications, file associations thing is very cool, to bad gnome doesn't have something like that. (or if it does not so obscure)

Yeah, that would have been good for the GNOME version.

Gosh, I thought that by simply inserting the DVD that the disc would be mounted...

---

