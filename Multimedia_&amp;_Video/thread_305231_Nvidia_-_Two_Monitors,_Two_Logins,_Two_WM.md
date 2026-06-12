---
title: "Nvidia - Two Monitors, Two Logins, Two WM?"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by befuddled on 2006-11-23
Hi,

I'm sure this must be possible, but I'm not really having much success.
I've got an Nvidia card set up, two monitors happily outputting - one from dvi, one vga on my Edgy box.
As it stands, the 'login' box only comes up on one monitor, and when logged in, the second display 'latches on' and becomes secondary display for that login.

What I would really like would be to have 2 separate logins, so my two monitors could basically be considered separate terminals (though sharing mouse/kb would be nice).

I have heard tales of people with multiple separate window managers (fluxbox, openbox etc) set up on their separate monitors to enable gaming fanciness etc...and this would imply something may be possible?

One of the main reasons I would like this is to enable one of the screens to be a remote xdmcp login to another box, though that should be incidental if 2 separate instances of the login manager can be spawned concurrently.

Other things that have been bandied around are (just to get them out of the way):

1) why not use vnc fullscreen on display :0.1
Because I don't want to use vnc, primarily so I don't have X running on the remote box constantly, but for other reasons as well, such as I don't like vnc :-D 

2) ability to do multiple sessions and switch via ctrl-f7 / f8 fn...
I also just don't want this solution, for practical reasons (it's annoying)

So. Any thoughts? I know other people have been looking for this solution too, but I'm yet to have found an answer after much searching ](*,) 

Any help on this would be much appreciated,

befuddled

---

### Post by steveoPatterson on 2006-11-23
i been looking for the same. searched for threads and other people are also looking tho noone has answers.

[http://ubuntuforums.org/showthread.php?t=252511]("http://ubuntuforums.org/showthread.php?t=252511")
[http://ubuntuforums.org/showthread.php?t=125809]("http://ubuntuforums.org/showthread.php?t=125809")
[http://ubuntuforums.org/showthread.php?t=153263]("http://ubuntuforums.org/showthread.php?t=153263")

be awesome if someone could fix this cos my mtyhtv setup needs it bad.

---

### Post by timfelgentreff on 2006-11-23
Hey,
there's a fairly easy way to do it.
[http://userful.com/products/free-2-user](http://userful.com/products/free-2-user)
They modified parts of gnome, gdm, xorg and some system-stuff (esp. pci). It comes with an easy setup tool.
What it does is to provide the possibility of 2 users on 2 screens with 2 mice and 2 keyboards to work on the same machine. The only thing that doesn't seem to work with this setup is 3D-accel (though that might have changed, been a while since I tried it, pre-Ubuntu times;). However, everything ordinary works fine. I was even able to play FreeCraft in multiplayer mode against my neighbour :)
HF

---

### Post by angel6700 on 2006-11-23
Hello,

you should also think about the possibility of acquiring one old pc; a you just need  a hard disk min. 1 Gb. a video card and a network card, and use it as X terminal. that is what I do at home.

---

