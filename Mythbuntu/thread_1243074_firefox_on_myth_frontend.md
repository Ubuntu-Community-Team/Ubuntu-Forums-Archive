---
title: "firefox on myth frontend"
date: 2009-08-17
forum: Mythbuntu
---

### Post by derrickadean on 2009-08-17
I was wondering if there was a way to use firefox on my frontend. 
i read some tutorials and correct me if im wrong but you have to of first installed mythweb i dont wont to have to do this i am a new user and dont wont to have to compile mythweb    is this passable

---

### Post by nasha on 2009-08-17
Correct me if i'm wrong but firefox is installed by default?
I cant see why you would need mythweb to use firefox either....

If for some reason you dont have firefo installed:
```
sudo apt-get install firefox-3.0
```

Cheers,
Nasha

---

### Post by derrickadean on 2009-08-20
i know that i have firefox on the os its self but what i wont to do is be able to access it from the myth frontend there are some tutorals. but they say replace /usr/bin/mythbrowser with /usr/bin/firefox in Configuration: Web Settings i checked for /usr/bin/mythbrowser and cold not find the path in the filesystem
so i came to the conclusion that mythbrowser must make this path there must be a better way

---

### Post by ahood on 2009-08-21
> **derrickadean said:**
> ... i checked for /usr/bin/mythbrowser and cold not find the path in the filesystem
so i came to the conclusion that mythbrowser must make this path there must be a better way

That is the correct conclusion. Mythweb includes its own web browser that isn't Firefox. 

What Mythweb does is provide the menu links to launch a web browser from within the MythTV frontend. As you are aware, it is possible to configure Mythweb to launch a different browser that is installed on the system, such as Firefox. Search the Ubuntu Forum, Google, or see [**[COLOR="Blue"]HERE[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=7805356&postcount=16") for instructions on how to do this.

It is not a requirement to use Mythweb for this purpose. Instead, some users have manually added a menu link to Firefox. I have not done this. Search this forum to find out how to manually edit the menu list. Keep the instructions saved in case the steps need to be followed after an upgrade sometime in the future.

---

