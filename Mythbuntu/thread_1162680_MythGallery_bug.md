---
title: "MythGallery bug"
date: 2009-05-17
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-05-17
I just notice some of the family photos are missing.  Got to poking around and found they are on the harddrive and in the mythgallery directory.

It appears mythgallery likes to display 4 rows x 7 columns on a 1920 x 1080 monitor.  The bug is there is only room for 4 rows x 6 columns.  The last column is off the screen.

Anybody else confirm that?

Is there a config place where I can specify 4 x 6 and not 4 x 7?


Thanks

---

### Post by joho500 on 2009-05-19
What thema are you using? I had the same problenm with Project Grayhem Wide. On a different resolution though.

Cheers,
Joost

---

### Post by Dewey_Oxberger on 2009-05-20
It's the default theme.  Is the row/column stuff in the theme?

---

### Post by joho500 on 2009-05-21
I had the same problem with the Project Grayhem Wide theme and adjusted the display area in the file gallery-ui.xml. That worked for me. Not sure you should do the same with the default theme. 

Appearently it has something to do with the resolution one uses. I wonder whether others have the same problem. In that case it would be better to have an option to adjust the number of rows/columns.

Cheers,
Joost

---

### Post by Dewey_Oxberger on 2009-05-22
Thanks for the help.  It looks like the theme Mythbuntu-8.04-wide has some problems but you can fix them by tinkering in the xml file.  (It looks like the "blackhole" section needs to be reduced a bit.

---

### Post by usererror on 2009-07-28
If you need an example, check out this thread: 

[http://ubuntuforums.org/showpost.php?p=7692073&postcount=6](http://ubuntuforums.org/showpost.php?p=7692073&postcount=6)

user, crez79, posted a fix for the theme glass-wide.

I had the same problem as the OP, but when I searched I did not find this thread.

---

