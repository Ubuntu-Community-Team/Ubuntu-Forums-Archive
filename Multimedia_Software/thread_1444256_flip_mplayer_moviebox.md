---
title: "flip mplayer moviebox"
date: 2010-04-01
forum: Multimedia Software
---

### Post by littlepeon on 2010-04-01
hey there.....
tried a quick google...no luck, so maybe some1 here knows how...

am using gtk-record-mydesktop and am inserting a snapshot from my webcam using the following code:
```
mplayer -vo xv tv:// -tv driver=v4l2:width=640:height=480:fps=30:device=/dev/video0
```

which works....
now my problem...webcam is locked to laptop lid...i can rotate it outwards to view what i'm seeing (instead of viewing myself) but now the view is upside down (rotated 180 degrees)

what code do i now need to use to rotate this image 180 degrees upright????

thxs
-Peon

---

### Post by andrew.46 on 2010-04-01
Hi Peon,

> **littlepeon said:**
> what code do i now need to use to rotate this image 180 degrees upright????

Try:

```
mplayer **[COLOR="Red"]-flip[/COLOR]** -vo xv etc etc
```

More options are available btw using *-vf rotate=n*, for example:

```
mplayer **[COLOR="Red"]-vf rotate=2[/COLOR]** my_file
```

will rotate 90 degrees counterclockwise and there are several other optins available for this filter...

All the best,

Andrew

---

### Post by littlepeon on 2010-04-01
hey,

thankyou, thankyou, thankyou

works like a charm now!!!!!

i need to study up on my command line arguments.....but just found this one tonight and can use it right away in an email to a friend..

thanks again
-Peon

---

### Post by andrew.46 on 2010-04-01
Hi Peon,

> **littlepeon said:**
> thankyou, thankyou, thankyou

works like a charm now!!!!!

It is completely my pleasure :).

Andrew

---

