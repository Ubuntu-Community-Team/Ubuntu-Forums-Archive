---
title: "Mencoding programming query"
date: 2011-09-13
forum: Multimedia Software
---

### Post by Mangesh_B on 2011-09-13
Hi all,

 I am using mencoder (MPlayer) for recording the TV programs, But i want to take some snapshot at regular interval. So can somebody help me out doing the same.

---

### Post by aeiah on 2011-09-13
mencoder isn't interactive, so you'll have to call another program to do it (or use a 2nd instance of mencoder).

you may find that two programs cant access your tv card at the same time, in which case, it might be best to take the snapshot from the file mencoder is recording into.

found this on the doom 9 forums:
> 
According to the manual, yes, -ss specifies a time, not a percentage.

I don't know if there's an easier way, but the following works (at least in linux):

create a text file (commands.txt) with this content:

seek 20 1
screenshot
pause
quit


(the first value for seek is the percentage)

And then run:

mplayer video.avi -slave -nosound -vf screenshot < commands.txt



instead of seek 20 1, you could do seek 96 1 to seek 96% of the way through the file, which will be an area that's been fairly recently recorded.

instead of the script, you might just be able to use this command, but i cant test either:
```

mplayer video.avi -slave -nosound -vf screenshot < (seek 96 1;screenshot;pause;quit;)
```

---

### Post by shantiq on 2011-09-13
[**tip 5**]("http://ubuntuforums.org/showthread.php?t=1154431") might give you ideas

---

