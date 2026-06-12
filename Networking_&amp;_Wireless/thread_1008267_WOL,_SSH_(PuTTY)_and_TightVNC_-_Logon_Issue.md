---
title: "WOL, SSH (PuTTY) and TightVNC - Logon Issue"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by bluelamp999 on 2008-12-11
Hello,

I can easily set up SSH between my Intrepid host and XP client and control the host using TightVNC having followed this excellent guide...

[http://www.mydemosite.org/Ubuntu-Remote-Desktop-Guide.pdf](http://www.mydemosite.org/Ubuntu-Remote-Desktop-Guide.pdf)

However, what I want to do is 'wake up' my Ubuntu host and then control it..

I can wake up the host using a great little portable app 'IH Wake On LAN Portable'...

[http://portableapps.com/node/12734](http://portableapps.com/node/12734)

But my problem is...

When I wake up the host from shutdown, it wakes up fine and I can log in via an SSH connection and the box is showing the Ubuntu logon screen. However, I can't get a VNC connection because (I assume) the RDC stuff isn't yet running so I can't remotely control the machine.

I don't have this problem when the machine is woken from suspend (because the logging in has already been done!).

Is there some command I can issue from SSH to bypass/handle the logon screen so I can then run TightVNC?

Any help greatly appreciated...

---

### Post by sco` on 2011-12-06
Hi iv been doing a lot of messing around with ssh and vnc over the past month.


ssh -p XXXX -t -L 5900:localhost:5900 [EMAIL="username@192.168.1.2"]username@192.168.1.2[/EMAIL] -k sudo  x11vnc -safer -localhost "-auth /var/lib/gdm/:0.Xauth -display :0"

Notice the "-auth /var/lib/gdm/:0.Xauth -display :0" 
That's what gives it the ability to load the x11VNC pre any user logging on.

(script has to be run in terminal - sudo ya see)
(also here im using x11vnc - sudo apt-get install x11vnc)
 
there are other possibilities for the auth if your not running the same  desktop enviro - google is your friend - however i found mine in the  help for x11vnc

gdm:     -auth /var/gdm/:0.Xauth
         -auth /var/lib/gdm/:0.Xauth


Have only just installed Putty tonight but found out how to get it working -

ok read up here for using plink (putty command line) 
[http://the.earth.li/~sgtatham/putty/0.61/htmldoc/Chapter7.html#plink]("http://the.earth.li/%7Esgtatham/putty/0.61/htmldoc/Chapter7.html#plink")

then the command i used to connect ssh and load x11vnc

C:\Documents and Settings\ME>plink -ssh -P XXXX -X -t -L  5901:localhost:5900 [EMAIL="user@192.168.1.2"]user@192.168.1.2[/EMAIL] sudo x11vnc -localhost -display :0  -auth /var/lib/gdm/:0.Xauth

bit of trial an error on this one ^^ lol duno why 5901 worked... im  guessing thats a windows thing, rather than a gnu/linux to another. as  the first command is

Can go into more detail in you need dude, i feel this is the first  ubuntu forum post i actually have something good to contribute :) 

Sco.

11.04
gnome2



 ONLY 4 YEARS LATE!! ha

---

