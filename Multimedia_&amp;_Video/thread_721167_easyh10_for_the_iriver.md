---
title: "easyh10 for the iriver"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by kiisu on 2008-03-11
Hey, I know this program has been mentioned and asked about a few times here but nothing too recent and mostly installation instructions.

I downloaded easyh10 from the repo's and its supposedly installed but I can't bring up any gui for it, when I type easyh10 as a run command nothing happens. But its definitely installed. I thought maybe it wouldnt work until I had my iriver plugged in but that did nothing.

My computer recognizes my mp3 player fine and I can put music on to it. I just need this application to work to properly index my music files. Please can someone help me out with this?

---

### Post by kiisu on 2008-03-12
Perhaps even someone unfamiliar with iriver & easyh10 can help me with this?

Its puzzling me because its definitely on my computer:

> kvm@kvm-laptop:~$ sudo apt-get install easyh10
[sudo] password for kvm:
Reading package lists... Done
Building dependency tree
Reading state information... Done
easyh10 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kvm@kvm-laptop:~$


But when I pull up a run command box and type 'easyh10' nothing happens ... the box disappears but the program is not opened

---

### Post by Rhubarb on 2008-03-12
Here's the website: [http://easyh10.sourceforge.net/](http://easyh10.sourceforge.net/)

If you type in:
```
man easyh10
```
You get a nice manual how to use the application.
If you scroll down, you'll see all the switches you can use, and right down at the bottom there are some examples of usage.

---

### Post by kiisu on 2008-03-13
Yes, I see now that I need to specify the player model:

> EasyH10 [CUI] 1.5  Copyright (c) 2005-2006 by Nyaochi

ERROR: H10 model template must be specified.
kvm@kvm-laptop:/usr/share/easyh10/model$

Still pretty much a noob with linux and having trouble accomplishing that ... the directions at sourceforge tell me how to copy the model template to the root of the device, but I get an error message doing this and thats where I get lost.

---

### Post by Rhubarb on 2008-03-14
I can't help you that much more, namely because I don't have a supported iriver player that I can use to test it out with.
But I'll try anyway :)

Firstly, make sure your iriver is plugged in, and that you can freely browse it within ubuntu.
Go into a terminal, type in:
```
cd /media/
ls
```
This will give you a listing of the name your iriver is mounted under.  - It's probably "disk"
If it is "disk", then change into that directory:
```
cd disk
```

This is where I'm not so sure, so I could be very wrong here:
You need to install the model template to the iriver, get the model of your iriver and substitute that for **MODEL** here:
```
easyh10 --install-model --model=**MODEL**
```

Now once that's done, it's time to index your files (create a database for it):
```
easyh10 --construct /media/disk
```

If you've just updated a few songs, it's probably faster to just update your database (do this after you've created the database, and after you've added / deleted some music):
```
easyh10 --update /media/disk
```

I hope this actually works for you, as said previously I don't have a compatible iriver player to test this out on.


If you can, try to get a little more familiar with the command line, once you learn it, it is often quite simple to run command line only applications like easyh10, just by reading the syntax in the man page.
```
man easyh10
```

---

### Post by kiisu on 2008-03-16
Thanks Rhubarb. I am getting better and better with command line interface but it takes time, I have absolutely no background in computers and jumped into Linux without any friends to help me out. The community forums are all I've got so I especially appreciate you helping out on something you dont even have personal experience with.
I'll give your suggestions a shot and report back.

---

### Post by kiisu on 2008-03-16
Hats off to you, its working. Now I just need to delete this horrible Rockbox firmware I loaded on to it a while back ....

---

### Post by Rhubarb on 2008-03-19
Wow good to hear kiisu, keep up the learning there, as I have learned mostly everything I know about Linuxy stuff from these forums and general internet searches too.  :)

---

### Post by kiisu on 2008-03-20
Only thing I should have added :

At the point where Rhubarb dictated how to specify the iriver model, i needed to specify the path afterwards, so, my full command was:
easyh10 --install-model --model=MODEL /media/H10

(in my case it was /media/H10 - in another it could be different)

---

### Post by protenniser on 2008-04-04
Hi all,

I know this thread is a little old however I'll try my luck :D
I have an H10 (i-river), and I try to use the easyh10 package in order to manipulate this device.
I installed easyh10 from repository however when I try to run it, I get this:
```

kmuslu@kmuslu-laptop:/media$ easyh10 
EasyH10 [CUI] 1.5  Copyright (c) 2005-2006 by Nyaochi

ERROR: H10 model template is not found.

```

I think this error is different than the one that is mentioned in this page.Any help will be appreciated, thanks...

---

