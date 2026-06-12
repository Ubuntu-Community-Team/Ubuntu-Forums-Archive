---
title: "wireless trouble HP Mini 210 UNR"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by Chuancey on 2010-03-27
I've just installed UNR on my HP mini 210.  The wireless is not working.  When I boot the netbook up in Window 7 it connect fine.  I followed the documentation instructions and performed a "device recognition" test.  In the terminal window it said "unclaimed" which apparently means there's no driver loaded(?)  I can't find instructions on how to fix this.  Sorry if this is really basic.  I've been searching the forums and documentation and can't figure out how to fix this problem.  I would really appreciate any help.  Please keep in mind that I'm a total newbie.  
Thank you very much in advance for your time.

---

### Post by Alterax on 2010-04-05
I think I can help you with this.  I have the exact same model of netbook, and had the exact same problem.  Here's what you will need to do:

Put in the netbook remix USB stick that you installed it from.  Go into it with the file manager and into the pool directory, then to restricted.  There's a folder in it called "b".  Go into it.  Dig around until you find a file called bcmwl-kernel-source.deb (or something like that.  bcmwl in the name's what you are looking for.)  Double-click on it to run the installer.  You'll need to give it your password.

Once the installation on it is finished, do a reboot. (not strictly necessary but old habits die hard),  When you log back in, go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS.  You'll need to enable the driver.

Then you're done, and good times will be had by all.

---

### Post by russet_wolf on 2010-05-09
I have a similar issue, except when I launch the installer, I get "Status: Error: Dependency is not satisfiable: dkms" What does this mean and what can I do to fix it?

---

### Post by pdc on 2010-05-10
> OK.... after another quick google. I found a DKMS package at

[http://packages.ubuntu.com/da/karmic/dkms](http://packages.ubuntu.com/da/karmic/dkms)

*That installed fine and allowed me to install the driver package with no issues*. 

[http://ubuntuforums.org/archive/index.php/t-1305296.html](http://ubuntuforums.org/archive/index.php/t-1305296.html)

you would look in karmic repositories?   or intrepid if they still exist ..........

use synaptic? search on dkms

---

