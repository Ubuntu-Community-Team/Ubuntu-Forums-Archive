---
title: "Banshee is Crashing"
date: 2016-10-22
forum: Multimedia Software
---

### Post by anon24 on 2016-10-22
I really like how Banshee is set up and I've been told it plays nice with the iPhone. I can't seem to get Banshee to be stable at all though. As it is scanning my library, it always crashes and never scans the whole library. Pretty much doing anything, like making the app full screen, causes Banshee to crash.

Does anyone have any suggestions? I hate pretty much all of the other music players for ubuntu. 

Clementine is annoying and doesn't allow playlist functions like Banshee does, yet it's completely playlist based? I don't understand why they don't just allow you to see all of the tracks and play them. You have to create a playlist every time you want to listen to an album or a song.

Rhythmbox is stable, but I don't like the layout that much. It reminds me of iTunes back in like 2000, but more plain and wonky. 

Anyway, I would appreciate any help. I am trying to completely ditch Windows and the only way to do that is to have a multimedia app that will allow iPhone syncing capability. I'm considering getting an ubuntu phone eventually.

Thanks in advance!

---

### Post by speartip on 2016-10-23
I have the same problem. Banshee seems very unstable on both Ubuntu & Linux Mint. Googling around, it seems very little has been done on the development of Banshee over the last 3 years.
Clementine or Rhythmbox seem to be the only reasonable alternatives.

---

### Post by CantankRus on 2016-10-23
The trouble with banshee is it relies on Xamarin's DOTNet layer, **Mono**.... so if it's not banshee causing problems
you also have to contend with bugs in Mono.
Stopped using banshee years ago.
[http://www.mono-project.com/docs/getting-started/install/linux/](http://www.mono-project.com/docs/getting-started/install/linux/)

---

### Post by mc4man on 2016-10-23
Try opening banshee > Edit > Preferences > Extensions & disable the BPM Detection utility. May prevent some crashes.
As far as vids - not best choice but will work, 1st. scan of a video folder will likely crash

---

