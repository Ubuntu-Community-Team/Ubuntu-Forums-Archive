---
title: "Not able to make DSL connection"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by elodsson on 2011-06-11
Hi!

I am trying to run **Ubuntu 11.04 64 bit** on an **ASUS X53SV laptop**. I configured the **DSL connection** (username and password), and it **can't connect** to it (the icon in the system tray keeps showing, that it is searching for the connection, and from time to time it flickers).
I have tried it with ElementaryOS 64 bit and LinuxMint 64 bit (both based on Ubuntu), and either it is the same problem, or it doesn't even bother to look up the connection. I have also tried it with KiwiLinux (also based on Ubuntu, but there is only a 32 bit edition), and the network worked without problem (no sound though if jack plugged in - the same problem as with my old ASUS A3E laptop).
The network connection works fine under Windows 7.
I have been careful when i introduced the username and password, so mistyping shouldn't be the problem.
So what should i do, where should i look to try to get it to work?

Thanx!
El&#337;d

ps.:I would like anyone not to try to convince me to use a different distro, or 32 bit or any other "conversions", i would just like someone to help me fix this problem. Thank you!

ps2: I looked in the forum and i couldn't find another thread that would discuss my problem. If there is one, please forgive me for opening a new similar one, and redirect me to it. Thank You!

---

### Post by novinick on 2011-06-11
So basicaly we may safely say
that it is ok with ubuntu 9.04 32 bit ,and have sort of an issue 
with ubuntu 11.04 64 bit ? 

since kiwi linux is formed over ubuntu 9.04
[http://kiwilinux.org/en/faq.html](http://kiwilinux.org/en/faq.html)

Do you conect on ethernet box or usb ?

---

### Post by novinick on 2011-06-11
tick this check boxes:
"Connect automatically" and "Available to all users"

as explained in thread
"DSL Connection won't connect after upgrade to Ubuntu 11.04"
[http://ubuntuforums.org/showthread.php?t=1779929](http://ubuntuforums.org/showthread.php?t=1779929)
[http://ubuntuforums.org/showpost.php?p=10740156&postcount=2](http://ubuntuforums.org/showpost.php?p=10740156&postcount=2)

and in this picture
[http://ubuntuguide.net/wp-content/uploads/2010/02/network-manager1-309x360.png](http://ubuntuguide.net/wp-content/uploads/2010/02/network-manager1-309x360.png)

---

### Post by elodsson on 2011-06-12
Yepp! It works now! Thank you very much. The tip from your second link made it work: i just left the "Service" box empty. That simple thing did the job. (I had the automatic connection and availability for all users checked before).

And to tie up the loose ends and answer your questions from above:

1. yes it worked just fine with the service name entered in ubuntu 9.04 32 bit so to say.

2. I don't have an ethernet box, just a simple ethernet cable making its way through my wall. Maybe somewhere on the street in a big metal box or something...

So, case closed, i think...
Thank you again!

---

