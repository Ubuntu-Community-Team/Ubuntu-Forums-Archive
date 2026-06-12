---
title: "Avi file which was encoded by Mencoder  is not recognized by portable dvd player"
date: 2009-06-23
forum: Multimedia Software
---

### Post by haneulso on 2009-06-23
I have a panasonic dvd-ls855 portable dvd player.
It can play divx and mpeg files.
But, it cannot sometimes play some files even though its extension is .avi.
So, I am trying to convert these video files to divx format even though their format are already divx.
I use this command.

"mencoder foo.avi -ovc lavc -oac mp3lame -o foo2.avi"

The convert was successful.And it can be played in Desktop.

But, my panasonic player cannot play converted avi file.

Is there any other option for this?

Or any other program is useful?

Thank.

---

### Post by starcraft.man on 2009-06-23
I don't know if it's the answer your looking for, but devede is a great program for this. It creates fully compliant standard DVD movies, as well as Divx DVDs for players such as yours I believe, and it's got a fairly nice gui. 

It's in the basic repositories, just install the package named devede by whatever means. Pretty intuitive after that.

---

### Post by andrew.46 on 2009-06-24
Hi haneulso,

> **haneulso said:**
> 
I use this command.
```
mencoder foo.avi -ovc lavc -oac mp3lame -o foo2.avi
```
The convert was successful.And it can be played in Desktop.
But, my panasonic player cannot play converted avi file.


By default the conversion you are doing will use a fourcc of FMP4 for the resulting mpeg4 video and I believe that some devices will baulk at this. One solution is to add:

```
-ffourcc XVID
```

to your encoding string and this may be enough to keep your device happy.

Andrew

---

### Post by haneulso on 2009-06-24
Thans guys.
This is useful and helpful.
But, my problem is not codec.
The problem is video image size.
My player cannot play a file which has image size over 720x480.
I will post a new thread for this.
Thanks.

---

