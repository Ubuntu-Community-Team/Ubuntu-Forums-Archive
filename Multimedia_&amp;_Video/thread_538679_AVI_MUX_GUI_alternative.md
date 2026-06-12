---
title: "AVI MUX GUI alternative"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by 6205 on 2007-08-30
Hello,

Do anybody know usable alternative to application AVI-Mux GUI for Ubuntu Feisty?
I need it mostly for merging various type of files and this app is excellent.[http://www.alexander-noe.com/video/amg/](http://www.alexander-noe.com/video/amg/)

I have tried MKV toolnix, its great for some things, but it cannot merge 2 MKV files.
If i merge 2 MKV files, it only looks OK but it will still play only first one...

---

### Post by yabbies on 2007-08-30
I'm currently at work and don't have all my docs in front of me, as long as you are not afraid of using the terminal, I can give you a how-to for using ffmpeg, mencoder, etc for all your muxing needs.

in the mean time see if this works.

open a terminal and type

```
cat *filename1*.mkv *filenam2*.mkv
```

this will combine both files into one, works really well for avi
but a lot of times you will need to use mencoder to fix the scr.

---

### Post by 6205 on 2007-08-30
What did you mean with .."but a lot of times you will need to use mencoder to fix the scr" ? Sounds Bad...

I am not afraid of terminal when is there no gui front-end for merging video files, but at least 100% fully functional guide would be great. 

When i download some anime, mostly separated in two files, i'm using MKV toolnix to edit language and subtiles options and then i merge these two newly edited re-muxed files into one final file with AVI-Mux GUI...It is open source software, but too bad - without linux port :( 

And now i have 1+ reason for me to keep WinXP in dualboot with Feisty...Bud anyway, thanks for help :)

---

### Post by yabbies on 2007-08-31
are you going to be burning the combined vids to a dvd? or just watching on the computer?

when combining files such as one avi with another avi, in most cases there is not a clean edit.
so when you combine the two vids there is a small break from the first file to the next. So to the time counter it thinks it is moving backwards.
Such as you have video 1 that is 2:03 and video 2 is 4:26. When the first video plays and at the end of the 2:03 the millisecond break starts the counter over making it think that the time is moving backwards.

Mencoder succesfully will encode the 2, 3 or however many videos you have combined so there is no break. 

The only time I have ever had to completely and manually remux my whole video was from a video camera where I hadn't edited the raw vids. I wanted to keep it all intact.

dealing with mkv it might be a necessary step to encode to avi before you can remux.

If this what interests you then I can give you a how-to to take your mkvs combine and encode to avi to either play on the computer or encode to mpeg and burn to a dvd.

---

### Post by 6205 on 2007-08-31
I watch those movies in computer and there is no easy way (if any) to convert MKV to DVD.
When i was using AVI-Mux GUI, merging was allways perfect, but unfortunately linux is missing 
many key apps...but maybe somebody could write some nice tango-gui front-end for mencoder...

---

### Post by shirilover on 2007-08-31
To merge 2 or more mkv files is rather simple.
In the MKVMergeGUI, after adding the first file, use the append button to add the next file.

---

