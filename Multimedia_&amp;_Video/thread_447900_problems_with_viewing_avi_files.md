---
title: "problems with viewing avi files"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by doubleuicked on 2007-05-18
Hey guys,

I have some axxo produced avi files, which i have no problem opening, however when it plays on my video player there is a thick green line on the top and also distorted colors that appear for the whole video.

any clues??

thanks in advance!

---

### Post by The Seeker on 2007-05-18
Try playing it with VLC.

```
sudo aptitude update && sudo aptitude install vlc
```

---

### Post by doubleuicked on 2007-05-18
still the same thing, and it has been the same problem for 3 separate axxo files. Im thinking its possibly a codec issue??

---

### Post by rigelstar on 2007-06-08
I can confirm the same exact problem with playback of axxo movie's while using vlc and other decoders.  The above green horizontal bar problem only occurs when viewing a movie encoded by axxo thus far.  Any luck so far finding a solution?

---

### Post by rigelstar on 2007-06-08
Depending on your video card the horizontal green line is produced when the default video output module is selected for the given media player.  

For example I only found this problem after switching from an ati to a nvidia video card using the default output module. 

To correct this go into preferences for VLC (this can be repeated for any media player); 

1) select advanced options 
2) click output modules and you will see various output choices.  
3) try different outputs until you find one that works for you. 

I choose OpenGL and the video is now being displayed correctly.  

Hope this helps.

---

