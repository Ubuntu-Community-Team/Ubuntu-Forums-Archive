---
title: "image viewer(eog)"
date: 2015-12-21
forum: Multimedia Software
---

### Post by wyndlass on 2015-12-21
i just downloaded a pic a friend did of her and her daughter and sent to me in email. eog only shows a blank screen with the pic. file in cli says that it's jpg, matching the extension and so do the properties box in the gui. the image shows fine in gimp, i am going to test shotwell with the pic. just wondering why eog won't display the pic. my system is a samsung np-nc10 with intel atom n270 cpu and intel 953 gpu 2gb ram 250gb hd and was borrowing a friends external monitor last night since my laptop screen broke. eog works just fine with other pics. tonight i'm gonna also see if eog will display the pic on an ancient crt vga monitor. is this just a glitch? i also put the pic on my deactivated metro pcs phone and the pic shows fine on that. thanx

---

### Post by ajgreeny on 2015-12-21
See what errors show if you open the jpg in eog with the command line ```
eog file.jpg
```

---

### Post by wyndlass on 2015-12-24
here is the eog error...

```


(eog:14542): EOG-WARNING **: Failed to open file '/home/jad/.cache/thumbnails/normal/3800dd5a78f9939d1ad533cdfe7c8685.png': No such file or directory


```

the regular image viewer prog shows the jpg just fine as does shotwell. i don't see why eog would have a problem with just this pic, it's odd.

---

### Post by Vladlenin5000 on 2015-12-24
What is really odd is opening something from ..../**.cache**/thumbnails...

---

### Post by mc4man on 2015-12-24
> **wyndlass said:**
> here is the eog error...

```


(eog:14542): EOG-WARNING **: Failed to open file '/home/jad/.cache/thumbnails/normal/3800dd5a78f9939d1ad533cdfe7c8685.png': No such file or directory


```

the regular image viewer prog shows the jpg just fine as does shotwell. i don't see why eog would have a problem with just this pic, it's odd.
running eog from cli typically shows that Warning, seems irrelevant. Also in Ubuntu eog is the regular "Image Viewer"

---

### Post by wyndlass on 2015-12-26
like i said, eog shows other pics just fine. i have no idea why it's looking for a png file when what i'm telling it to show is jpg. the jpg, regardless of how you check it's file info, always comes up jpg(jpeg). plus the fact the other image viewer, gimp, shotwell, image magik all have no problems displaying it at all, neither does chrome. strange, i had to reinstall eog to run it to display the file, just shows a black screen and shows that error at cli.

---

### Post by wyndlass on 2016-01-26
i uninstalled eog and use the other image viewer now.

---

