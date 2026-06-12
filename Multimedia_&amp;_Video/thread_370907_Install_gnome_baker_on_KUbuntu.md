---
title: "Install gnome baker on KUbuntu?"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by BrandonBrown on 2007-02-26
Hello all. I have had a hell of a time getting K3B to run on my system. I have tried under dapper and edgy. I click on it and I get an hour glass on the task bar but then it disappears. I have read many posts on this issue and no tips have resolved the issue. It must be a hardware issue I have a Sony DVD RW. So, how do I install the Gnome foundation so I can see if GnomeBaker will work? I don't want gnome but I would like to have the apps that come with it. (I once done a similar install with Suse 10.2 I wanted KDE and when I was installing the OS I chose to have the Gnome Foundation installed.) Which gave me evolution, etc in my KDE menu. Any help is greatly appreciated.

---

### Post by jethro10 on 2007-02-26
You can just select Gnomebaker from the repo's to install. It should automatically pick any dependancies required (I guess it will be the major part of Gnome!)

You can then still log into KDE as normal and use Gnome baker from there.

J

---

### Post by taurus on 2007-02-26
Run it from a terminal to see what the error message is.

```
k3b
```

---

### Post by BrandonBrown on 2007-02-26
Thanks for the info Jethro10. Taurus, I ran k3b in a terminal and the cursor sat there and there was no report produced. I let it run for 20 min and finally just closed the window nothing was happening at all.

---

### Post by BrandonBrown on 2007-02-26
Taurus any idea why I have no error message when I run k3b in the terminal?

---

### Post by taurus on 2007-02-26
Look in ~/.xsession-errors to see if there is anything in there.

```
tail -20 ~/.xsession-errors
```

---

### Post by BrandonBrown on 2007-02-27
Ok Taurus here is what my error report reads when I ran the command you suggested. Sorry for taking so long to reply back I hope I not too late.

Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop

---

### Post by BrandonBrown on 2007-02-28
Hope this post hasn't died on me.

---

