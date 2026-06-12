---
title: "unable to view pictures"
date: 2016-09-18
forum: Multimedia Software
---

### Post by Matrix01 on 2016-09-18
Lubuntu is unable to view pictures, which imported from Android JB, Samsung Galaxy.
can you fix this?

[ATTACH=CONFIG]271251[/ATTACH]

---

### Post by howefield on 2016-09-18
> **Matrix01 said:**
> Lubuntu is unable to view pictures, which imported from Android JB, Samsung Galaxy.
can you fix this?

What does the terminal "*file*" command say about the .jpegs..

```
file examplepicture.jpg
```

---

### Post by Matrix01 on 2016-09-24
taro@taro-HP-Mini-110-3000:~$ /home/taro/Desktop/20160620_054229.jpg
bash: /home/taro/Desktop/20160620_054229.jpg: Permission denied
taro@taro-HP-Mini-110-3000:~$

---

### Post by &amp;KyT$0P# on 2016-09-24
> **Matrix01 said:**
> ```
taro@taro-HP-Mini-110-3000:~$ [COLOR="#FF0000"]**file**[/COLOR] /home/taro/Desktop/20160620_054229.jpg
```
You're missing the "file" part (corrected in my quote of your post)

---

### Post by howefield on 2016-09-25
As halogen2 said you need the "file" command to precede the path to the image.

eg.

```
hugh@yakkety-laptop:~$  file ~/Pictures/photo_2016-08-26_21-16-42.jpg 
/home/hugh/Pictures/photo_2016-08-26_21-16-42.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, baseline, precision 8, 720x1280, frames 3
hugh@yakkety-laptop:~$
```

---

### Post by Matrix01 on 2016-09-25
taro@taro-HP-Mini-110-3000:~$ file ~/home/taro/Desktop/20160620_054229.jpg/home/taro/home/taro/Desktop/20160620_054229.jpg: ERROR: cannot open `/home/taro/home/taro/Desktop/20160620_054229.jpg' (No such file or directory)


no luck?

---

### Post by howefield on 2016-09-25
> **Matrix01 said:**
> taro@taro-HP-Mini-110-3000:~$ file ~/home/taro/Desktop/20160620_054229.jpg/home/taro/home/taro/Desktop/20160620_054229.jpg: ERROR: cannot open `/home/taro/home/taro/Desktop/20160620_054229.jpg' (No such file or directory)

Just do..

```
file ~/Desktop/20160620_054229.jpg
```

~/ is a short hand way of typing the path to your home folder.. so ~/Desktop/20160620_054229.jpg would be the same as /home/taro/Desktop/20160620_054229.jpg

---

### Post by Matrix01 on 2016-10-02
file ~/Desktop/teeth2/20160505_075446.jpg/home/taro/Desktop/teeth2/20160505_075446.jpg: ASCII text

---

