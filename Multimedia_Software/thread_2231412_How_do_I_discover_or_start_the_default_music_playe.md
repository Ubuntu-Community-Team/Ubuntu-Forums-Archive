---
title: "How do I discover or start the default music player from CLI?"
date: 2014-06-25
forum: Multimedia Software
---

### Post by jcllings on 2014-06-25
Is there a command for this? Assumes I am not targeting a specific file, so xdg-open or gnome-open aren't really cutting it. 

Jim C.

---

### Post by ajgreeny on 2014-06-25
Probably just the command **rhythmbox**, assuming you are using Ubuntu.

---

### Post by Bucky Ball on 2014-06-25
Might help if you tell us what you are trying to launch, but as ajgreeny says, just the name of the app should do it. For VLC, for instance:

vlc

That's it.

---

### Post by arsenic23 on 2014-06-25
> **ajgreeny said:**
> Probably just the command **rhythmbox**, assuming you are using Ubuntu.
> **Bucky Ball said:**
> Might help if you tell us what you are trying to launch, but as ajgreeny says, just the name of the app should do it. For VLC, for instance:
He doesn't want to open anything, just know what will open them.

Here: [https://wiki.archlinux.org/index.php/Default_applications](https://wiki.archlinux.org/index.php/Default_applications)

Scroll down to "Using MIME types and desktop entries".  I **think** you should be able to get the data you need by looking through those files with a simple script.

---

### Post by ajgreeny on 2014-06-25
> **arsenic23 said:**
> He doesn't want to open anything, just know what will open them.

Here: [https://wiki.archlinux.org/index.php/Default_applications](https://wiki.archlinux.org/index.php/Default_applications)

Scroll down to "Using MIME types and desktop entries".  I **think** you should be able to get the data you need by looking through those files with a simple script.
Sorry, but I am not sure I understand what you mean by this.

If you want to know the default application for opening a music file, and don't forget it might be different for each of the the many different music file-types, you can do so by using file-properties from a right click.

However, if it must be by CLI you can see the mime-type default settings for audio files by using ```
cat .local/share/applications/mimeapps.list | grep audio
``` and similarly for other types of file, eg video, etc etc.

---

### Post by mc4man on 2014-06-25
> **ajgreeny said:**
> Sorry, but I am not sure I understand what you mean by this.

If you want to know the default application for opening a music file, and don't forget it might be different for each of the the many different music file-types, you can do so by using file-properties from a right click.

However, if it must be by CLI you can see the mime-type default settings for audio files by using ```
cat .local/share/applications/mimeapps.list | grep audio
``` and similarly for other types of file, eg video, etc etc.
That file doesn't exist until one starts using the context menu. Until then the default music player in Ubuntu/Gnome is either totem or RB based on mime as set in /etc/gnome/defaults.list

---

### Post by ajgreeny on 2014-06-26
Thanks for that info.

So what file query would I use in Xubuntu 12.04 to do the same job if I have not used the context menu?

PS:
I don't actually **need** to know this, but I am just incredibly curious.

---

### Post by mc4man on 2014-06-26
> **ajgreeny said:**
> Thanks for that info.

So what file query would I use in Xubuntu 12.04 to do the same job if I have not used the context menu?

PS:
I don't actually **need** to know this, but I am just incredibly curious.

Don't use xubuntu so don't know how it handles default associations..
It does appear to have desktop-file-utils installed which inc. /etc/gnome/defaults.list
otherwise here are some other packages containing a defaults.list  file
[http://packages.ubuntu.com/search?searchon=contents&keywords=defaults.list&mode=exactfilename&suite=trusty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=defaults.list&mode=exactfilename&suite=trusty&arch=any)

(- in the past & possibly still something like system settings > details > default applications used a single mime for default audio & default video players - 
audio/x-vorbis+ogg=  for audio player
video/x-ogm+ogg= for video player

---

### Post by ajgreeny on 2014-06-26
Thank you.
Xubuntu does indeed have the /etc/gnome/defaults.list file as you suggested and I have used a similar cli query on that file as I suggested in post #5, and it does work, however using the grep query for **audio** files there are so many output lines that it is useless;  to get a meaningful answer you need to query the exact file type in the command, eg mp3, aac, wav etc etc.

---

### Post by tgalati4 on 2014-06-27
Work the problem the other way.  How many music players are installed?

```
apropos music
```

---

