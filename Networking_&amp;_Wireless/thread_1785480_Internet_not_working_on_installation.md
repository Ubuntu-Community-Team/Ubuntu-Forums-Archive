---
title: "Internet not working on installation"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by Proxmty on 2011-06-18
I've just installed ubuntu for the first time (latest version) on an HP laptop alongside windows vista and the Internet is not working at all.wired nor wireless. I connect through a router.

The menu options are greyed out for wireless and wired. I'm writing this from my iPad which is happily connected, as does the computer via the windows session so the problem is def not the internet connection. I really don't know where to start, could anyone help?

Thanks

---

### Post by nbound on 2011-06-18
Goto the terminal, and provide the output of lsmod, lsusb, and lspci.

---

### Post by Iowan on 2011-06-18
From a terminal (Applications>Accessories>Terminal), **lshw -C network** is another command that will provide similar results.

---

### Post by Proxmty on 2011-06-18
Please see attached, thanks

---

### Post by nbound on 2011-06-18
Perform a forum search for BCM4312. From my limited experience with broadcom cards it will require firmware, which isnt supplied unlike for most cards.

---

### Post by superduperlinuxperson on 2011-06-18
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
copy the folders to your home folder
then, run gksudo nautilus 
from that window, copy the two folders and put them in lib/firmware/

edit: take this post as null and void, i did not read your first entry allthe way sorry

---

### Post by Proxmty on 2011-06-19
I've done this so now there are two folders sat in the firmware folder called b43 and b43legacy, I rebooted but there is no change. Not sure if I've missed something? The laptop model is the HP compaq 6735s

---

### Post by superduperlinuxperson on 2011-06-19
i know how to fix the greyed out network part.
sudo NetworkManager
it will tell you its pid then (replace pid with what it told you):
sudo kill pid
sudo NetworkManager

---

### Post by Proxmty on 2011-06-19
I tried that, it came up with pid 865 originally, then 2137 after I killed it but network options still greyed out and no other change...

---

### Post by Proxmty on 2011-06-19
Wireless was resolved by following this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Finally!

However, less urgent but still something I'd like to address, the wires connection remains the same, greyed out and unusable.

Thanks for your help, if you know how I can sort the wired will be greatly appreciated

---

### Post by nbound on 2011-06-20
try **modprobe sky2**, if that works then we'll need to make it permanent. I dont know if this will require further setting up though. Hopefully someone will be along with more experience in ethernet cards

---

### Post by Proxmty on 2011-07-03
thanks for that. will try it.

just a further update, the wireless solution I mentioned earlier temporarily, the permanent solution is on this thread:
[http://ubuntuforums.org/showthread.php?t=896713&highlight=Bcm4312]("http://ubuntuforums.org/showthread.php?t=896713&highlight=Bcm4312")

---

