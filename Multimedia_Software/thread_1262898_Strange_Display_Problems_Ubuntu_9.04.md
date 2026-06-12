---
title: "Strange Display Problems Ubuntu 9.04"
date: 2009-09-10
forum: Multimedia Software
---

### Post by grifonas on 2009-09-10
Hi Everyone.
Sorry if it has been discussed somewhere else, but I couldn't find it.

I have a very weird display problem in Ubuntu 9.04 for no apparent reason. Everything was working fine and I didn't make any changes to the driver. After starting the system today me screen looked like this:
[IMG]http://farm3.static.flickr.com/2649/3907226566_27dc7a6cbe.jpg[/IMG]

Tried booting another kernel and 'fixing possible display problems' from the start-up menu, but neither helped. 

Is there a way to fix it or is reinstalling the system the best solution?

Thank you!

---

### Post by ultima on 2009-09-11
Don't reinstall just yet.

A few Ideas

1. Check what updates if any have been made since last boot.

2. Post the contents of your xorg.conf file
```

cat /etc/X11/xorg.conf
```

3. Back up your xorg.conf file and then recreate it. instructions on that should be in the xorg.conf file itself.

Backup
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Remove xorg.conf
```

sudo rm /etc/X11/xorg.conf
```

Then read your xorg.conf file for instuctions on how to recreate it. I forget how and I'm on windows at the moment :)
```

more /etc/X11/xorg.conf | less
```

What video card do you have and what driver are you using?

Worst case, your card could be buggered. :( 

You can check that by running the live cd to see if it still works.

Thats what I'd do anyway :)

---

### Post by grifonas on 2009-09-11
I'm afraid I already reinstalled it. =) Everything works fine now.
Just couldn't wait to start using it again. 

But thanks for the reply. Apparently this problem is not unheard of, so this thread will be useful.

Thanks.

---

### Post by henwyn on 2009-09-12
I upgraded my son's computer to jaunty on Thursday the 10th and all was well and then when he booted up in the morning one day later the screen looked just like the picture at the top of this post. I'll probably reinstall but I'd sure like to know what is causing this. Older computer with AGP ATI video card.

---

### Post by mdbader on 2009-09-14
Same problem here, it was fine when I turned it off.
Even unplugged it from AC.
Next day I got pretty much the same thing.
Live CD works fine, hate to reload, but I may have to.

mike

---

