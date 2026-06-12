---
title: "XvidCap RecordMyScreen?"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by Coolprogram on 2008-04-02
Hey, i am really new to this forum, and linux. I am looking for a way to record my screen, so I have been looking around here, and I find that people say that XvidCap and RecordMyScreen are the best for recording my screen. The problem I have is downloading it. i have used sudo apt-get recordmyscreen, and I have downloaded xvidcap. I just cannot seem to figure out how to install it to my computer. Can someone please help me with this?
-Coolprogram

---

### Post by cor2y on 2008-04-02
Never heard of a RecordMyScreen but i have used xvidcap and RecordMyDesktop both found in synaptic with the universe repos enabled.
If XvidCap is installed look for it in Applications->Sound & Video
RecordMyDesktop requires a frontend if you do not wish to run it from the terminal so you have to install both RecordMyDesktop and gtk or kde-RecordMyDesktop
```

sudo apt-get install recordmydesktop gtk-recordmydesktop
```
If its ubuntu and
```
sudo apt-get install recordmydesktop kde-recordmydesktop
``` if its kubuntu and again that should be located in Applications->Sound & Video after the install in Ubuntu not to sure where it is in kubuntu since i don't use that.

---

### Post by Coolprogram on 2008-04-02
Thanks for the reply, I used the codes, but nothing worked... I keep getting E: Couldn't find package recordmydesktop any other help or advice?

---

### Post by cor2y on 2008-04-03
Enable the universal repos in Ubuntu.
Easy way System->Administration->Software Sources , and tick off the ones that have (universe) (multiberse) and maybe (restricted) if they are not ticked, let the list update then try the commands again.

---

### Post by Coolprogram on 2008-04-03
haha thnx man IT WORKS lol
-Coolprogram

---

### Post by cor2y on 2008-04-03
Glad i could help
Edit
And don't forget to add [Solved] to the title now that the problem is fixed

---

