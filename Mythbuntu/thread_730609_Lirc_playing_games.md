---
title: "Lirc playing games"
date: 2008-03-21
forum: Mythbuntu
---

### Post by KillerKiwi on 2008-03-21
I want to be able to play frozen bubble and super tux with my remote!!

Sounds simple... only it isn't there is an app called irxevent but it wont work with SDL games....

Turns out there is a way using irxkeys
[http://frodo.dyn.gno.org/~brettk/irxkeys](http://frodo.dyn.gno.org/~brettk/irxkeys)
This small c app uses XTestFakeKeyEvent
Note it needs a  small fix to make it work on ubuntu

This works but is not that playable as the onkeyup is fired after a small delay... I really need it to fire if irc stops receiving codes or gets a new different code... else tux runs with a stutter

So any one out there know enough c to make a timer?

I could do this in python but I dont have enough c skills to pull it off.... I might try a proof of concept in python though

Python sendkeys
[http://wwwx.cs.unc.edu/~gb/wp/blog/2007/11/16/sending-key-events-to-pygame-programs/](http://wwwx.cs.unc.edu/~gb/wp/blog/2007/11/16/sending-key-events-to-pygame-programs/)

Later

---

### Post by 12growon on 2008-09-03
I know it's a tad late to leech on this post, but irxkeys is killing me, what's the "small fix" for Ubuntu?  I've been trying to compile it on Hardy32 for 3 days, but keep getting "undefined reference to : "XopenDisplay", and such.  Is there another LDFLAG to add to the make?

---

### Post by KillerKiwi on 2008-09-03
have a look here

[https://jkeys.googlecode.com/](https://jkeys.googlecode.com/)

its all python, im using it for my joystick and remote

---

