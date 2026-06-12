---
title: "Beryl Installation Gone WAY wrong"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by kornpopz on 2007-07-05
Hey everybody, I'm a fairly new Linux user and ever since I've gotten Ubuntu, I've played around with it but it has never crashed on me. Until now. Last night I tried installing Beryl and after many "how to's" that asked me to change system text entries and whatnot, I think I messed up my X Server. Now whenever I start, it displays the Ubuntu splash screen but then goes to a console and says 

"Failed to start the x server (your graphical interface)  It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <Yes> <No>".

I have an old ATI all in wonder Rage Pro 128 card that was woorking perfectly fine up until i tried installing beryl.....what to do i now? 

Here is the screen I get after pressing "Yes" on the above error: 

[[IMG]http://img441.imageshack.us/img441/9761/hpim0969um9.th.png[/IMG]](http://img441.imageshack.us/my.php?image=hpim0969um9.png)

[[IMG]http://img523.imageshack.us/img523/5272/hpim0971cl6.th.png[/IMG]](http://img523.imageshack.us/my.php?image=hpim0971cl6.png)

:D

---

### Post by tgm4883 on 2007-07-05
ctrl-alt-f1 to get to command line

From the command line do sudo dpkg-reconfigure xorg

Why are you installing the discontinued beryl and not compiz fusion?

---

### Post by kornpopz on 2007-07-05
> **tgm4883 said:**
> ctrl-alt-f1 to get to command line

From the command line do sudo dpkg-reconfigure xorg

Why are you installing the discontinued beryl and not compiz fusion?

When I typed that in and pressed enter it basically just ignored it and started a new command line...no error msg/acknowledgement, just a pause before a new line where i can type in something.

Never heard of Compiz Fusion, but now that i googled it, I think I just may give it a try on my inspiron 640m w/ ubuntu as well....

as for the problem, its still there, any other suggestions?

---

### Post by tgm4883 on 2007-07-05
> **kornpopz said:**
> When I typed that in and pressed enter it basically just ignored it and started a new command line...no error msg/acknowledgement, just a pause before a new line where i can type in something.

Never heard of Compiz Fusion, but now that i googled it, I think I just may give it a try on my inspiron 640m w/ ubuntu as well....

as for the problem, its still there, any other suggestions?

Arg, thats cause I typed it in wrong.  It's 

sudo dpkg-reconfigure xserver-xorg

And compiz fusion is the remerge of compiz and beryl

---

### Post by kornpopz on 2007-07-05
> **tgm4883 said:**
> Arg, thats cause I typed it in wrong.  It's 

sudo dpkg-reconfigure xserver-xorg

And compiz fusion is the remerge of compiz and beryl

bah, i got all excited it would work after it led me though a bunch of setup screens, but to no avail. :(

Is there any way to "repair" the installation of Ubuntu fiesty fawn as one is able to do w/ Windows XP?

---

### Post by zero244 on 2007-07-05
Hey bro weve all been there.........and probably will been there again at some point.
Ive been struggling to get beryl to run stable for months. I wont go into the details but I finally got there. So it can be done.
It takes time to understand Linux in relation to your hardware. 
Just keep plugging away you will eventually get there.

---

### Post by kornpopz on 2007-07-08
> **tgm4883 said:**
> Arg, thats cause I typed it in wrong.  It's 

sudo dpkg-reconfigure xserver-xorg

And compiz fusion is the remerge of compiz and beryl

Thanks tgm, it worked like a charm the second try. I really appreciate it :).

---

