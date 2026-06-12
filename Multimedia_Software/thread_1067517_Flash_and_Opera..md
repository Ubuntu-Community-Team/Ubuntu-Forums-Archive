---
title: "Flash and Opera."
date: 2009-02-11
forum: Multimedia Software
---

### Post by jwbrase on 2009-02-11
I was having problems with Firefox crashing all the time (I think I saw in an other thread that it had something to do with Flash plugins on 64 bit systems), and so I decided to try out Opera. I am now addicted to Opera.

The only problem is that, while Opera is stable, and while the browsing experience is great for most things in Ubuntu, and great for everything in Windows, I still can't get Flash to work properly. It hasn't sabotaged the browser, which it did with Firefox, and I do at least get sound, which I didn't in Firefox, but video is still a no-go in Ubuntu. My test run to see if Flash works consists of trying to watch Monty Python's Dead Parrot sketch on Youtube. When I do that in Opera, I get just a white blank space where the video is supposed to be (even the play/stop/volume controls are invisible), but the sound plays perfectly.

Any ideas?

---

### Post by wolfen69 on 2009-02-12
go [here]("http://get.adobe.com/flashplayer/") and download the tar.gz flash file. right click and do "extract here". inside the folder will be a file called libflashplayer.so (the one you need)

but first do in terminal:
```
gksudo nautilus
```
then navigate to the libflashplayer.so file and right click-copy. then while still in nautilus, navigate to /usr/lib/opera/plugins and paste it there. restart opera.

---

