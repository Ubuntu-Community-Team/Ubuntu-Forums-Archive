---
title: "RealPlayer"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Hoom@n on 2008-02-04
Hello!
I downloaded RealPlayer10GOLD.bin from [http://www.real.com/linux](http://www.real.com/linux) but I couldn't install it:
```
hooman@hooman-laptop:~/Downloads$ sh RealPlayer10Gold.bin
sh: Can't open RealPlayer10Gold.bin

```
So I used apt-get, but I got:
```
hooman@hooman-laptop:~$ sudo apt-get install realplay
[sudo] password for hooman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay

```
What should I do and how can I install it?
Thanks.

---

### Post by ron999 on 2008-02-04
Hi
In the past I have had problems trying to install Real Player.
So last time I installed it using Automatix.

---

### Post by Hoom@n on 2008-02-05
Sorry! I got almost nothing! What should I do to install real player?
Thanks.

---

### Post by Cantabile on 2008-02-05
Hi

I just installed realplayer without a problem. The bin file you downloaded is executable, so you should first   make it so by: 

chmod +x RealPlayer10GOLD.bin

then all you need is:

./RealPlayer10GOLD.bin

and follow the instruction on screen. Hope this helps.

---

### Post by Hoom@n on 2008-02-05
Thank you, but:
```
hooman@hooman-laptop:~$ cd Downloads
hooman@hooman-laptop:~/Downloads$ sudo chmod a+x RealPlayer10GOLD.bin
[sudo] password for hooman:
hooman@hooman-laptop:~/Downloads$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
hooman@hooman-laptop:~/Downloads$ 

```

---

### Post by PmDematagoda on 2008-02-05
This thread is a duplicate of:-

[http://ubuntuforums.org/showthread.php?p=4273737#post4273737](http://ubuntuforums.org/showthread.php?p=4273737#post4273737)

---

