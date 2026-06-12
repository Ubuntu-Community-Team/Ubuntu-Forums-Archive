---
title: "natty beta root access, dumb question"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ditchdoc7893 on 2011-04-10
Hey guys.  I have a really dumb question.  I'm trying a couple things out on Natty Beta and for some stupid reason I can't figure out how to work from the desktop environment as root.  I tried logging in as root, but it won't let me log in (I've only entered a password for my user logon, "ryan", but when setting up the original install, it did not have me specify a root password).

---

### Post by Enigmapond on 2011-04-10
Try not logging in as root...not good to do that anyway. Open a terminal and do:

```
gksudo nautilus
```

This will give you temporary root access. What are you trying to accomplish? If you need root terminal do:

```
sudo su
```

---

### Post by Ditchdoc7893 on 2011-04-10
I've installed conky, simply because I like its information being right there on the desktop.  I need to edit the conkyrc to get exactly what I want.  I'll try your suggestion and see what happens.  Thanks for the input!  :D

---

### Post by Enigmapond on 2011-04-10
> **Ditchdoc7893 said:**
> I've installed conky, simply because I like its information being right there on the desktop.  I need to edit the conkyrc to get exactly what I want.  I'll try your suggestion and see what happens.  Thanks for the input!  :D

The .conkyrc file should be in your home directory but it's a hidden file and you won't need root access to alter that.

---

### Post by Ditchdoc7893 on 2011-04-10
Ok, I looked for it in my home folder, and as you said, it should be a hidden file.  How do I "un-hide" those files?  I know, dumb, I should know this.  Thanks!!!

---

### Post by Enigmapond on 2011-04-10
Ctrl + h

---

### Post by Ditchdoc7893 on 2011-04-10
Thanks!  I'll give it a shot!

---

### Post by Enigmapond on 2011-04-10
No problem..also the only dumb question here is the one you don't ask.. ):P

Cheers!

---

### Post by Ditchdoc7893 on 2011-04-10
Well unfortunately, there is not a .conkyrc file in my home folder.  I have no idea where it is.

---

### Post by Enigmapond on 2011-04-10
Well you may have to create it then. Check the forum for the Conky Thread to assist you in at least a template that you can play with. If you create an empty file and name it .conkyrc {with the . at the beginning) you just paste your configuration in it and save.

---

### Post by Ditchdoc7893 on 2011-04-10
> **Enigmapond said:**
> Well you may have to create it then. Check the forum for the Conky Thread to assist you in at least a template that you can play with. If you create an empty file and name it .conkyrc {with the . at the beginning) you just paste your configuration in it and save.

Fabulous!  I'll definitely give that a try!  Thanks so much for your help!!  :D

---

### Post by Enigmapond on 2011-04-11
Again...no problem here is the thread to at least get a starter config..

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Cheers!

---

### Post by Elfy on 2011-04-11
move to natty.

[Root access in natty is the same as it is in the other releases.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by SnappyU on 2011-04-12
When prompted with gksudo, if we enter a wrong password, what is the expected behavior?

Should it just close up without any message?

This is happening for me in natty with all the lastest update.

---

### Post by Elfy on 2011-04-12
It's certainly what happened to me in recent releases. No idea if it is normal in natty.

---

### Post by cariboo on 2011-04-12
As far as I know, that's the normal behavior, and has been been for quite some time.

---

