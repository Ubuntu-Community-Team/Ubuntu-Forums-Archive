---
title: "hulu on 64bit flash - firefox on 32bit flash"
date: 2009-10-15
forum: Multimedia Software
---

### Post by afonteijn on 2009-10-15
Hulu has released a [linux version of the hulu desktop]("http://www.hulu.com/labs/hulu-desktop"). This is great news! I have a few problems though. I run ubuntu 9.10 64bit and hulu desktop only starts after a fresh restart. I found out that this is a flash problem in relation to any ubuntu 64bit version. (so not just 9.10 beta). The problem can be solved by removing 32bit flash and installing 64 bit flash, but 64bit flash does not work well with imeem.com.

So, my question: is there a way to let hulu desktop use 64 bit flash, while firefox will just continue using 32bit flash. In that way I'll get the best of both worlds.

I'm looking forward to your input!

---

### Post by truck87bp on 2009-10-16
Hulu messes up Flash for 9.10. If you access Hulu with Firefox 1st, you can watch vids at you tube, otherwise youtube won't work.

---

### Post by rifak on 2009-10-17
yes there is a way. download 32bit flash for firefox, then download 64 bit and save the libflashplayer.so file where ever you like.

then do:

```
gedit ~/.huludesktop
```

this will open hulu-desktop config file. towards the end of the file, you'll see where you can specify the location of the flashplayer...just point it to where the 64bit version is.

---

### Post by afonteijn on 2009-10-20
ego-sum-deus: Thanks for the tip! I haven't had time to try it yet, but I'll definitely will!

---

### Post by afonteijn on 2009-10-26
Just to let you all know. The solution works, hulu is now using 64 bit flash and firefox 32 bit flash. However, after I have started firefox and I try to start hulu it doesn't work. Maybe this is not a flash problem, or the 64 bit flash somehow conflicts with the 32 bit version. Either way, thanks for the help.

---

### Post by spesheled1 on 2011-07-22
Nice tip! It worked perfectly!

---

