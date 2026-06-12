---
title: "Problem with totem and playing an audio CD"
date: 2008-05-13
forum: Multimedia Software
---

### Post by wakawakawaka on 2008-05-13
My problem is not being able to play a cd with totem in xfce using latest version of ubuntu.  Autoplay is step up, and when I insert a CD totem opens but says that the location is not found.  If i goto the terminal and try to play the cd I get this:

```
$ totem cdda:///dev/scd0

** (totem-gstreamer:10783): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** Message: Error: A Audio CD source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1663): gen_source_element (): /play:
No URI handler for cdda

** Message: Missing plugin: gstreamer|0.10|totem-gstreamer|Audio CD source|urisource-cdda (Audio CD source)
no application found
** Message: No installation candidate for missing plugins found.
** Message: Error: A Audio CD source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1663): gen_source_element (): /play:
No URI handler for cdda

** Message: Missing plugin: gstreamer|0.10|totem-gstreamer|Audio CD source|urisource-cdda (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

```

Info from dmesg :
```
[ 9946.515213] sr0: CDROM (ioctl) error, command: Volume set (in), Read cd be 00 00 00 03 98 00 00 01 f8 00 00
```

I installed sound juicer and the cd plays fine.  Also, in totem the play audio cd selection is greyed out.  Gstreamer seems to be in order, at least i dont know what other packages I would need installed.  Thanks for the help!

---

### Post by cor2y on 2008-05-13
Install all the gstreamer plugins and enable the universe/restriceted repos before installing

---

### Post by wakawakawaka on 2008-05-13
Thanks for the quick reply, however unfortunately your advice did not work.  Looking at gstreamers website it looks like the cdda parts are in the base  and good plugin set which is and was installed.

---

### Post by cor2y on 2008-05-13
If all the correct plugins are installed then its time to look at the other libraries.
Like libcdio7, libcdio-cdda, cd-paranoia, libcdio-paranoia and libcdparanoia.
While i don't use totem to play audio cds.
Rhythmbox is my default audio cd player and it uses gstreamer so if i was missing the necessary libraries my audio cds would not play.

---

