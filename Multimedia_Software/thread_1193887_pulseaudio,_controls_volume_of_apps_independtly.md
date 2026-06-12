---
title: "pulseaudio, controls volume of apps independtly?"
date: 2009-06-22
forum: Multimedia Software
---

### Post by keypox on 2009-06-22
How do i enalbe this? I read that is the reason ubuntu uses pulseaudio? 

[http://brainstorm.ubuntu.com/idea/7557/](http://brainstorm.ubuntu.com/idea/7557/)

---

### Post by LKjell on 2009-06-22
Open a terminal and type in

```
sudo apt-get install paman
pavucontrol &
```

There is also another way by installing gnome-volume-control-pulse package. Though it creates confusion in System => Preference.

---

### Post by keypox on 2009-06-22
> **LKjell said:**
> Open a terminal and type in

```
sudo apt-get install paman
pavucontrol &
```

There is also another way by installing gnome-volume-control-pulse package. Though it creates confusion in System => Preference.

cool thanks man that worked... anyway to make this the default? Or is that not recommended?

---

### Post by LKjell on 2009-06-22
Default? You can add a launcher. Left click on the panel and click add to panel...

---

### Post by keypox on 2009-06-22
> **LKjell said:**
> Default? You can add a launcher. Left click on the panel and click add to panel...

ok thanks again...

---

