---
title: "Soundblaster Audigy no sound"
date: 2009-06-24
forum: Multimedia Software
---

### Post by ToppKatt on 2009-06-24
[SIZE=4]I have a Soundblaster Audigy card installed.
I finally got sound in Skype by useing CA01060 (hw:CA01060) which was one of my choises. However I don't have sound on my desktop for Music Player.
I have tried the commands Ispci | grep -iaudio and
Ismod | grep - isnd. Which come back with errors.

toppkatt001@OWNER-PC:~$ ispci | grep -iaudio
grep: unknown directories method
bash: ispci: command not found

Card is installed but receive <access denied> error
toppkatt001@OWNER-PC:~$ 

toppkatt001@OWNER-PC:~$ ismod | grep -isnd
grep: option requires an argument -- 'd'
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
bash: ismod: command not found
toppkatt001@OWNER-PC:~$ 

Any ideas just starting to learn this OS.







[/SIZE]

---

### Post by ToppKatt on 2009-06-24
[COLOR=Magenta][SIZE=4]A little more reading and found answer. So ignore first post. :KS[/SIZE][/COLOR]

---

### Post by SR_ELPIRATA on 2009-07-14
Out of curiosity, what did you read that helped you?

ELP

---

