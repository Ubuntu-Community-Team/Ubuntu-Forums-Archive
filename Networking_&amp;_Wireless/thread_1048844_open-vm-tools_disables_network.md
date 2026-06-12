---
title: "open-vm-tools disables network"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by AndyBro on 2009-01-23
I have installed out of the box Kubuntu 8.10 in a vm running in vmware player 6.5 on an xp system.  My network works fine and I am able to update kubuntu just fine.

I install the open-vm-tools package from the package manager.  This kills my network connection.  Network Manager is showing as disabled.  I remove the open-vm-tools package using the package manager and the network magically comes right back.  I could do this all night with the same results each time.

I have looked everywhere for a solution.  I have tried downloading and building the latest open-vm-tools.  That sort of works but I can never build with the unity enabled.  I followed the directions [here]("http://cccarey.wordpress.com/howtos/howto-install-vmware-tools-on-ubuntu-810-intrepid/").

I would appreciate any help at all on this.  I'm also a Windows guy so I struggle with Linux a bit.  I'm not an idiot though.  My wife would argue with me on that one however.

Thank You in advance!

Andy

---

### Post by AndyBro on 2009-01-24
I noticed that after I ran open-vm-tools force reload I was able to connect to the network.  Each boot required this in order to connect.

But nevermind!  I've worked for days on this now.  Last night I discovered, downloaded, and installed VirtualBox.  No kidding, 20-30 minutes after downloading VirtualBox I was running a perfectly installed Kubuntu 8.10.  The "Guest Tools" actually installed with no problems and the "Seamless Windows" are awsome.  The whole install process was simply a treat and it's all very professionally done.  I would recommend this free tool over VMWare Player any day.

---

### Post by johnnyrae on 2009-04-09
In case anyone else hits this snag:

modprobe pcnet32
/etc/init.d/networking restart

That should get your network going again.

Here is a nice writeup that will help make the whole thing persistent:
[http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn/](http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn/)

---

