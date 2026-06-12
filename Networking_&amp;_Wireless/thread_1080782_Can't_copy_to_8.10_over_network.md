---
title: "Can't copy to 8.10 over network"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by arigwapo on 2009-02-25
I'm running 8.10 on a headless server and I've permitted other users to write to my video & music folders.  I have no problems connecting to the shares from my iMac and Macbook.  However, when I try writing to the folders over the network, it says that I do not have sufficient authorization to do so.

Any idea on a fix?

---

### Post by MockY on 2009-02-25
do a chmod 777 on the share and see if that changes anything.

---

### Post by arigwapo on 2009-02-25
I'm a newbie and since the option to chmod doesn't show up when I right-click the folders, I'll assume I have to do it a terminal.

Can someone give me the command-line for it?  I have a plain-jane 8.10 install...no other OS onboard.

---

### Post by MockY on 2009-02-25
On the machine that serves the folder, open up terminal and type
```
sudo chmod 777 /thesharedfolder
```

---

