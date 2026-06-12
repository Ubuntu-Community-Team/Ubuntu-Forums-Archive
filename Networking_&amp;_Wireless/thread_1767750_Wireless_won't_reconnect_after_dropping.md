---
title: "Wireless won't reconnect after dropping"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by TerribleLIar on 2011-05-26
Hello. I'm having a problem with the wireless on my Asus EEEPC 1000HE using Ubuntu 110.04. Digging into the laptop forums, it says there is a problem with wireless on some models of the 1000HE, but it is not the same wireless device and my wireless problem doesn't seem as bad as listed, so I think it's a different problem. But my problem is that if wireless drops for any reason, it will not start working again unless I either reboot the computer or click the wireless icon in the systray, click disconnect so it stops flashing (like it's trying to reconnect) and then suspend my computer or log off and back on. And it only does the latter because I added a file located at /etc/pm/config.d/00sleep_module with the one line that reads SUSPEND_MODULES="rt2800pci" (my wireless driver) So that one line seems to cause wireless to get a fresh connection after suspending (or something. I'm not a very advanced LInux user). I've tried running the command "sudo /etc/init.d/networking restart", but that does nothing for me. I'm not sure what other command to try to see if can fix it.

Any help is much appreciated.

Edit: fixed by eliminating drivers as found in this topic: [http://ubuntuforums.org/showthread.php?t=1727945&highlight=1000he](http://ubuntuforums.org/showthread.php?t=1727945&highlight=1000he)

---

### Post by TerribleLIar on 2011-05-26
Bump.

---

### Post by TerribleLIar on 2011-05-27
Another bump.

---

### Post by jakkaru on 2011-06-05
I am having almost the exact same problem.
except mine is wired.
if the connection drops for any reason it just wont reconnect.
I have to restart the machine.

I'm sorta using 11.04 but I'm using the kernel from the previous version(the new kernel doesn't boot on my machine)
but i had this problem with the previous version of Ubuntu as well.

---

