---
title: "Phatch in command line mode"
date: 2010-06-19
forum: Multimedia Software
---

### Post by wannabegeek on 2010-06-19
Hi folks....

I installed Phatch today hoping to use it to reduce the file size of some pictures
I took for work.

I originally took the pics with 12 MP camera and now want to email them to a few people
as smaller files.

I found Phatch, but the docs under man phatch suck...

Would anyone mind sharing an example of how to make the above changes to a
directory of pics.  My guess is it starts: phatch -vkc --desktop [action] [path]

thank you,
wbg


EDIT: found this [http://photobatch.wikidot.com/server](http://photobatch.wikidot.com/server)

---

### Post by wannabegeek on 2010-06-19
figured out the gui

but the command line still didn't work yet... action test is scaling
```

phatch -ckv test  /media/Pics/pics

```

---

### Post by stani on 2010-06-20
You need first to make an actionlist with the gui and be sure that a save action is at the end. Test the actionlist first from the GUI (Tools>Execute).

To use it from the command line do:
```
phatch -cv test.phatch /media/Pics/pics
```

---

### Post by wannabegeek on 2010-06-20
thanks stani, I found that wiki and  realized that I still need to use GUI....still a cool program :)

will try CL again..

EDIT:
```

IOError: [Errno 2] No such file or directory: 'Scale12MPpic.phatch'

```

What dir should I be in to call patch with actions ?  I see that the actions are in:$ home/.local/share/phatch.actionslists
I tried calling the program from  /share

---

