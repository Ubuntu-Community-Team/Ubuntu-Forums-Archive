---
title: "Automatic screenshots app?"
date: 2009-12-09
forum: Multimedia Software
---

### Post by tripler on 2009-12-09
I'm looking for an application which will automatically take a daily screenshot of a webpage. It's a webcam and I only want to capture the video (not the rest of the webpage). Is there something like that for linux? I'm on ubuntu 9.04.

---

### Post by kaibob on 2009-12-11
I assume you are looking for an application with a GUI. I don't know of one. However, I did something similar with a shell script and cron and thought I might briefly explain.

I first created a shell script that contained the following and placed it in my ~/bin directory:

```
#!/bin/sh

import -window root -display :0 -crop 800x600+25+25 \
   "/home/kaibob/screenshots/$(date +%m.%d.%y_at_%H.%M.%S).png"
```

You have to change the path and the -crop option in the above. The filename of the screenshot is the date and time the screenshot was taken. 

I then edited the crontab file with:

```
EDITOR=gedit && crontab -e
```

I typed in the following line, which consists of the path to and name of the shell script and the minute and hour that the shell script will be run. 

```
15 14 * * * /home/kaibob/bin/ss-daily
```

The numbers 15 14 specify a time of 2:15 p.m. I believe you have to have a newline after pasting in the above. 

The import utility is a part of the Imagemagick package, which is not installed by default. However, it's in the repo's and relatively small.

As mentioned, probably more effort than you were looking for but if not it does work.

---

### Post by tripler on 2009-12-11
that's very interesting, Kaibob. You're taking a screenshot of a web page, are you? Where is that specified?

---

### Post by kaibob on 2009-12-11
> **tripler said:**
> that's very interesting, Kaibob. You're taking a screenshot of a web page, are you? Where is that specified?
I may have misunderstood what you were looking for. My script takes a screenshot of whatever is showing on your computer screen at the specified time. I assumed in your case this was the web page with a web cam image. Perhaps you want to download the web cam image from a web site. If that's correct, then my suggestion will be of no help. I believe that wget may be able to do what you want, but I have little experience with this utility. Perhaps someone else will be able to help.

---

### Post by tripler on 2009-12-11
> **kaibob said:**
> Perhaps you want to download a web page daily and then crop out everything except the web cam image. If that's correct, then my suggestion will be of no help. Sorry!
That is what I want to do. But if I left the web page open your method would take a screenshot of whatever window is open, is that correct?

---

### Post by kaibob on 2009-12-11
> **tripler said:**
> That is what I want to do. But if I left the web page open your method would take a screenshot of whatever window is open, is that correct?
That's correct. It sounds like wget or something similar would be most useful in your case. Have a look at this thread, which sounds closer to what you want. 

[http://ubuntuforums.org/showthread.php?t=1287788](http://ubuntuforums.org/showthread.php?t=1287788)

---

### Post by tripler on 2009-12-11
thanks for the link, Kaibob. Looks like exactly what I'm after. Hope my not very brilliant computer skills are up to it.

---

