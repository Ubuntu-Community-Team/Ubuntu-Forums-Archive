---
title: "Boxee get uninstalled when applying updates in Ubuntu 11.10"
date: 2011-10-30
forum: Multimedia Software
---

### Post by kingscorpio on 2011-10-30
Hi All

Has anyone come across this issue. I install Boxee on Ubuntu 11.10 64 Bit and when I do 

# sudo apt get install update

I get message telling me about how many Packages will be installed and 1 package will be removed. After doing the updates I see that Boxee gets uninstalled.

Can someone help on this....


Harry

---

### Post by bardov on 2011-10-31
Similar problem, I cannot install boxee 64bit on 11.10 64bit.
Boxee relies on a version of libxmlrpc-c3, that was replaced by 11.10 to a newer version.

I guess we should complain to boxee, not ubuntu.

---

### Post by David Valentine on 2011-11-18
> **kingscorpio said:**
> I install Boxee on Ubuntu 11.10 64 Bit and when I do 

# sudo apt get install update

I get message telling me about how many Packages will be installed and 1 package will be removed. After doing the updates I see that Boxee gets uninstalled.I'm having the same problem and am also looking for a solution.

---

### Post by beew on 2011-11-18
Well if you try to reinstall Boxee synaptic will tell you which packages will be uninstalled before you click "apply", that way you will find out where the conflicts are, with that knowledge you may be able to find a solution.

---

### Post by clauziere on 2011-12-03
I think it's a dependency problem. You can try this tutorial
[http://lauziere.net/how-to-install-boxee-ubuntu-11.10](http://lauziere.net/how-to-install-boxee-ubuntu-11.10)

---

