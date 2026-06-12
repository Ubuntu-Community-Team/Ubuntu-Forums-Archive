---
title: "Need help installing latest new nVidia driver..."
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by jonathanmotes on 2007-09-25
I can't seem to find any definite suggestions on how to install the latest nVidia driver (version 100.14.19) on the forums. I have a lot of questions: What seems to be the most popular way to install it? Is it best to follow the instructions on nVidia's website, or use an Envy script? I would rather not try anything that is not "undo-able." Are there any nice tutorials that I am just skipping over? If you've gotten it to work, could you post how you did it? 

Thanks!

---

### Post by wolfen69 on 2007-09-25
```
sudo apt-get install nvidia-glx-new
```
is that easy enough?

---

### Post by jonathanmotes on 2007-09-25
> **wolfen69 said:**
> ```
sudo apt-get install nvidia-glx-new
```
is that easy enough?

Well, I thought that the driver wasn't in the repositories since it was only released last week or so....am I wrong?

EDIT: I can't check in the package manager right now because of the problems I'm having described [here]("http://ubuntuforums.org/showthread.php?t=559938").

---

### Post by ~LoKe on 2007-09-25
```
sudo apt-get install envy
```
```
envy -g
```

---

