---
title: "open-iscsi boot mount points"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by baggar11 on 2009-09-24
What's the trick to getting Jaunty to automatically mount iSCSI targets on boot? Right now, it looks like open-iscsi is loaded before networking. This causes a nice 15 second pause when booting up the system, with error messages.

Using Ubuntu 9.04 Desktop 64bit.

---

### Post by baggar11 on 2009-09-25
I kind of solved this. Although it's a patch job more than anything. I had stumbled upon this thread --> [http://ubuntuforums.org/showthread.php?t=661697](http://ubuntuforums.org/showthread.php?t=661697). Of which I wasn't really satisfied with setting the nodes to automatic, because that would produce a slow down in bootup times and error messages flashing by the screen.

I ended up doing something similar with a script that I have gnome loading on start instead. That way, I can have all the nodes as manual, still preserve normal bootup times, and have the node mounted when I enter gnome.

the script goes like this -->

sudo "password" | sudo -S iscsiadm --mode node --targetname iqn.1995-04.com.dlink:blablatest:6-0015e9-000a75826-4abcff80bf51ad07 --portal <server ip> --login
sleep 10 %% mount /dev/sdb1 /<mountpoint>

Hope that helps someone else. I still would prefer a better way for open-iscsi to start on system boot.

---

