---
title: "Hunting and printing time and day to IP camera image series..terminal"
date: 2022-11-12
forum: Multimedia Software
---

### Post by jari169 on 2022-11-12
a comment to the Ubuntu terminal, which is used to run the time and date in the upper right corner of the ip camera image.. Eg bash?

 thanks

---

### Post by TheFu on 2022-11-12
> **jari169 said:**
> a comment to the Ubuntu terminal, which is used to run the time and date in the upper right corner of the ip camera image.. Eg bash?

 thanks

I think imagemagick has a tool for this.  I think you want a text overlay.  A quick google found this: 
[https://legacy.imagemagick.org/discourse-server/viewtopic.php?t=23823](https://legacy.imagemagick.org/discourse-server/viewtopic.php?t=23823)

```
convert "$i" -font Arial -pointsize 48 -fill lightblue -gravity southeast -auto-orient -annotate +80+50 %[exif:DateTimeOriginal] "$i"
```

Is stolen from that link.  $i is the original filename.

---

### Post by jari169 on 2022-11-12
How server **realtime?
convert "$i" -font Arial -pointsize 48 -fill lightblue -gravity southeast -auto-orient -annotate +80+50 "**time-tags there**" "$i"
Realtime not works

thanks!

---

### Post by TheFu on 2022-11-12
$(date)
?

Not sure what you seek.  The EXIF data inside the photo should have the time that the photo was taken, so that would be more important than the time than the script it run.

---

### Post by mIk3_08 on 2022-11-14
> **jari169 said:**
> a comment to the Ubuntu terminal, which is used to run the time and date in the upper right corner of the ip camera image.. Eg bash?
 thanks
This date and time you mean, Maybe its in the setting of the app thru web app ip camera firmware using some web browser. In my case, their I can set the time/date to show when recording or capturing image via ip camera settings. I can configure/manipulate it via web browser using the ip web app firmware. Regards and cheers.

---

