---
title: "Flash player missing?"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Sentience on 2009-05-27
My flash player does not seem to be working. Whats worse, when I tried to reinstall common restricted packages something crashed, but I didnt get the name of it. It wasnt anything I knew I was using.

So I tried to reinstall macromedia flash with the command line and this is what I got.


jinn@anon-laptop:~$ sudo apt-get install flashplayer-mozilla
[sudo] password for jinn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplayer-mozilla has no installation candidate
jinn@anon-laptop:~$ 
jinn@anon-laptop:~$ 



I may have foolishly added random programs while I was messing around trying to get the right codecs together. Now I dont know what to add or remove.

---

### Post by Sentience on 2009-05-27
No ideas?

---

### Post by Hamchan on 2009-05-27
You could try poking around in synaptic and doing a search for flash to see what you have installed. When I had a problem with flash it turned out that I had several versions of flash players installed and had to get rid of one of them.

What version are you running, 32 bit or 64 bit?

---

### Post by AbdRahim on 2009-05-28
Answers may be found here;
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Sentience on 2009-05-28
I got rid of the non free adobe apt and it works perfectly now. Thank.

Maybe someday I wont be a noob anymore.

---

