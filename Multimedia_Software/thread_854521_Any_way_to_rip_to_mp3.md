---
title: "Any way to rip to mp3?"
date: 2008-07-09
forum: Multimedia Software
---

### Post by wbutchart on 2008-07-09
I have been trying to rip to mp3 but nothing seems able to do it.  I have rhythembox which has the option to do it but it when i click to activte it, it still wont allow me to use it.

Is there any programme that will allow me **simply** to rip from a owned cd to mp3?.  This is a important option for someone i have installed ubuntu for too, her daughters put their mp3's on their phones so its important i find a realistically simple programme.

Thanks.

---

### Post by Drunky on 2008-07-09
The mp3 codec is a proprietary format and not shipped by default with Ubuntu.

It is easy to install though, see this webpage: [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats?action=show&redirect=MP3")

Also see [Ripping CD's]("https://help.ubuntu.com/community/CDRipping") further down on the same page.

Regards.

---

### Post by atomkarinca on 2008-07-09
Have you tried Sound Juicer?

---

### Post by wbutchart on 2008-07-09
I have tried sound juicer.  I have the mp3 option _twice_.  In the preference area and the edit audio profiles box i have two mp3 options which are both active.  Yet when i close that and goto the output format i have two options - OGG or FLAC for some reason the programme is completely ignoring the new enabled output options, does anyone know why? and is there anything else that works better?.

---

### Post by gandaran on 2008-07-10
> **wbutchart said:**
> I have tried sound juicer.  I have the mp3 option _twice_.  In the preference area and the edit audio profiles box i have two mp3 options which are both active.  Yet when i close that and goto the output format i have two options - OGG or FLAC for some reason the programme is completely ignoring the new enabled output options, does anyone know why? and is there anything else that works better?.
 

that is strange, I only have one mp3 option, or did you make the second option in edit profile?
check if the **gstreamer0.10-plugins-ugly-multiverse** is installed, this plugin is needed by both rhythmbox and sound-juicer for ripping.

---

### Post by soloman498 on 2008-07-10
Have you tried Audiograbber?

---

