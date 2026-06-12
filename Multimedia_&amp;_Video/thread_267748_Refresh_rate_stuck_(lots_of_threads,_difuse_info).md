---
title: "Refresh rate stuck (lots of threads, difuse info)"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by marmilho on 2006-09-29
OK. First of all I did search before creating this.
The thing is I could not find anything that worked nor seemed to..

I've been trying to force 1280x1024@70Hz for some time but still only able to set it @60Hz...

What to do?
I've tried editing xorg.conf addin lines and so on but no sucess

Also: I've seem some people suggesting some Step-by-step configurer.. But I do not know how to config it properly(afraid of messing up another things while configuring the refresh)

Thanks in advance.
Best Regards.

PS. Small question, how do I install video/audio Codecs? (New to linux lol)
Or is there any way to install 'windows fonts'(eg. Tahoma)?

---

### Post by ringmaster on 2006-09-29
Have you tried this:

sudo dpkg-reconfigure xserver-xorg

and when it lets you select the resolution select "medium" and select the desired resolution/refresh.

Restart X with Ctrol+Alt+Backspace and that's it!!

---

### Post by marmilho on 2006-09-29
This was the comand I awared about.. It just keep popping questions.. I might mess it up..
no direct way to it?

---

### Post by tseliot on 2006-09-29
> **marmilho said:**
> This was the comand I awared about.. It just keep popping questions.. I might mess it up..
no direct way to it?

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)


BTW you can press ENTER whenever you don't know the question to an answer

---

### Post by marmilho on 2006-09-29
Well I've tried reconfiguring xorg.. messed up a few things. (eg keyboard)
Luckly I was able to undo the changes(it made an automatic backup.

I think i'll have to stick with 1024x768 :/

---

