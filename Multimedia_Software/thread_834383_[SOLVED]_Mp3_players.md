---
title: "[SOLVED] Mp3 players"
date: 2008-06-19
forum: Multimedia Software
---

### Post by Creasey on 2008-06-19
I have a sony mp3 player.  The player appears as "USB Drive" in Places, Computer. When I click to access it, the warning messages pops up: "Unable to mount location, Cannot mount file."  
Can anybody help me?  How do I get to the file system for drag and drop?
Thanks
Creasey

---

### Post by xc3RnbFO8P on 2008-06-19
I dont know if it works in Hardy, in Terminal:
> gconf-editor

Navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again.

---

### Post by cozmicharlie on 2008-06-19
Is it a Walkman?

This might work for you:

Install pmount: 
```
sudo apt-get install pmount 
```

and then: 
```
pmount /dev/sdxx WALKMAN
```

For sdxx use whatever the device is showing up as in your system.  To find out type or cut and paste:
```
ls /dev/disk/by-label -lah
```

---

### Post by Creasey on 2008-06-20
cheers cozmicharlie, magic all works fine Brill
Creasey

---

### Post by cozmicharlie on 2008-06-20
Excellent - please mark this solved.

---

### Post by WorldPax on 2008-06-22
I attempted this fix, because I have had the exact same issue since upgrading. This is what I get when I attempt stage 2 of the fix.

pax@pax-laptop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2008-06-22 17:14 .
drwxr-xr-x 6 root root 120 2008-06-22 17:14 ..
lrwxrwxrwx 1 root root  10 2008-06-22 17:14 WALKMAN -> ../../sdb1
pax@pax-laptop:~$ pmount /dev/WALKMAN
Error: device /dev/WALKMAN does not exist


any help would be appreciated, I have some new songs I'd like to take with me :guitar:

---

### Post by WorldPax on 2008-06-27
5 days and no help, glad I wasn't drowning. Seriously though, I'm guessing this is a problem due to my ignorance, someone please show me the way.

---

### Post by puggers on 2008-07-05
I stumbled accross this thread on google looking for some something else, but it seems a shame no one replied to you. 

```
pax@pax-laptop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 60 2008-06-22 17:14 .
drwxr-xr-x 6 root root 120 2008-06-22 17:14 ..
lrwxrwxrwx 1 root root 10 2008-06-22 17:14 WALKMAN -> ../../sdb1
```

From the last line here we can see that WALKMAN is at sdb1; so instead of: ```
pmount /dev/WALKMAN
```

You need: 
```
pmount /dev/sdb1 WALKMAN
```

Then it should mount fine.

---

### Post by valmorel on 2008-09-07
WorldPax............ I just came across this thread. Are you or anyone else reading this still having problems automounting (not using terminal) Walkman in Hardy Herron? If so, ping this thread and I will post fix.

---

### Post by DLF44 on 2008-10-13
i have a sony Mp3 player that is doing the same thing. it says wont mount.

im very new to ubuntu and dont know much about computers or code. where are you supposed to enter all of this code to make the mp3 player work?

I also have the same problem with a sony memory stick duo, only this doesnt even show up.

any help?

---

### Post by valmorel on 2008-10-14
DLF44, which version of Ubuntu are you using? I am guessing Hardy Heron 8.04 32 bit?

---

### Post by DLF44 on 2008-10-18
yup thats the one

---

### Post by valmorel on 2008-10-18
OK. Well, the first thing to do, is to check to see if your computer can run the 64bit version of Ubuntu by downloading the 'live CD' immage, and checking to see if it will boot up. I say this because these problems dont exist in that version, and it is usually beneficial to use the 64 bit version if you can.............

---

### Post by DLF44 on 2008-10-18
sorry i missed the bit part of the question.

how do i  check wheather i have 32 or 64?

---

### Post by valmorel on 2008-10-18
The simplest and surest way is to download a 64bit live CD image from the Ubuntu site here   [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  On this page you will see the options you need to download a 64 bit version of Ubuntu. Download the file, and then just burn it to a CD. You can do this in Windows if you find it easier, then just see if your PC can boot normally from the CD. If it can, 64 bit works for you, and that is probably the version of Ubuntu you should be using.
However, there is another thing to consider........ in order for any of this to work, you must have one of the later versions of Walkman that support drag and drop in Windows File Manager, and compatibility with Windows Media Player. If your Walkman only works with Sony Sonic Stage, you may be stuffed.
IF your Walkman is compatibile (drag and drop/MTP enabled), you might also consider simply downloading Gnomad2 from the official repositories using your software manager. This little program is fast and easy to use, and will save you dicking around with system settings. If you are unsure how to install it, just ask. It takes about twenty seconds to get it. Super program..........

---

### Post by DLF44 on 2008-10-20
alright thanx a lot for your help. much appreciated.

---

### Post by DLF44 on 2008-12-07
hey i got the 64bit version. and i got gnomad2, but still cannot figure things out with my mp3player?

---

