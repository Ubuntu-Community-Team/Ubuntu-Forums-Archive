---
title: "fglrx 8.25.18 and tk applications"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by ilbahr on 2006-06-05
Installed the latest fglrx 8.25.18 drivers from the repos on my i686 machine using  9600 ati card. Everything works fine till i run an tk application which refuses to work such as xmaxima, tkremind where i get this error message

"Application initialization failed: this isn't a Tk applicationunknown color name "Black"
Error in startup script: can't invoke "wm" command:  application has been destroyed
    while executing
"wm withdraw ."
    (file "/usr/bin/tkremind" line 20)"



or works imporperly

such as scilab where i had messed up fonts and half of the menus do not work.

Now all those applications runs fine using the opensource radeon drivers. just i have problems with cpu loads. Any one have a solution for this stupid bug.

Just to close this post i hate ati cards they have always been a pain.

---

### Post by empthollow on 2006-06-05
i recently had a problem with tk apps,  turns out the rgb.txt file was refered to wrong in the /etc/X11/xorg.conf file.  it said the path was /usr/X11R6/lib/X11/rgb and the actual path was /etc/X11/rgb

---

### Post by ilbahr on 2006-06-06
thank you empthollow you are a life saver. Just making a symbolic link to the file under the old path did the trick. Thanx again.

:D

---

