---
title: "Huawei E270 USB Modem help!!!"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by Ruanej90 on 2010-04-17
Ok guys....I am new to this Forum and new to Ubuntu....

I recently received my Ubuntu 9.10 CD, Kubuntu 9.10CD and Server Edition.
I was recommended to do so by a friend because my computer Running on Windows Vista Home Basic with 512MB RAM has been extremely, unbearably slow for the last month or so....
I got the CD's yesterday and i Ran the Ubuntu CD and everything was fine, i rebooted the Computer and it started up! It was great!! Really quick and responsive and easy to use and i LOVE it's features...
My only problem is my Broadband:(...I live in Ireland and i have my broadband with o2 ([www.o2.ie](www.o2.ie)) it's quick and sufficient for my needs. I have a Huawei E270 usb modem (It's wireless broadband)
And it wouldn't Work.... i plugged it into my pc with Ubuntu up and running and it opened the File for o2 rather than the Interface for it....When i plugged th modem in there was a green lock symbol on the top right of the screen if that helps...Is Ubuntu even compatible with the E270 modem?:confused:
Any help to get it going? Because once this works i am deleting Windows and using Ubuntu on it's own.
Joe.

---

### Post by Ruanej90 on 2010-04-17
BuMp...

---

### Post by GeorgeVita on 2010-04-17
Hi **Ruanej90**, welcome to this forum!

Ubuntu 9.10 LiveCD version comes with [bug#446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") affecting many 3g modems. This bug fixed with the next kernel, so you must update your system using any other connection (ethernet, wifi) and retry.

After update if you still have problems, post here to try other tests.

Regards,
George

---

### Post by Ruanej90 on 2010-04-17
Thanks George!! :)
I got my modem to work but now i am having Connection difficuties with FireFox Web Browser :( It's saying i am not allowed to connect to the internet and that it vcannot access some sort of serve ?? 
Any ideas on this new problem?

---

### Post by GeorgeVita on 2010-04-17
> **Ruanej90 said:**
> ...now i am having Connection difficuties with FireFox Web Browser :( It's saying i am not allowed to connect to the internet and that it vcannot access some sort of serve ?? 
Any ideas on this new problem?
Some problems occur due to bad DNS setup. Disconnect, wait, connect again to check if resumes. 
Finally check network-manager settings:
right click icon, edit connections, mobile broadband, click provider, edit, IPv4 Settings > Automatic (PPP)

You can also compare these settings with other users of the same provider.

Other check is to 'ping' some known web-pages from terminal:
```
ping www.canonical.com
```
Read a similar thread: [http://ubuntuforums.org/showthread.php?t=1379094](http://ubuntuforums.org/showthread.php?t=1379094)

Regards,
George

---

### Post by Ruanej90 on 2010-04-19
ok i got it working this morning......came home and it's not working anymore.......i was browsing the net !!!!!....and no its saying that server cant connect crap again :(:confused:

---

### Post by spiky001 on 2010-04-19
can you connect now

---

### Post by Ruanej90 on 2010-04-19
Yes i can.
Also when i try to edit my network connections it asks me for password identification....and when i fill it in it says i dont have the 'Priveliges' and it wont let me edit my connection settings :(

---

### Post by spiky001 on 2010-04-19
that should be your root password make sure caps is not on

---

### Post by Ruanej90 on 2010-04-19
Root Password....? You mean the one i logon with?
Lets say it's AAA,
When i type in AAA, it still doesn't work...I also tried the connection password lets say... BBB, typing in BBB doesn't work either *Shrugs*
Im gonna install Kubuntu and see if that works:lolflag:

Also i dont know what this means exactly...but when im running Vista...like now my Pc makes a really loud racket constantly and when i run Ubuntu there is no noise.....any ideas on this?:confused:
P.s thanks for the help you two !!:)

---

### Post by Ruanej90 on 2010-04-21
Gotta BuMp it up!!!!!!!!

---

### Post by Ruanej90 on 2010-04-21
And again, nobody??

---

### Post by pdc on 2010-04-22
so what happened to this

> Im gonna install Kubuntu and see if that works

and this ? hardware issue?

> but when im running Vista...like now my Pc makes a really loud racket constantly and when i run Ubuntu there is no noise.....any ideas on this?

and you seemed to have problems here ........

> Root Password....? You mean the one i logon with?

so it would help you to grasp a few linux principles ....

..... we all function as ordinary users .....

....... ie you can't change the date on your computer unless you assume 
"adminstrative privileges"; *sort of stops you putting your fingers into the light switch when the power is on* .....

so to change the lightbulb the computer insists you have administrative powers; (not the ordinary mess-around function of everyday)

have a read at this

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

it's not a huge bundle of fun, but you might have a few laughs ..

and read this too

[http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/](http://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/)

this is the like the sort of reading you do before the driving test .......

---

### Post by Ruanej90 on 2010-04-25
Installed Kubuntu working fine
Dunno if thats a problem or not but the sound it makes on vista over ubuntu is weird.....
Read the links PDC....:lolflag:
Also i have now fixed the problem...dont know how but i did!!
Can anyone shed light on why this computer is so loud??:confused:

---

### Post by pdc on 2010-04-26
> Also i have now fixed the problem

well done Ruanej90; you're a genius

> *why this computer is so loud*

shedding light on it might just make it even hotter ......

......... go on; we can't keep on guessing: tell us what you mean

---

### Post by Ruanej90 on 2010-04-28
loving the sarcasm there dude....what i mean is this computer is Uber ****ing loud when i am running Vista...making odd sounds i cannot expain.....and there is little/no sound when i run on Ubuntu.....Yes i am a genius thanks for realising.

---

