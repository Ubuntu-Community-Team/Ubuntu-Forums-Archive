---
title: "Webcam works in Cheese but not Skype"
date: 2009-11-11
forum: Multimedia Software
---

### Post by Jefferythewind on 2009-11-11
Hello everyone, 
  I have a little IBM webcam.  I don't think IBM actually makes webcams so i don't know exactly what kind of cam it is.  I would like to use this webcam on Skype, but it doesn't seem to work.  I can use it on Cheese Webcam Booth no problem but in Skype i just get a screen with multi-colored lines.  Does Anybody know anything that would help me?
  Thanks a lot,

---

### Post by Claus7 on 2009-11-11
Hello,

since I can see that you are using jaunty, this might help you as well:
[http://ubuntuforums.org/showthread.php?t=1178637&highlight=skype](http://ubuntuforums.org/showthread.php?t=1178637&highlight=skype)

Regards!

---

### Post by Jefferythewind on 2009-11-14
Hey Thanks, i haven't tried it yet but it looks like it should work.

---

### Post by Jefferythewind on 2009-11-15
Hi, 
  I just ran that command, and it works great!  I still have the same question that was posted on that other thread; how to have the command already loaded at startup?  I know i could probably put it in the Startup Apps list, but then it would open skype automatically every time also.  Is there somewhere in the Skype code where i would put something in?  

Thanks

---

### Post by idodos on 2009-11-15
Just create a text file with gedit with that command in it.
Make it executable and change the Skype link to use it.

---

### Post by Jefferythewind on 2009-11-16
idodos thanks for the help, got it!

---

### Post by PCZahra on 2011-10-13
How about in Unity? It's still doing it here.

> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

What DOES work is using Skype's "share my screen" feature to share the Cheese window. Go figure.

---

### Post by overdrank on 2011-10-13
Please start a new thread for your issues. No need to revive a sleeping thread. :)

---

