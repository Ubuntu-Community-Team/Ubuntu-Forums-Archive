---
title: "Update manager hanging on fresh install 12.04"
date: 2012-06-19
forum: Mythbuntu
---

### Post by MrMic on 2012-06-19
I just installed a fresh copy of mythbuntu 12.04.Once at the desktop I opened update manager and set it updating all the files it recommended.When it got to Samba, the update manager would become unresponsive .To the point that the windows would become blank and unable to refresh.A reboot and the update manager offers to do a partial update.From what I read , this is a bad idea:confused:

I decided to run apt-get dist-upgrade in a terminal instead and I found the reason for the manager hanging.In the terminal window apt-get stops at samba and asks if you want to replace your modified smb.conf with the new package smb.conf file.The gui manager does not seem to be able to handle this situation.Choosing to retain the original file allows the update to proceed.

Thought I'd write this up to help anyone else new to mythbuntu to save them some frustration.:D

Mic

---

### Post by richbl on 2012-06-23
> **MrMic said:**
> ...

Thought I'd write this up to help anyone else new to mythbuntu to save them some frustration.:D

Mic

Same exact problem here. Can someone please direct me to the Mythbuntu launchpad (not sure if bugs get reported through MythTV, Ubuntu, or Mythbuntu).

Thanks

rich

---

### Post by nickrout on 2012-06-24
> **richbl said:**
> Same exact problem here. Can someone please direct me to the Mythbuntu launchpad (not sure if bugs get reported through MythTV, Ubuntu, or Mythbuntu).

Thanks

rich


[http://bit.ly/Ku8O6R](http://bit.ly/Ku8O6R)

---

