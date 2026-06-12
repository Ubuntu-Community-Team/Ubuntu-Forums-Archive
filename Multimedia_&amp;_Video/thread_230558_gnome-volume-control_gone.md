---
title: "gnome-volume-control gone?"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by nathandh on 2006-08-06
For some reason gnome-volume-control doesn't work anymore. It seems like it's deleted.

```
Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)
```

Is there an easy way to just reinstall it? As it isn't a standalone package.

Nathan

---

### Post by dusu on 2006-08-06
Hi,
gnome-volume-control is part of the package gnome-media.
Could you try to reinstall this ?

---

### Post by nathandh on 2006-08-06
Thanks thats fixed it, for some reason it wasn't even installed at all.

---

### Post by dusu on 2006-08-06
> **nathandh said:**
> Thanks thats fixed it, for some reason it wasn't even installed at all.

Cool :)

---

### Post by Haggis on 2007-10-30
I had the same error message.  I followed your advice and installed gnome-media and now I get the following error:

No volume control GStreamer plugins and/or devices found.

I then used the synaptic program manager to search for gstreamer volume control and only found totem-gstreamer.  I continue to get the same error.  I have tried installing alternative plugins (I am currently using the "good" set), but am currently having no luck.

Where am I going wrong?

Thanks

---

### Post by pcostanza on 2007-10-30
I've got the exact error you have and nothing I've tried to install helps. THe message is not reall clear to me.

---

### Post by pcostanza on 2007-10-30
I fixed my problem by following the info that I found at [http://ubuntuforums.org/showpost.php?p=3640117&postcount=8]("http://ubuntuforums.org/showpost.php?p=3640117&postcount=8")

---

