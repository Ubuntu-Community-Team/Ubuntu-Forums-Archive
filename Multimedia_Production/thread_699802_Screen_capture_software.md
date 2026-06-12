---
title: "Screen capture software"
date: 2008-02-17
forum: Multimedia Production
---

### Post by hamzamusa on 2008-02-17
For My Seminars i need an interactive demonstration : so i needed to capture my active live screen to video files ,. somehow i manage to install :
[LIST=1]
[*]istanbul 0.2.2
[*]gtk-Record My Desktop
[/LIST]

However they both record my vedio sessions in  OGG files , which i can't play , so i installed the xine , and still can't play them .

I have 3 Questions :

1- How to Play OGG files ?

2-How to Convert Them to other video extensions ?

3- Is there any other software that record my live sessions to video files ?

Hamza

---

### Post by arkara on 2008-02-17
are you sure that you cant play them?? ogg can be played by default in all linux distributions

---

### Post by Crafty Kisses on 2008-02-17
If the output is in ogg video format you can convert it to avi by mencoder.

Example:

```
mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi
```

You would have to install mencoder first though.

---

### Post by hamzamusa on 2008-02-17
Araka : no i can't Play ogg files with the defualt or even with the xine codecs .

Codename : I Installed the " mencoder " 

also i successfully convert the ogg file  to avi , but also got the same problem as ogg , : When it start working the player ( every player i have ) close ...

P.s : Both of the ogg and avi files got a video thumbnail of what's inside them .

---

### Post by Crafty Kisses on 2008-02-17
> **hamzamusa said:**
> Araka : no i can't Play ogg files with the defualt or even with the xine codecs .

Codename : I Installed the " mencoder " 

also i successfully convert the ogg file  to avi , but also got the same problem as ogg , : When it start working the player ( every player i have ) close ...

P.s : Both of the ogg and avi files got a video thumbnail of what's inside them .

Hmmm, do you have all your codecs installed?

---

### Post by Creative2 on 2008-02-18
plz see install codec and etc to covert file in every formats :) look at my signature

---

### Post by eye208 on 2008-02-18
> **hamzamusa said:**
> When it start working the player ( every player i have ) close ...
You have desktop effects enabled. Your media player crashes while trying to activate the XVideo overlay. This is a well-known problem.

Solution: Turn off desktop effects or switch your player to X11 output. Search the forums, this topic has been discussed numerous times.

---

