---
title: "nsf file playback in natty"
date: 2011-10-18
forum: Multimedia Software
---

### Post by chimmy on 2011-10-18
Hi,
Just wondering if anyone knows of a program or plugin that will play nsf (nintendo sound files) and works in natty. I'm looking for something that can toggle channels on and off if at all possible.:-\"
Thanks:)

---

### Post by chimmy on 2011-10-19
ok, so I figured it out. Both nosefart and festalon do what I want them to. Neither of them work right after installing, but there's a simple fix as follows (at least it worked for me):

- Install alsa-oss

- Install or reinstall nosefart or festalon or both according to instructions (This seemed to need be done after installing alsa-oss. Otherwise the same problem persisted)

- Now, whenever you want to run the program, from the command line type aoss and then the command to run the program. It works like a charm!

e.g. from the folder where festalon is installed after your prompt you would type

aoss ./festalon *.nsf

where *.nsf is the path to the file you want to hear. 

If you're into figuring out what nintendo composers did to write their songs both of these programs have different strengths so they're both good to have. There's a GUI version of nosefart, but I haven't tried it yet.

Hope this helps.:-)

---

