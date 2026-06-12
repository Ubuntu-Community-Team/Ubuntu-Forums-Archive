---
title: "Playing DVD from folder"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by imaca on 2007-06-20
Hi - can anyone help me on how to play a dvd from folder using something other than VLC? - (preferably Xine since this seems to work best in every other way)
VLC is no good to me because it seems incapable of output to SPDIF which is what I need for sound.
Xine has an "Open Location" command in the menu but once in the dialogue it doesn't seem possible to actually do anything.

Any help much appreciated - this is only reason I use windows now except printing photos (better quality on Canon) and playing games

---

### Post by yabbadabbadont on 2007-06-20
Using xine, you have to provide the full path to the folder that contains the VIDEO_TS folder.

xine dvd://home/user/movies/movie-to-watch

Edit: you can only do this from a terminal window or the Alt-F2 run dialog in Gnome or KDE.

---

### Post by nutz on 2007-06-20
VLC will open folders, for instance if you had a DVD copied to your hard drive.

---

### Post by yabbadabbadont on 2007-06-20
> **nutz said:**
> VLC will open folders, for instance if you had a DVD copied to your hard drive.

He already stated that vlc was no good for him and his reason why....  ;)

---

### Post by imaca on 2007-06-20
Thanks - I have seen this mentioned before but it doesn't work for me. All I get is
-xine engine error-
Input plugin failed to open mrl

---

### Post by yabbadabbadont on 2007-06-20
You've got something else wrong then.  I just tested it to be sure that I gave you the correct syntax.  :?

What was the exact command you used?

---

### Post by imaca on 2007-06-20
xine dvd//path_to_of_folder_containing_VIDEO_TS

Also tried

xine dvd//path_to/VIDEO_TS

---

### Post by YoG%*@ on 2007-06-20
hi!
> **imaca said:**
> xine dvd//path_to_of_folder_containing_VIDEO_TS

Also tried

xine dvd//path_to/VIDEO_TS

did you write the colon?
```

xine dvd**:**//path_to_of_folder_containing_VIDEO_TS

```

---

### Post by imaca on 2007-06-20
ummm duh!
NO I didn't
Works now thanks very much!:p

---

### Post by YoG%*@ on 2007-06-20
you're welcome ;)

---

