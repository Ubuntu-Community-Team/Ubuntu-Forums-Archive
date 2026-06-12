---
title: "Automatically scan your HDD for thumbsnails"
date: 2009-03-30
forum: Multimedia Software
---

### Post by ranpha on 2009-03-30
I use gthumb for viewing my pictures. But my directory are so larges it take forever to make he thumbnails so everytime i need a directory i need to wait until gthumb is ready with the generating the thumbs.

I heard that gthumb and nautilus uses the same cache. 
Is there a way where i can prompt a command line (or something else) that can generate thumbnails for a complete HDD ?

---

### Post by Barriehie on 2009-04-07
> **ranpha said:**
> I use gthumb for viewing my pictures. But my directory are so larges it take forever to make he thumbnails so everytime i need a directory i need to wait until gthumb is ready with the generating the thumbs.

I heard that gthumb and nautilus uses the same cache. 
Is there a way where i can prompt a command line (or something else) that can generate thumbnails for a complete HDD ?

How familiar are you with bash and do you have an editor that can run macros???

Barrie

---

### Post by ranpha on 2009-04-08
Euh well bash ..not quite I can put command in a row ..like wget that link then that link etc. And macros ...hehehe no ;-(.. Love to learn it though

---

### Post by Barriehie on 2009-04-08
> **ranpha said:**
> Euh well bash ..not quite I can put command in a row ..like wget that link then that link etc. And macros ...hehehe no ;-(.. Love to learn it though

There are probably some gurus here that can do this with a one liner but I've got this idea...

**find** all .jpg's on the HD and direct the listing, with pathnames, to a file.  Open that file up with let's say emacs and run a macro that uses Imagemagick, either mogrify or convert, to generate the thumbnails in ~/.thumbnails.  You can then use the shell script we'll make to run from /etc/crontab on a daily, weekly, whatever basis to keep ~/.thumbnails updated.

See if this will find all the .jpg's on your HD and then we'll go from there.  Obviously substitute your home dir where mine is listed...  You should have a streaming list of .jpg's in the terminal, with full pathnames.

```

find /home/barrie -name *.jpg -ls 

```Barrie

Edit: I too use gthumb and just noticed that in ~/.Trash is where it's putting the deleted files.  This script will be good to use before backing up!

---

### Post by ranpha on 2009-04-09
Okay that could work. But the find command you use could be different. 
I think find /home/* -name '*.jpg* is enough to get the pathnames. I normally use those command to find *.html files i need to delete.
If you use Imageshack maybe this command can help

find /home/* - name '*.jpg*' -exec Imageshack {} \;

Only i don't know the command for imageshack where it only makes the thumbnail.




PS. For some unknown reason i can't you the code wrapper

---

### Post by Barriehie on 2009-04-09
Just found this link, [http://www.ibm.com/developerworks/library/l-graf/?ca=dnt-428](http://www.ibm.com/developerworks/library/l-graf/?ca=dnt-428)
Now have to get find to put all the .jpg's in the .thumbnail dir.

Barrie

---

### Post by Barriehie on 2009-04-09
Gottit!

This will copy all .jpg's to the ~/.thumbnail directory.
```

find /home/barrie/ -name '*.jpg' -exec cp {} /home/barrie/.thumbnails/ \;
```Next is using Imagemagick to convert to thumbnails.  Getting closer to a one liner... :)

Barrie

---

### Post by ranpha on 2009-04-09
> **Barriehie said:**
> Gottit!

This will copy all .jpg's to the ~/.thumbnail directory.
```

find /home/barrie/ -name '*.jpg' -exec cp {} /home/barrie/.thumbnails/ \;
```Next is using Imagemagick to convert to thumbnails.  Getting closer to a one liner... :)

Barrie

Euh barrie ....i count over 2tb on images .... not a smart idea to copy all the jpg to the thumbnails then convert them.Besides if the thumbnails arn't made with a  hash code which tells where the thumb needs to appear when you browse though the directory. I still think you need to let gthumb ( or another thumbnailer) scan a complete directory tree. Fore xample that "Thumbs 7.0 " but that's windows and uses access databases (you can expand to a mysql database) but i want something simpel like the gnome approach just put thumbnails in a thumbnails directory

---

### Post by Barriehie on 2009-04-09
> **ranpha said:**
> Euh barrie ....i count over 2tb on images .... not a smart idea to copy all the jpg to the thumbnails then convert them.Besides if the thumbnails arn't made with a  hash code which tells where the thumb needs to appear when you browse though the directory. I still think you need to let gthumb ( or another thumbnailer) scan a complete directory tree. Fore xample that "Thumbs 7.0 " but that's windows and uses access databases (you can expand to a mysql database) but i want something simpel like the gnome approach just put thumbnails in a thumbnails directory

Hey, still playing with find!  I found this [link]("http://jens.triq.net/thumbnail-spec/index.html") and will check it out to see what needs to happen where.

Barrie

Edit:  Okay, according to the thumbnail-spec this task is beyond my bash skills.  I can only see a way to do it with a shell script that incorporates some python.

---

