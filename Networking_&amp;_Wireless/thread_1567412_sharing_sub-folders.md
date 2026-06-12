---
title: "sharing sub-folders?"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by scradock on 2010-09-03
I'm trying to set up one machine to "serve" music to several others, running ubuntu or windows. Sharing the main "Music" folder is fine (Using Sharing in Nautilus), but the sub-folders in it are not accessible. I have tried setting the file permissions on the server (all 755), but that doesn't seem to affect the situation - the Music folder is available, so are any music files directly in Music, but trying to open the folder "JazzMisc" within Music fails.

The way I have found to get around this is to separately set up JazzMisc, and many other folders, as shares; but then I have dozens of shares, rather than a folder tree under Music in which I can find what I want.

What am I missing?

---

### Post by Morbius1 on 2010-09-03
It sounds like a permissions issue to me. 

Post the output of these two commands:
```
net usershare info
```
```
ls -al /path-to-your-Music-folder
```

---

### Post by scradock on 2010-09-03
> **Morbius1 said:**
> It sounds like a permissions issue to me. 

Post the output of these two commands:
```
net usershare info
```
```
ls -al /path-to-your-Music-folder
```

Thanks for the suggestions: the problem was indeed permissions.

I had inadvertently set the permissions for the sub-folders to 766, not 755. Resetting them to 755 solved the problem.

---

