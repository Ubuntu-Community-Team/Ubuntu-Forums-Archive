---
title: "Unity on 10.10"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rplantz on 2011-03-24
I ran across [http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/), which tells how to install unity on 10.10:
```

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update

sudo apt-get install unity-2d

```

Has anybody tried this? Is this any different than simply installing unity from the (10.10) repositories?

---

### Post by cariboo on 2011-03-24
The 2D version of Unity was written using the QT libraries, the version in the Maverick (10.10) was written using mutter, I don't recommend using it, as it is broken on some makes of computers.

---

### Post by rplantz on 2011-03-24
> **cariboo907 said:**
> The 2D version of Unity was written using the QT libraries, the version in the Maverick (10.10) was written using mutter, I don't recommend using it, as it is broken on some makes of computers.

Thank you for your response, but which one does "it" refer to?

---

### Post by cariboo on 2011-03-24
The Unity in the repositories, is the broken one.

---

