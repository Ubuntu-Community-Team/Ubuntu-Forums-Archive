---
title: "Installation help v11.04"
date: 2011-01-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ownagemuffin on 2011-01-01
Hello fellow forum members,

I have been trying to install Ubuntu v11.04 for the PS3, and I am stuck in one of the installation prompt windows. 

Halfway into installing Ubuntu on the PS3, Ubuntu prompts me to configure the package manager by entering a Ubuntu archive mirror hostname and Ubuntu archive mirror directory. There are no selections for both fields, and something has to be entered through typing.

What are the correct responses to enter into the window?
Is is possible to skip this part of the installation process, and if so, will there be any future consequences?

Thanks in Advance
Ownagemuffin

---

### Post by coffeecat on 2011-01-01
I think you're going to have problems installing 11.04 on the PS3. See:

[http://ubuntuforums.org/showthread.php?t=1645294](http://ubuntuforums.org/showthread.php?t=1645294)

By the way, threads about Natty belong here:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by Elfy on 2011-01-01
Moved.

Please do not post threads about development version of ubuntu in main support areas.

---

### Post by Ownagemuffin on 2011-01-01
But the build for it is still on the website!
That means at least installing it for the time being is possible.

---

### Post by Elfy on 2011-01-01
> **Ownagemuffin said:**
> But the build for it is still on the website!
That means at least installing it for the time being is possible.

Where?

Of course it is installable - however it has not been released and is still alpha1. It could break/be unusable at anytime - if you are not comfortable troubleshooting issues then I would suggest you install with one of the released versions.

Whether you'll get it working on a ps3 I have no idea.

---

### Post by ronacc on 2011-01-01
during developement nothing is gaurenteed to be possible except breakage . As sugested by coffeecat read the sticky's on [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394). Ask on that forum , someone may have natty running on a ps3 and be able to guide you .

---

### Post by Ownagemuffin on 2011-01-01
Are there any past PS3 Ubuntu versions that are still supported though? I installed v9.04 before, but it was no longer supported and I can't install anything.

---

### Post by ronacc on 2011-01-01
you might try looking here [http://psubuntu.com/forums/](http://psubuntu.com/forums/) , I seem to remember something about Ubuntu no longer providing support for ps3 installations awhile back , I didn't pay much attention since I don't own one .

---

### Post by Ownagemuffin on 2011-01-02
But do these prompts show up for other versions of Ubuntu?

What does it mean by a Archive mirror hostname and Archive mirror directory?

---

### Post by ronacc on 2011-01-02
no but try this , for archive mirror hostname use ```
 us.archive.ubuntu.com 
```  and for archive mirror directory use ```
 natty 
```

edit you may have to add  /ubuntu   after us.archive.ubuntu.com  but try without it first .

---

### Post by Ownagemuffin on 2011-01-03
It doesn't work :(
Things are already looking bleak, but does anyone else have any other ideas I can try?

---

### Post by Ownagemuffin on 2011-01-03
It didn't work :(
Any other ideas I can try?

Sorry for double post, I did not know there was a page 2 and thought my initial message did not pass through.

---

### Post by zoggnoff on 2011-04-04
> **Ownagemuffin said:**
> It doesn't work :(
Things are already looking bleak, but does anyone else have any other ideas I can try?

i got it to work with this hostname for mirror
```
ports.ubuntu.com
```
leave the subdirectory as is, i.e. /ubuntu-ports/

i did 11.04 on ps3 last night and wrote a thing about it here:
[http://ubuntuforums.org/showthread.php?t=1644073](http://ubuntuforums.org/showthread.php?t=1644073)

---

