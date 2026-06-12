---
title: "DRM removal for Linux"
date: 2009-03-11
forum: Multimedia Software
---

### Post by xrayjohn on 2009-03-11
Does anyone know of an application for the Linux OS that will remove DRM from music files? 

Thanks from the Linux newby... If i can get DRM removal working, I can throw away Windows for ever!

---

### Post by lovinglinux on 2009-03-11
Since it looks like you are a newbie here in the forums, I would like to give you a tip.

Try searching google specifying the Ubuntu forums site in the search like this:

```
DRM site:ubuntuforums.org
```

Here is what I got using this search string:

[http://ubuntuforums.org/showthread.php?t=785377](http://ubuntuforums.org/showthread.php?t=785377)

Please keep in mind that removing the DRM from music files could be illegal in your country, even if you purchased them.

BTW, welcome to the freedom world of Linux.

---

### Post by canadiandude007 on 2009-03-11
Do you have specifics as to music files?  Are you talking about m4a or m4p files (presumably ones in iTunes)?

If you install components to play restricted formats, then you will be able to play mp3 files as well as m4a.

Protected music files in iTunes should be burned to a CD then ripped.

However this is likely what you are looking for:

[http://ubuntuforums.org/showthread.php?t=1080099&highlight=m4p+files](http://ubuntuforums.org/showthread.php?t=1080099&highlight=m4p+files)

---

### Post by Simian Man on 2009-03-11
> **canadiandude007 said:**
> 
Protected music files in iTunes should be burned to a CD then ripped.


I did that and the sound quality was crap.  I just deleted all the files I had and started fresh.

---

### Post by kidux on 2009-03-11
Please be careful when asking these kinds of questions, as legality does become an issue. Welcome to the forums and the freedom of Linux, but keep in mind that Linux isn't about bypassing or getting over on "the man", it's about having the right to do what you want with what you own.

---

### Post by canadiandude007 on 2009-03-11
It's probably best to burn protected m4p files to CD, then rip them.

SoundConverter in Gnome or SoundKonverter in KDE work well at ripping and re-sampling songs to different bitrates.

Using something like Amarok (even in Gnome) works well to play all sorts of files whether AAC or mp3, provided restricted formats package has been added.

Highly useful: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by xrayjohn on 2009-03-18
Thanks to all who helped...

---

### Post by Lateefah-ubuntoo on 2010-11-27
How could you remove DRM from a pdf file? There's nothg illegal, I got the files from my university, as well as the password, but calibre coulnd't convert it to the mobi format because of the DRM? How can I solve the problem?

---

### Post by canadiandude007 on 2010-11-28
Try this:

```

gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=unencrypted.pdf -c .setpdfwrite -f encrypted.pdf

```

---

