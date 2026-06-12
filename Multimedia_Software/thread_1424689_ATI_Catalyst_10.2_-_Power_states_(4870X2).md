---
title: "ATI Catalyst 10.2 - Power states (4870X2)"
date: 2010-03-08
forum: Multimedia Software
---

### Post by shockandawe on 2010-03-08
My video card runs hotter in Ubuntu 9.10 than in Windows.

This is because it is always set to 3D powerstate. In Windows it is always set to 2D powerstate, and it will switch to 3D once a 3D application is launched (like a game).

I've tried the command:

>aticonfig --set-powerstate=1

but I get this error:

>aticonfig: unrecognized option '--set-powerstate=1'
>aticonfig: parsing the command-line failed.

How can I get his command working?! Or is there a workaround I can use? 

This is driving me nuts. My card is sitting very hot for no reason. 


Cheers.

---

