---
title: "Default behaviour of alsamixer"
date: 2014-05-01
forum: Multimedia Software
---

### Post by xeonix on 2014-05-01
Hello people.

Upgraded to 14.04, using gnome-desktop, when ever I start my laptop, the sound mode is on 0ff mode by default. Image below:

[IMG]http://i.imgur.com/bNcWBIW.png[/IMG]

Every time I have to manually set the volume. How do I make the volume to full by default?

---

### Post by ronb19495 on 2014-05-01
have you tried arrow up on the master to see if you can increase volume

---

### Post by ibjsb4 on 2014-05-01
Open it in terminal with:

```
gksudo alsamixer
```

Set the master and see if that will hold the setting.

---

### Post by xeonix on 2014-05-03
Thanks for the reply,
Yes, I could increase the volume by arrow key, thats what I mean, every time I start my OS, I had to manually do it.
I just wanted the setting of the master volume to be 100% by default.

---

### Post by Yellow Pasque on 2014-05-03
Set the volume to where you want it and run:
```
sudo alsactl store
```

---

