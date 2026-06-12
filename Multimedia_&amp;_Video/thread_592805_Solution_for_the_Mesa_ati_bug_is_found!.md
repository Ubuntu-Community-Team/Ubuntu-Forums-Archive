---
title: "Solution for the Mesa ati bug is found!"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by ASPCartman on 2007-10-26
Hi. So i had a bug with fglrx driver. My fglrxinfo showed me that i have mesa driver installed. So, after few hours, i was going to throw me ati card into a window but i found a way to fix it!

So. We already installed all as it said in here:
[http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)

And now open console and copy/paste all to there:
```

sudo apt-get remove fglrx-*
```

Answer y.

Then u go to

[http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)

And do ALL (GODDAMIT!) as it said there 

And the main part: There is a lot of dummies like me. So here is real problem:

```

8. Compile kernel module

sudo m-a prepare,update

sudo m-a build,install fglrx-kernel

sudo depmod
```

Most of people just copy pasted all this into console.... guys dont u see that all this i wrote in different lines!?
So for megadummes - copy/past this all into console and push small button called "Enter" (I hope u was able to find it before) one time by one.

```
sudo m-a prepare,update
```
```
sudo m-a build,install fglrx-kernel
```
```
sudo depmod -ae
```

And now continue the guide as it said there

[http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)

So i hope that all this that i had writed here was helpful for some of u. Worked for me.

PS
WTF? My build-in nvidia 6150 works better then ATI Spphire x1800GTO2 512!


[RIGHT]***ASPCartman*** :lolflag: [/RIGHT]

---

