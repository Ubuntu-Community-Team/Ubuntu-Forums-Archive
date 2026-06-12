---
title: "X-server breakage still break my ubuntu"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-18
Some time ago my GDM stopped working and all i got was a command line so i waited
for at least a few days,today i downloaded latest alpah 3 and reinstall it then i added 
x-swat ppa and compiz ppa and downloaded all 411 updates and now after restarting
ubuntu i again get just a command line so what can i do to fix the problem and is waiting 
and downloading updates some time in the future would fix it?
 
Thanks in advance.
 
P.S i did not did partial update i downloaded only the "official" updates.

---

### Post by marcio.mutti on 2010-08-18
Same problem here. I actually installed the Alpha 3, and everything was OK. Then I installed Xubuntu-desktop (from synaptics) and updated the other packages. Now GDM won't start unless in safe-mode. I'll try swapping GDM for something else latter, at home.

---

### Post by cariboo on 2010-08-18
Can you start gdm or X from the command line?

```
sudo service gdm start
```

or

```
startx
```

---

### Post by waspbr on 2010-08-18
nope, though whenever I use "startx" it copmplains about there not being a /usr/bin/X directory

All in all I thought that all this had to do with apparmour, it seems to get stuck there.

---

### Post by sinurge on 2010-08-18
Please read this [http://ubuntuforums.org/showthread.php?t=1549195](http://ubuntuforums.org/showthread.php?t=1549195)

xorg/xserver has been upgraded to a newer version (1.9) and some nvidia cards will break (mine did)

read the sticky: It will provide the workarounds for this issue

You would have to open up /etc/X11/xorg.conf and add

open up hardware Drivers and choose Current Version then 

Section "ServerFlags"
"ignoreABI" "True"
EndSection

if the same does not work check if your card is supported. If not you will have to switch to nouveau as default till 173 is upgraded.

---

### Post by aviramof on 2010-08-18
I tried sudo service gdm start it didn't work i would startx my card is ati hd 3650 512mb ddr2 not nvidia.

---

### Post by SevenMachines on 2010-08-18
> **waspbr said:**
> nope, though whenever I use "startx" it copmplains about there not being a /usr/bin/X directory

All in all I thought that all this had to do with apparmour, it seems to get stuck there.
Did you accidentally do a partial upgrade?
$ sudo apt-get install xorg

---

### Post by VMC on 2010-08-18
You guys need to look at some of your log files to figure out where the problems lies. In home dir check "**.xsession-errors**", in "**var/log/Xorg.0.log &/or syslog , kern.log**".

---

### Post by ronacc on 2010-08-18
try apt-get -f install , that should pull in the missing x files .

---

### Post by aviramof on 2010-08-18
> **SevenMachines said:**
> Did you accidentally do a partial upgrade?
$ sudo apt-get install xorg
 
No i didnd't and i wrote it at the top of the thread.
 
And how can i check home dir check "**.xsession-errors**", in "**var/log/Xorg.0.log &/or syslog , kern.log from command line?**

---

### Post by andrewthomas on 2010-08-18
> **aviramof said:**
> 
And how can i check home dir check "**.xsession-errors**", in "**var/log/Xorg.0.log &/or syslog , kern.log from command line?**
```
cat /home/username/.xsession-errors|less
``````
cat /var/log/Xorg.0.log|less
```

etc...

---

### Post by aviramof on 2010-08-18
Problem was solved in a very easy way all i did was to remove fglrx by using:

Sudo apt-get remove fglrx

and that it.

Thanks for everyone for there help.

---

### Post by cariboo on 2010-08-18
For .xsession-errors:

```
cat .xsession-errors
```

For the others in /var/log:

```
cat /var/log/X
```

where X is wahtever log file you want to read, the error should be close to the end of the file. if you want to page through the log append **|less** to the end of the command.

---

### Post by VMC on 2010-08-18
> **aviramof said:**
> No i didnd't and i wrote it at the top of the thread.
 
And how can i check home dir check "**.xsession-errors**", in "**var/log/Xorg.0.log &/or syslog , kern.log from command line?**

```
less .xsession-errors
```

or

```
vi .xsession-errors
```

---

### Post by aviramof on 2010-08-19
> **aviramof said:**
> Problem was solved in a very easy way all i did was to remove fglrx by using:

Sudo apt-get remove fglrx

and that it.

Thanks for everyone for there help.

Problem is already solved.:)

---

### Post by waspbr on 2010-08-19
> **sinurge said:**
> Please read this [http://ubuntuforums.org/showthread.php?t=1549195](http://ubuntuforums.org/showthread.php?t=1549195)

xorg/xserver has been upgraded to a newer version (1.9) and some nvidia cards will break (mine did)

read the sticky: It will provide the workarounds for this issue

You would have to open up /etc/X11/xorg.conf and add

open up hardware Drivers and choose Current Version then 

Section "ServerFlags"
"ignoreABI" "True"
EndSection

if the same does not work check if your card is supported. If not you will have to switch to nouveau as default till 173 is upgraded.


I finally see my Desktop, thanks a bunch.

---

