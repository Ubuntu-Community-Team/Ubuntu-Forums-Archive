---
title: "Video issues"
date: 2013-10-29
forum: Multimedia Software
---

### Post by DenyingProduct on 2013-10-29
My amd laptop is at it again. black screen no boot. i installed teamviewer then boom it stopped working. I can get to terminal using ctrl alt f4 thing but the video will not open.

By the video wont open i mean the graphical interface. i get greeted with a blinking command line and nothing until i press the ctrl alt f4
 
I attempted to remove the proprietary amd drivers using 
```
amdconfig --uninstall
``` 
and erased the xorg.config file but still nothing. 
I have also uninstalled team viewer using 
```
sudo apt-get remove teamviewer
``` 
I cant get it to work please advise.

Here is a tread i opened not to long ago with a similar problem [http://ubuntuforums.org/showthread.php?t=2182060](http://ubuntuforums.org/showthread.php?t=2182060)

---

### Post by DenyingProduct on 2013-10-30
bump anyone I need my laptop

---

### Post by Bucky Ball on 2013-10-30
I know it's frustrating but please wait 24 hours before bumping. If no-one has responded yet, no one has a clue for the moment. 

It helps if you post in the correct section, also (and use descriptive titles).

*Thread moved to **Multimedia & Video**.*

I would have thought you would need to uninstall:

fglrx-amdcccle
fglrx

... and anything else fglrx related to uninstall the amd drivers. This command:

```
amdconfig --uninstall
```

I have no idea about. Where did you find it? I don't find 'amdconfig' in the repos anywhere. Looks like a file, perhaps part of a third-party driver you installed manually. 

Good luck.

---

### Post by DenyingProduct on 2013-10-30
sorry about that I was not aware of that i am still new to this forum.

---

### Post by Bucky Ball on 2013-10-30
All good. ;)

I have edited my last post. You might find some clues there.

---

### Post by DenyingProduct on 2013-10-30
I gave up and scrapped the entire os and re installed from scratch -___-

---

