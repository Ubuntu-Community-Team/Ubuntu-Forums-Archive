---
title: "Don't have permission to play movie dvd"
date: 2009-06-29
forum: Multimedia Software
---

### Post by burrhead1 on 2009-06-29
I just downloaded Ubuntu 9.04 and I can't get movie dvds to play. After I insert the dvd and go thru the steps to play it I get a message to the effect "you don't have permission or authorization to play". I get this type of message with both the Ubuntu Movie Player and VLC. I purchased the dvd from Amazon and it will play on Windows and Mac laptops. I am not trying to rip the movie but only to play it. Any advice would be greatly appreciated. burrhead1

---

### Post by colau on 2009-06-29
> **burrhead1 said:**
> I just downloaded Ubuntu 9.04 and I can't get movie dvds to play. After I insert the dvd and go thru the steps to play it I get a message to the effect "you don't have permission or authorization to play". I get this type of message with both the Ubuntu Movie Player and VLC. I purchased the dvd from Amazon and it will play on Windows and Mac laptops. I am not trying to rip the movie but only to play it. Any advice would be greatly appreciated. burrhead1
```

gksudo nautilus

```

---

### Post by colau on 2009-06-30
> **burrhead1 said:**
> I just downloaded Ubuntu 9.04 and I can't get movie dvds to play. After I insert the dvd and go thru the steps to play it I get a message to the effect "you don't have permission or authorization to play". I get this type of message with both the Ubuntu Movie Player and VLC. I purchased the dvd from Amazon and it will play on Windows and Mac laptops. I am not trying to rip the movie but only to play it. Any advice would be greatly appreciated. burrhead1
Did you install libdvdcss2?
```

sudo apt-get install libdvdcss2

```
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by burrhead1 on 2009-07-01
Many thanks for the advise colua. Followed the link you provided, downloaded the software and now I'm playing the dvds. Best regards, burrhead1

---

### Post by colau on 2009-07-01
> **burrhead1 said:**
> Many thanks for the advise colua. Followed the link you provided, downloaded the software and now I'm playing the dvds. Best regards, burrhead1
Welcome.

---

### Post by loboc on 2009-07-01
> **colau said:**
> ```

gksudo nautilus

```


this may be a mistake. then your whole desktop environment has root access 

```
sudo adduser 'name' disc
``` will add you to the group of users allowed to manipulate the discs

---

### Post by 3rdalbum on 2009-07-01
double-post

---

### Post by 3rdalbum on 2009-07-01
> **loboc said:**
> 

```
sudo adduser 'name' disc
``` will add you to the group of users allowed to manipulate the discs

It was a DVD decryption issue, not a permissions issue.

---

