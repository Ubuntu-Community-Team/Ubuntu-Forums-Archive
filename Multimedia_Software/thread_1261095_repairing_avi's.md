---
title: "repairing avi's"
date: 2009-09-08
forum: Multimedia Software
---

### Post by Arminius on 2009-09-08
is there any software for repairing avi's?
some of my avi's seem to have gotten a bit damaged, one player belives that a 30 mins avi is really only 2 mins, and if u try to skip ahead past the point it says it is the video ends.

is there any program that goes deep and restores it as if it were new?

---

### Post by rob-ward on 2009-09-08
You may be able to use mencoder to sort the AVI file out,

you could try a simple command like
mencoder YOURAVI.avi -o newavi.avi

it maybe that the header information in the AVI file is wrong and I thing that mencoder would fix that however I havn't ever run into this problem so I don't know for sure.  I'd just try it and see what happens.

---

### Post by DaithiF on 2009-09-08
in addition to the previous posters suggestion, I would also add the -forceidx option to mencoder which tells it to rebuild the index used for seeking, ie. jumping forward or backward through the video.

---

### Post by Arminius on 2009-09-08
I tried that command, I got back bash: memcoder: command not found

---

### Post by scragar on 2009-09-08
```
apt-get install mencoder
```Install it then.

---

### Post by rob-ward on 2009-09-08
its mencoder not memcoder :-) 

oh and you will have to install mencoder: ```
sudo apt-get install mencoder
```

EDIT: scragar bet me to it :-(

---

### Post by kostkon on 2009-09-08
You can try [*DivFix++*]("http://divfixpp.sourceforge.net/"). If you have 9.04 you can download a deb from the site.

Hope that helps.

---

### Post by Arminius on 2009-09-08
thanks kostkon divfix worked great
but there are a few .mpg's that are bad as well.
anyone know a good .mpg fixer?

---

### Post by mcduck on 2009-09-08
Avidemux can handle many video formats & containers, and might be able to fix the files as well.

Also VLC is pretty capable of playing back broken files, and since it has plenty of CLI tools included it might be useful for fixing the files as well.

---

### Post by Baneblade on 2009-09-08
+1 for VLC

---

### Post by rob-ward on 2009-09-08
VLC will playback the broken file no problem however it won't fix it unless you stream it to another file which will re-encode it completly, I think that mencoder will just repackage it as the command given doesn't tell it to convert the file... I think....

---

### Post by andrew.46 on 2009-09-08
Hi Arminius,

> **Arminius said:**
> anyone know a good .mpg fixer?

If MEncoder is not really your thing FFmpeg will do the job by simply copying both audio and video streams into a new container. For example:

```
ffmpeg -i broken_container.mpg -acodec copy -vcodec copy new_container.mpg
```

All the best,

Andrew

---

