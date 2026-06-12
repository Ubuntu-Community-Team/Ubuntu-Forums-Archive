---
title: "Youtube stops playing after a few seconds"
date: 2009-02-16
forum: Multimedia Software
---

### Post by epqr on 2009-02-16
So youtube videos stops playing after a certain amount of seconds. about 25 seconds into the movie. Its the same with all browsers ive tried (firefox, opera, seamonkey). I've seen people have issues like this before, but never a real solution. any help?

---

### Post by Majkijin on 2009-02-18
I'd had the same problem until I noticed that I had no free space on my root drive "/". After freeing some space on "/" youtube started to work again. You would also need to restart your machine after freeing some space on "/" if your /tmp folder had already been mounted as "overflow".

---

### Post by khelben1979 on 2009-02-18
Do you know what flashplayer that you are using?

[Gnash]("http://en.wikipedia.org/wiki/Gnash") is the slower variant of the flashplayer while [the one from Adobe]("http://en.wikipedia.org/wiki/Adobe_flash") has pretty good speed with no notice'able slowdowns (if the machine is fast enough).

---

### Post by epqr on 2009-02-21
> **Majkijin said:**
> I'd had the same problem until I noticed that I had no free space on my root drive "/". After freeing some space on "/" youtube started to work again. You would also need to restart your machine after freeing some space on "/" if your /tmp folder had already been mounted as "overflow".

Then im sure that the problem, I've don't even have enough space to download a file (needs space in /tmp). Any advice on how to free space without deleting necessary files?

---

### Post by Majkijin on 2009-02-21
> **epqr said:**
> Then im sure that the problem, I've don't even have enough space to download a file (needs space in /tmp). Any advice on how to free space without deleting necessary files?

Try:
```
sudo apt-get clean
```
It'll remove unnecessary deb files that was downloaded when you was installing or upgrading some packages.
If it don't free enough disk space, you'll need to remove manually some packages (for instance unused old versions of kernel images if any).

---

### Post by lukjad on 2009-02-21
Also, here's something that could prove useful. There is a program called youtube-dl that downloads the videos to your hard drive. It's useful for when you have too little bandwidth left to spare and want to see a vid.

---

