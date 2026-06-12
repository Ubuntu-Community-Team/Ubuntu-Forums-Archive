---
title: "How to fix flash for processors missing sse2 (without using older versions of flash)"
date: 2013-12-03
forum: Multimedia Software
---

### Post by I.Bun.Tu on 2013-12-03
Let me start off by saying this is my first time posting a solution to a known problem, please let me know if I can add any more information or post this solution anywhere else on the web (or if this is even the best forum to post in). I am using Ubuntu 13.10 32-bit and have not tested the following solution in any other versions of Ubuntu.

So there is a known problem trying to use flash in Ubuntu (and I believe Linux in general) with older processors that lack sse2 support.

You can see if your processor has sse2 support by opening a terminal (ctrl+alt+t) and typing:

```
cat /proc/cpuinfo
```

and seeing if sse2 is listed under flags. You could also type into the terminal:

```
cat /proc/cpuinfo | grep flags
``` 

to list only the flags line of the cpuinfo file, or you could type:

```
cat /proc/cpuinfo | grep sse2
``` and see if you get any output.

If you are unable to play flash (YouTube videos for example) and your processor lacks the sse2 support, this is most likely your problem.

Scouring the net, there are proposed solutions to this problem that invole rolling back to older versions of flash that do not require sse2 (I believe 10.2 and earlier). It is also implied that such a version of flash is not readily available and that the problem lacks a simple solution. If anyone is successfully running flash on a CPU without sse2 by using an older version of flash, please post a link where we can download such a version of flash and include it in this solution.

I was living without flash on my old system until I came across this guide for playing Netflix in your browser in Linux without using Netflix Desktop: [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

It involves using Pipelight to play windows applications through firefox in linux as far as I understand. It allows you to use silverlight in your firefox browser normally (with the addition of a user agent switcher so netflix believes you are using firefox in windows, but this user agent switcher is not necessary to fix flash), but it also allows you to use the windows version of flash in firefox. Tada!(sp?) Flash works for CPUs without sse2 support in Linux.

All of the instructions are in the guide in the link but for the sake of posting a complete solution I will include instructions here for how to fix flash for CPUs missing sse2 without using an older version of flash.

First open a terminal (ctrl+alt+t) and add the dependencies, update and install pipelight:

```

sudo apt-add-repository ppa:ehoover/compholio
sudo apt-add-repository ppa:mqchael/pipelight
sudo apt-get update
sudo apt-get install pipelight-multi

```

Then all you need to do to get flash working is type into the terminal (with your browser closed preferably, but it worked for me with my browser running):

```
sudo pipelight-plugin --enable flash
```


I hope this helps anyone out there using an old CPU. I was insanely greatful to have happened upon this and even more grateful to the programmers who created Pipelight. Cheers. Enjoy yourselves everyone!

---

