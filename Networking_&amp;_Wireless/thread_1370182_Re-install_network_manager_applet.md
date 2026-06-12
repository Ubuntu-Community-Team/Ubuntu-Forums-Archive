---
title: "Re-install network manager applet"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by anjoeaj on 2010-01-02
I accidentally uninstalled the network manager applet from my ubuntu 8.10.
Now i cant access the internet. I don't know how to configure my internet connection without the applet. 
How can i install the nm applet without internet. Is there any 'executable' like things available.
Please help me to get my nm applet back

Regards
Anjoe

---

### Post by GeorgeVita on 2010-01-02
Hi **anjoeaj**, welcome to this forum!

Searching ubuntuforums.org I found the following which may work for you:

[http://ubuntuforums.org/showthread.php?t=1254085](http://ubuntuforums.org/showthread.php?t=1254085) posts #3 and #4

Regards,
George

---

### Post by iponeverything on 2010-01-02
If you delete and re-add the the "Notification Area" to the status bar, it should re-appear. 

This might work as well, open a terminal and do:

```

nm-applet&
disown %1
exit

```

---

