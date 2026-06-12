---
title: "Software for video mixing"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by caveman56 on 2007-06-01
Hey all, working on a video project and need some advice.  Hopefully someone has a solution for me  :-)  I have two videos from different angles of my school's christmas concert.  I'm looking for a software solution to mix the two videos together.  Ideally I'd be able to load both videos, sync them up and cut back and forth between the two feeds.  I know hard ware solutions are available, but we don't have that kinda cash to invest in one.  If anyone knows of a piece of software that will do this, please drop me a line, I'd prefer an open source solution, but right now I'm willing to entertain just about anything,

thanks,

Dave

---

### Post by jamesjtucker on 2007-06-01
There are TONS of video editing apps out there, and even a few really good ones ;)
Heres a quick list in order of what i like  best:
Jakasha    [http://www.jahshaka.org/content/view/71/42/](http://www.jahshaka.org/content/view/71/42/)
Cinelerra   [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)
Kino          [http://kinodv.org/article/static/2](http://kinodv.org/article/static/2)

   I dont know if you would be able to sync them both up as you mention, but you may be able to strip the audio from one video,  edit the video together as desired and then lay the audio track back over the finished product.

---

### Post by mohnkern on 2007-06-01
another package, which is very easy to use is kdenlive.  

See -- [http://ubuntuforums.org/showthread.php?p=274076](http://ubuntuforums.org/showthread.php?p=274076)


If you've ever used Windows Movie Maker, this is similar, and good for a novice video editor.

---

### Post by cyber_bushi on 2007-07-07
If you want to use Jahshaka, you might want to do the following: (just tried it on feisty)

add the following line to your /etc/apt/sources.lst : 

deb [http://repo.jahshaka.org/ubuntu/dapper/](http://repo.jahshaka.org/ubuntu/dapper/) binary-i386/ 

then type on the console:

sudo apt-get install jahshaka

and you're done...

---

### Post by toddbmobile on 2007-08-03
I installed Jahshaka, but I get the splash screen for a second, and the error message from terminal.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

Any ideas how to fix this.

---

### Post by jamesjtucker on 2007-08-15
I hope youre still checking this thread. 

Where did you install it from? I think getdeb.net has a .deb for it

---

