---
title: "Make deb of save-for-web plugin for Gimp?"
date: 2008-01-10
forum: Multimedia Production
---

### Post by Sonja on 2008-01-10
I'm an Ubuntu n00b and would really like to have the functionality that this plugin provides ([http://registry.gimp.org/plugin?id=8799](http://registry.gimp.org/plugin?id=8799)), but i'm not up to speed on compiling it as it throws errors that the gimp ubuntu 7.10 comes with is not the right version.  Can somebody please make a deb of it?  if you search the forums for "gimp save for web" you'll see that this will certainly benefit other users.  i'm running on x86.

---

### Post by sparazza on 2008-04-11
up! It's my problem too!

---

### Post by gali98 on 2008-04-11
[http://w15.easy-share.com/1700108903.html](http://w15.easy-share.com/1700108903.html)

try this I used to checkinstall so I don't know if it will work for you. works for me.
P.s I'm sorry but this sight may show you a bad picture. Its the only site I could find that would work where I'm at.
Kory

---

### Post by Sonja on 2008-04-11
This is way too awesome!!! THANKS! <3 You win bonus points.

---

### Post by gali98 on 2008-04-11
lol I guess it worked...
I think your problem was that you didn't have gimp2.0-dev installed.
you had to run the autogen.sh first then do "make" and "sudo make install."
Just incase you want to compile it yourself... All the best
Kory

---

