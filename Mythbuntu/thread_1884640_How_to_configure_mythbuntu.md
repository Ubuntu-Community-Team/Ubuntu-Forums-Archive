---
title: "How to configure mythbuntu?"
date: 2011-11-21
forum: Mythbuntu
---

### Post by xwang on 2011-11-21
Hi to all!
I've just installed Mythbuntu.
I've not found yet how to configure the audio level since it is very low.
Moreover I would like to use myth to see my media file (which are on an external hard disk), but I don't know how to configure it to search files in the hard disk.
Can you help me?
Thank you,
Xwang

---

### Post by PhilWig on 2011-11-30
Hi Xwang,
two things to do:

1.  run alsamixer in a terminal session.
set master and line volumes up with +.
Escape out

2.  Set volume sliders in frontend>setup>general

Best wishes.
Phil

---

### Post by xwang on 2011-11-30
> **PhilWig said:**
> Hi Xwang,
two things to do:

1.  run alsamixer in a terminal session.
set master and line volumes up with +.
Escape out

2.  Set volume sliders in frontend>setup>general

Best wishes.
Phil

Thank you!
Xwang

PS Can you explain me how to add files to the Media Library?

---

### Post by nickrout on 2011-12-01
> **xwang said:**
> Thank you!
Xwang

PS Can you explain me how to add files to the Media Library?

I assume you mean mythvideo. If not ignore the following and explain yourself better.

Add your video files to the path myth expects to find videos in, by defaukt in mythbuntu it is /var/lib/mythtv/videos [1]

Then go to mythvideo and press the menu key (m by default) and choose scan.

[1] alternatively set the video path in storage groups setup in mythtv-setup to the directory where you choose your videos, amke sure permissions and ownerships are appropriate and then scan as above.

---

### Post by xwang on 2011-12-01
> **nickrout said:**
> I assume you mean mythvideo. If not ignore the following and explain yourself better.

Add your video files to the path myth expects to find videos in, by defaukt in mythbuntu it is /var/lib/mythtv/videos [1]

Then go to mythvideo and press the menu key (m by default) and choose scan.

[1] alternatively set the video path in storage groups setup in mythtv-setup to the directory where you choose your videos, amke sure permissions and ownerships are appropriate and then scan as above.

Thank you!
Xwang

---

### Post by romerje on 2012-04-21
[QUOTE=nickrout;11503170]I assume you mean mythvideo. If not ignore the following and explain yourself better.

Add your video files to the path myth expects to find videos in, by defaukt in mythbuntu it is /var/lib/mythtv/videos [1]

can change everything to direct my videos to the right place....but I do not have a menu choice on the main myth menu for "videos"  I have media library -->music, pictures, search internet and browse internet...nothing for videos.  Can you direct me somewhere or tell me how to add that menu choice?  Thanks

---

### Post by williammanda on 2012-04-22
> **romerje said:**
> [QUOTE=nickrout;11503170]I assume you mean mythvideo. If not ignore the following and explain yourself better.

Add your video files to the path myth expects to find videos in, by defaukt in mythbuntu it is /var/lib/mythtv/videos [1]

can change everything to direct my videos to the right place....but I do not have a menu choice on the main myth menu for "videos"  I have media library -->music, pictures, search internet and browse internet...nothing for videos.  Can you direct me somewhere or tell me how to add that menu choice?  Thanks

What version of mythtv are you using?

---

### Post by nickrout on 2012-04-29
> **romerje said:**
> [QUOTE=nickrout;11503170]I assume you mean mythvideo. If not ignore the following and explain yourself better.

Add your video files to the path myth expects to find videos in, by defaukt in mythbuntu it is /var/lib/mythtv/videos [1]

can change everything to direct my videos to the right place....but I do not have a menu choice on the main myth menu for "videos"  I have media library -->music, pictures, search internet and browse internet...nothing for videos.  Can you direct me somewhere or tell me how to add that menu choice?  Thanks[/QUOTE]

Sort your quoting out.

Sounds like you don't have mythvideo installed.

```
sudo apt-get install mythvideo
```

---

