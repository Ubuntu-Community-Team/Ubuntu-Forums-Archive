---
title: "Need help understanding ubuntu's and its network"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by philidox on 2009-02-08
I can't understand something about ubuntu and I need help with it.  Here is the scenario, start up ubuntu and I come to the login window(like normal) before I do anything I hit "Ctrl+Alt+F1" to enter the command line screen.  After I log in, I enter the command "iwlist scanning" or "iwlist eth1 scan" and it cannot find any wireless networks in the area.  Then I hit "Ctrl+Alt+F7" to return me the GUI login window.  I logged via GUI and then I disable the network to ensure that nm-applet(gnome default network manager) isn't connecting to any wireless networks.  I went back to the cli, by pressing "Ctrl+Alt+F1" and entered the same command "iwlist scanning" or "iwlist eth1 scan" and it showed all the wireless networks.  So obviously some system services/application is activated by the GUI log in. I need two questions answered, what services is actived by the GUI login that allows the "iwlist scanning" service to work, AND how do I activate it before the GUI login?

---

### Post by cariboo on 2009-02-08
If you are using Intrepid, networking doesn't start until after you login. You don't need Network Manager for networking, you can remove it completely and it still works. The server versions don't have a gui and therfore don't have network manager installed and networking still works.

Jim

---

### Post by vajorie on 2009-02-09
```
sudo ifconfig eth1 up
```

---

### Post by philidox on 2009-02-09
> **vajorie said:**
> ```
sudo ifconfig eth1 up
```

Thank you, thank you, thank you!!! Simple answer

---

