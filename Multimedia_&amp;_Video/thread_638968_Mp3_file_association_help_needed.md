---
title: "Mp3 file association help needed"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by jackpetrilli on 2007-12-12
I want to change my mp3 file assocation to the Listen Music Player (recently installed).

"Properties - Open With" doesn't work because the Listen Music Player (LMP) isn't offered as one of the choices.  Nor does clicking +Add work as LMP, once again, isn't offered (although crazy choices, like Firefox and Image Viewer, ARE offered).  I tried using the "custom command" module but that didn't work.  (Even though the command "listen" will open the app from the terminal, it doesn't do anything to add this command to the Add Application module.)

Shouldn't the Add Application module show me all the choices in the Applications menu, instead of just some of the inappropriate few?

Anyone have any ideas on how I can solve this problem?

- Jack

---

### Post by fenian on 2007-12-12
Click use custom command at the bottom and enter listen.

---

### Post by jackpetrilli on 2007-12-12
> **fenian said:**
> Click use custom command at the bottom and enter listen.

Already tried that.  It doesn't work.  The "listen" button does show up.  I choose it as my preferred application.  But when I double click on any mp3 file, nothing happens...

- Jack

---

### Post by jackpetrilli on 2007-12-12
I guess nobody here knows what to do...

---

### Post by srmantis on 2007-12-13
you have to go:
properties-->open with-->+add and look for at the list, it's not there then:
custom command-->search in the /usr/bin your program
it's not there, you must search where it's installed your program and   write in custom command, for example:
/usr/bin/your_program


Sorry, I'm not write very good inglish, I hope you understand
I'm using Amarok is very good mp3 player.

---

