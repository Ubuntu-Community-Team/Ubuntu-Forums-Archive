---
title: "Add songs from sub-folders recursively to Totem using terminal"
date: 2011-01-18
forum: Multimedia Software
---

### Post by K-Jtan on 2011-01-18
Hi everyone,

I hope I put this question in the right section. (It's my first post on this forum).

This is my problem, I want to add many songs to my Totem (movie player) playlist. These songs are in different sub-folders and it's pretty long to open every single folder to add them to Totem. 

I currently know how to use the terminal to put all the mp3 files in the playlist using this syntax : 

```
totem *.mp3
```or
```
totem --enqueue *.mp3
```Is there a way to say "*totem -r *.mp3*" and it will take all the .mp3 that are in the sub-folders from the current location?

---

### Post by kai4785 on 2011-10-10
Try this? I find it helpful if totem is already running, so the call to totem here doesn't steal my terminal. I usually start totem from F2.
```
find . -iname \*.mp3 -print0 | xargs --null totem --enqueue
```

---

### Post by K-Jtan on 2011-10-11
Thank you, it worked perfectly :D

I will make a small script for that so I don't need to type it every time. (I learn how to do those last week at my school)

---

