---
title: "Ok don't shoot me if this has been asked already but..."
date: 2008-05-29
forum: Multimedia Software
---

### Post by joexboxer on 2008-05-29
I am running UBUNTU & I have a JVC camcorder that has a 30 gig HD. I can view the movies (they are .MOD) just fine - however I want to make a DVD to watch on my DVD player and I cannot find a program to make one? I am pretty quick, however this operating system is like greek to me so I don't know if i am missing something? I wouldnt have a problem making a DVD from my own video files if I had Windows - and I tried Wine to import the JVC program but that didn't really work out right. I am pretty frustrated on this. I find I can burn ISO images and make data DVD's but I want to make my own dvd's. any help appreciated and this system is totally odd to me so please really slow step by step instructions. I am sorry if this has been asked before but all i find is info on copying dvd's and thats not what I am after.
Any help greatly appreciated.
thanks
Joe:popcorn:

---

### Post by pytheas22 on 2008-05-29
Tovid is a nice program for creating video DVDs in Linux.  To get the most out of it you should use the command-line, but it has a nice GUI too.  Take a look at [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page).  I'm a bit pressed now but if you have more questions I can answer later.

---

### Post by joexboxer on 2008-05-29
I appreciate it, I am having some trouble with this because i have to install it in so many pieces and .. i dont know. I keep getting permissions errors saying i dont have rights to certain drives... i added the Sabayon User Profile Editor and I think its blocking me from certain area's of the HD now. fun fun fun.
I'll get it... sooner or later...:confused:

thanks again!

---

### Post by pytheas22 on 2008-05-29
> I am having some trouble with this because i have to install it in so many pieces

Sorry, I should have mentioned this earlier, but you can install tovid very easily with this command:
```

sudo apt-get install tovid tovidgui
```

or, if you prefer a graphical interface, open Synaptic Package Manager (under System>Administration) and search for 'tovid.'

The directions on the tovid website are for compiling from source, but you rarely should have to do that when installing software.  Most software has already been compiled and placed in the Ubuntu repositories, which are one of the most convenient things about Linux once you get used to them.  You can always install from source if you want, but there's rarely a need to and if you're new to Linux, it's not easy.

---

### Post by joexboxer on 2008-05-31
ahhh yes very awesome thank you so very much!!!!!!

---

