---
title: "Menubar won't show in Audacity"
date: 2010-10-12
forum: Multimedia Software
---

### Post by compiz addict on 2010-10-12
Audacity doesn't have a menu bar anymore!
It doesn't even have that narrow space where a menu bar would be!

My problem doesn't have anything to do with Gnome's menubars as far as I can tell, but I even tried removing and reinstalling Audacity.

I even used --purge!

Anyone know how to fix this?

---

### Post by compiz addict on 2010-10-12
3pic bump

---

### Post by skompier on 2010-10-16
I had the same problem. I found that if I change the theme and then change it back...then the menu shows up. Weird.

---

### Post by bigsmitty64 on 2010-10-17
This is quite annoying! Can't do anything with it! Changing themes didn't work for me. :(

---

### Post by skompier on 2010-10-18
> **bigsmitty64 said:**
> This is quite annoying! Can't do anything with it! Changing themes didn't work for me. :(

I've found that this isn't a permanent fix. Leave Audacity open while you click on different themes and see what happens. This appears to only be an Audacity issue thus far.

---

### Post by bigsmitty64 on 2010-10-19
I have one "workaround" thats workin for me, but it's not something everyone will want to do. I have "Ubuntu Netbook Edition" installed on my desktop. When I log on to  that, the global menu shows audacitys menu. Like I said, not for everyone, and definately not a fix, but at least I can use audacity again until its fixed.

---

### Post by sanderd17 on 2010-10-21
could this be related to the use of the globalmenu? Who of you have/had installed unity or just the globalmenu? I had in any case.

I have the problem too, and the problem was mentionned on this thread: [http://ubuntuforums.org/showthread.php?p=10005355]("http://ubuntuforums.org/showthread.php?p=10005355")

---

### Post by sanderd17 on 2010-10-21
audacity and golly both work without problems from the live CD, but they don't work on my installation. I removed all the packages with "netbook" or "unity" in it, and still it doesn't work. Could someone try to pruge them instead of removing?

---

### Post by sanderd17 on 2010-10-21
I found a bug for it on launchpad: [https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/660314]("https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/660314")

And the sollution is to execute
```

export UBUNTU_MENUPROXY=0
audacity

```

note, this only works temporarilly, if the terminal is closed and you want to execute audacity, its w/o menu's.

To make this a permanent hack: do the following:
```

sudo mv /usr/bin/audacity /usr/bin/prog-audacity
gksudo gedit /usr/bin/audacity 

```

in gedit, type the text
```

#! /bin/bash


export UBUNTU_MENUPROXY=0
prog-audacity

```

save it and execute
```

sudo chmod a+x /usr/bin/audacity

```

this should do it.

---

### Post by bigsmitty64 on 2010-10-21
> **sanderd17 said:**
> 
```

sudo mv /usr/bin/audacity /usr/bin/prog-audacity
gksudo gedit /usr/bin/audacity 

```in gedit, type the text
```

#! /bin/bash


export UBUNTU_MENUPROXY=0
prog-audacity

```save it and execute
```

sudo chmod a+x /usr/bin/audacity

```this should do it.
Thanks for this, worked like a charm!

---

### Post by kingofmakai on 2010-10-21
Thanks sanderd17 so much! :)

---

### Post by tophill on 2010-10-22
Same problem, same fix.  Thanks.

---

### Post by glitterball on 2010-12-30
Thanks a lot - worked perfectly.

---

### Post by scooby359 on 2010-12-30
Thanks for the help! Works brill :)

---

### Post by Vermind on 2011-01-01
I found what sets this UBUNTU_MENUPROXY. It is /etc/X11/Xsession.d/80appmenu.
It comes from the appmenu-gtk package. Purging that should fix it.
Warning: I haven't tested what this will do to unity if you use that.

---

### Post by cordoval on 2011-01-12
I did # comment the line on 80appmenu file

and restart laptop and it works like a charm

however have not tried what it does to unity! netbook...

---

### Post by Ubiquitine on 2011-01-15
If you have problems not only with one program you can add this to your ~/.bashrc file:


echo "export UBUNTU_MENUPROXY=0" >> ~/.bashrc

---

### Post by Deefburger on 2011-01-29
I have the same problem and discovered that the F10 key will open the menus even though the menubar itself can't be seen.  So, I'm assuming the menubar is there, under the title bar I suspect, since that is where the menus appear to drop down from!

Any way, F10 will give you a menu without hacking the system.

---

### Post by mudd1 on 2012-06-18
> **sanderd17 said:**
> 
To make this a permanent hack: do the following:
```

sudo mv /usr/bin/audacity /usr/bin/prog-audacity
gksudo gedit /usr/bin/audacity
```

in gedit, type the text
```

#! /bin/bash
export UBUNTU_MENUPROXY=0
prog-audacity
```


Well, this is more of a hack than you normally need. 

```

alias audacity='UBUNTU_MENUPROXY=0 /usr/bin/audacity' 
```

in your .bashrc or whereever should also do it. And survives package upgrades.

---

### Post by bmathise on 2012-11-10
I just uninstalled appmenu-gtk and that fixed the problem.

---

