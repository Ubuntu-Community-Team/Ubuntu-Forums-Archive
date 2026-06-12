---
title: "Muted audio with realtek alc833 in feisty"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by nicky.7 on 2007-04-26
I have a new acer 9302 notebook. Everything work great with ubuntu 7.04  execpt the web cam (not essential) and audio.
Audio Card (a realtek alc833) is configurated, even the hot key works, but i have no audio output at all!!!
I have to use windows vista!!! Please help me.
nicola

---

### Post by Dekunuts on 2007-04-26
If your desktop is still configured as default, there should be a sound icon at the top right of the screen. Double click it and the sound levels dialog opens. There you can change a lot of things, it's a common problem for people to have no sound because something in there is muted. I'm not saying that IS the answer, but changes are high.

---

### Post by Beliar on 2007-04-26
Try this: [http://ubuntuforums.org/showthread.php?p=2538966#post2538966](http://ubuntuforums.org/showthread.php?p=2538966#post2538966) 
If you have problems, post in that thread. Maybe we just have to fine tune the options ;)

---

### Post by barney_1 on 2007-04-26
I would also make sure that you are member of the user group "audio".

List groups you are a member of:
```
$ groups <username>

```

You should see "audio" in that list.  If you don't:
```
sudo usermod -a -G audio <username>
```

---

