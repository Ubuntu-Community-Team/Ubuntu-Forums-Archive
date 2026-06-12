---
title: "Streaming video in a class-room"
date: 2013-12-05
forum: Multimedia Software
---

### Post by surfstyle78 on 2013-12-05
Hi I'm searching a solution for a problem in a school class-room.
In this room I have lots of pc, and one is a master for the teacher. He want to use a webcam-hd to record what is making on his desktop. The video then is streamed to the others pc.

I'm searching a solution that I can adapt in a school, better if I can work with compressed hd video

thanks
mark

---

### Post by Kirboosy on 2013-12-05
I used to be a volunteer system administrator for a highschool and I set them up with [iTalc]("http://italc.sourceforge.net/"). They absolutely loved it and it has the feature of displaying one screen on all the computers. you can also monitor what the children are doing without walking around behind them. 

The package is available in the repositories. There are actually two packages. Client (for the students) and Master (teacher or administrators)

On the student box
```
sudo apt-get install italc-client
```
On the Teacher box
```
sudo apt-get install italc-master
```

If he wants to make a video of what he is doing on the computer he can use "Recordmydesktop" to capture his screen

Hope that helps!
~Caboose

---

### Post by surfstyle78 on 2013-12-05
thanks, I tried iTalc that it's a very interesting software.... but from version 2.0 there are many troubles with 7...
and video streaming is poor and I'm searching good quality (better HD stream)...

---

### Post by Kirboosy on 2013-12-05
I don't know if there is anything else out there besides iTalc for free. Unfortunately iTalc has turned into a dead project. I found an alternate called [Schoolvue]("http://www.crosstecsoftware.com/index.php?option=com_content&view=article&id=65&Itemid=7") but its not free. 

If you play with the streaming settings in iTalc you should be able to get it too look a lot better.

---

