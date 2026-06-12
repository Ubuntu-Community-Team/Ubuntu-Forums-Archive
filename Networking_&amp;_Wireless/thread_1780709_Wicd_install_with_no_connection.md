---
title: "Wicd install with no connection"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by dfoley23 on 2011-06-12
I am trying to install wicd because of wpa2 problems with network manager on ubuntu 10.04 Lucid Lynx.

I go here [http://sourceforge.net/projects/wicd/files/wicd-stable/](http://sourceforge.net/projects/wicd/files/wicd-stable/) 
and I tried multiple versions up until 1.5.9 because they have .deb files the later versions dont have .dev files

I am downloading them onto a thumb drive and then moving them to the non connected computer.
I install using GDebi package install. 

After the installation wicd never starts its in my applications -> internet menu but It wont launch when I click on it. 
I did 

sudo wicd -foe 

and get an error

No module named wicd.path

Thanks for the help

---

### Post by dfoley23 on 2011-06-12
bump
 
I know this can't be too complicated so I just want to keep this thread alive long enough to find a solution. 
also there is this thread 
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy)
which I guess is another way I could get a wpa2 network to work?
I have a ralink driver it says that network manager and ralink driver wont connect to wpa2.
Will this way use network manager? (because i've already removed it (for wicd)) 
or will it use wicd in any way?
and will it work with a ralink driver?
 
also its also important to state that I have no internet connection on this computer so commands like apt-get wont work :(

---

### Post by dfoley23 on 2011-06-12
bump

---

### Post by dfoley23 on 2011-06-17
well I got wicd installed. The answer was here [http://ubuntuforums.org/showthread.php?t=1135636](http://ubuntuforums.org/showthread.php?t=1135636) number 7
but it didn't fix my wpa2 problems it just does the same thing network manager did
continuosly try to connect but then fail and then try to connect again and again.

---

### Post by dfoley23 on 2011-07-24
well it works now... 
the settings in the router configuration weren't exactly wpa2
they were something like wpa2 personal blah blah
set it to exactly wpa2 setting and it started to work

---

