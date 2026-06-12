---
title: "Playing Mp3 files....  going crazy"
date: 2008-12-13
forum: Multimedia Software
---

### Post by chaztrip on 2008-12-13
So I am new to Ubuntu... been a Widows Admin forever and just trying to learn some new stuff.  

Anyway I can play sound with the default player in rhythembox..  like radio or if I go to you tube I can hear sound no problem.  I mount a windows share containing .mp3 files on it and I see them fine, but I cant play them.  I installed Banshee and tried to play them in there but I get nothing!!!  I have looked around and did some searching but cant seem to find a solution to this.  I have the latest build of Ubuntu.

Thanks
Charlie

---

### Post by wolfen69 on 2008-12-13
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by chaztrip on 2008-12-13
> **wolfen69 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```


I already did that and it says that I am the newest version....  :-(

---

### Post by chaztrip on 2008-12-14
Anyone else?

THanks

---

### Post by kpkeerthi on 2008-12-14
1. Copy a mp3 file from the share to your home folder. [test.mp3]

2. Play it from using a command line tool like mplayer. If you do not have mplayer installed, install it:
```
sudo apt-get update && sudo apt-get install mplayer
```

3. Try playing the file you just copied over
```

mplayer test.mp3

```

Does it print anything useful on the console ?

---

### Post by chaztrip on 2008-12-14
> **kpkeerthi said:**
> 1. Copy a mp3 file from the share to your home folder. [test.mp3]

2. Play it from using a command line tool like mplayer. If you do not have mplayer installed, install it:
```
sudo apt-get update && sudo apt-get install mplayer
```

3. Try playing the file you just copied over
```

mplayer test.mp3

```

Does it print anything useful on the console ?

Well I just copied over an mp3 and it plays fine in banshee local.  So what am I missing that I cant play the share...  I am connected with full permissions?

thanks!!!!

---

