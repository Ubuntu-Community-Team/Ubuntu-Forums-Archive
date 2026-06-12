---
title: "Copying files using terminal"
date: 2008-06-12
forum: Mac OSX
---

### Post by aheckler on 2008-06-12
Question for a friend:
> I have a computer that has been heavily used by many people for photo and video editing and so forth. But now I am getting a new one, so I need to back up all these photos, videos, etc. The problem is that the files are scattered all throughout the drive, making it impractical to hunt them down by hand and copy them over. What would be the best way to approach this using the terminal?

Basically what I want to do is specify filetypes, have OS X find every single file of that type on the system, then copy it over to an external drive. Space is not an issue here, so I don't care if there are ten, twenty, or even a hundred "false positive" images copied.

I'm thinking the best way to do this would be using "find" or "locate", but I'm not familiar enough with OS X to be sure of this.

Something like this for .jpg files maybe?

```
find / -name "*.jpg" -exec cp {} /path/to/backup
```

And then just repeat that for every filetype?

---

### Post by aysiu on 2008-06-12
Can't you through the GUI do a find for all files in /Users and then copy those over through drag and drop?

---

### Post by aheckler on 2008-06-12
I don't know, I'm not an OS X user. My buddy just mentioned this problem to me off-hand the other day.

---

### Post by issih on 2008-06-12
terminal way would as you suggested probably be through something like find, but I'm not in osx right now so I can't check. Alternatively you can suggest he uses a smart folder. Just right click and create a new smart folder, then set it up to search for images.

I once had one of these to show me any images from the last week. If he just does that and makes the timeframe forever, he can then just select everything in that folder and copy it over to his backup location. Nice, simple, easy, very maccy :)

---

### Post by handy on 2008-06-14
The following link may be useful to someone:

***_[http://www.ss64.com/osx/index.html](http://www.ss64.com/osx/index.html)_***

---

