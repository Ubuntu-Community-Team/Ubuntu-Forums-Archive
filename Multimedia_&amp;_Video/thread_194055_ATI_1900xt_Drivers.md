---
title: "ATI 1900xt Drivers?"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by Remirp on 2006-06-10
Been racking my brain trying to get ATI 1900xt drivers to work.  Every time I install them I reboot and get a blank black screen.  It is running but no screen.  Can anyone out there with a 1900 get their video card to work with Ubuntu 6.06 or are 1900 users stuck till ATI comes out with better linux drivers?

](*,)

---

### Post by campnic on 2006-06-11
[QUOTE=Remirp]Been racking my brain trying to get ATI 1900xt drivers to work.  Every time I install them I reboot and get a blank black screen.  It is running but no screen.  Can anyone out there with a 1900 get their video card to work with Ubuntu 6.06 or are 1900 users stuck till ATI comes out with better linux drivers?

](*,)[/QUOTE]

I have the exact same problem.  1800xt but every time the drivers install it just goes to a blank screen once i restart X.  I've spent a long time trying to figure out whats going on.  I think the driver might just be broken.  It says my card is "ATI Technologies: Unrecognized 7120" or something like that when i run "lspci | grep ATI".  I get the distinct impression that my card is unsupported (though the ATI site seems to suggest it is).  The other possibility might be that we are both on amd64 and that there is a bug with that architecture.  What say you?

---

### Post by campnic on 2006-06-11
A New Hope?  This is my exact problem and someone has proposed a solution...
[http://www.ubuntuforums.org/showthread.php?t=193116](http://www.ubuntuforums.org/showthread.php?t=193116)

I'm going to try, i'll be back afterwards to comment.

---

### Post by campnic on 2006-06-11
[QUOTE=fadeh]Hi,

i'm a brand new ubuntu member so i'm not so experienced with ubuntu to say: "let's do what i say, i know it's correct!" :) but i've passed the last few days fighting against fglrx, dri, xgl and so on. I've got an amd64 3500+, X1900XT and the solution i found for black screen freeze is to commend Load "extmod" in your /etc/X11/xorg.conf i dunno why but there'are incompatibilities with fglrx driver while using dri.


Bye,

fadeh[/QUOTE]

Wow, after i wasted 4 days, finally a solution.  I hope this helps.  It fixed all my problems, I'm now running a much, much faster desktop!!!  This should fix your stuck at black error, I just hope everyone thats having this problem reads this.

---

### Post by dbarron on 2006-06-11
That did the trick for me too...you can't believe how :-D HAPPY I am now!
Thanks
Danny

---

### Post by Remirp on 2006-06-11
cool, haven't tried that yet.  i'll try it tomorrow and post my results.  thanks for the reply!

---

### Post by Remirp on 2006-06-12
[QUOTE=Remirp]cool, haven't tried that yet.  i'll try it tomorrow and post my results.  thanks for the reply![/QUOTE]
awesome.  that worked.  I did the steps [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") then commented that Load out and works great.  Thanks!! :KS

---

