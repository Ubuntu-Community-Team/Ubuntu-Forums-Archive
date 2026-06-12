---
title: "Network manager disappear"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by Goosej on 2010-06-27
Can anyone please help. I am new to Linux and have been struggling with various distributions, suse, kubuntu, ubuntu for the lats 3 weeks to get it to work. Ubuntu is the best so far, but I am having trouble with the network manager. Everything works 100% after installation, internet - updating, etc. However, after a reboot - my network manager is gone and I cannot connect to the internet. I have tried various solutions - (a) reinstalling ubuntu, (b) Remove / replace the notification bar (c) uninstalling network manager and installing wfi-radar (d) installing wicd, (e) If tried to reinstall network manager but couldn't get that to work??
 
This is my last attempt to sort out this problem - before going back (unfortunaley) to Windows:confused:

---

### Post by dineshs on 2010-06-27
Did you try this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
``` 
and set
```
managed=true
```
Also please post what is in */etc/network/interfaces*
```
cat /etc/network/interfaces
```

---

### Post by Goosej on 2010-06-27
When running the code that you suggested - nothing happens.
 
Where's the screen Shot:
 
[FONT=Times New Roman][SIZE=3]mj@mj-laptop:~$ cat /etc/network/interfaces[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]auto lo[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]iface lo inet loopback[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]auto dsl-provider[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]iface dsl-provider inet ppp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]provider dsl-provider[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]auto eth1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]iface eth1 inet manual[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by Goosej on 2010-06-27
In the mean time - I have installed Xubuntu (hoping that this might fix the problem). Problem however persist after the first reboot - Network manager is gone

---

### Post by dineshs on 2010-06-28
please try this
step-1
```
gksudo gedit /etc/network/interfaces
```
commentout all lines(put a # before each line)[COLOR="Blue"] except[/COLOR]
```
auto lo
iface lo inet loopback
```
Or you can edit the file so that it contains only these lines,after making a backup(*sudo cp /etc/network/interfaces /etc/network/interfaces.bak*)
step-2
Now restart your machine
step-3
Configure your DSL via NM (if it is available) and not [COLOR="Blue"]pppoeconf[/COLOR] command
following this
[http://ubuntuforums.org/showpost.php?p=9516979&postcount=3](http://ubuntuforums.org/showpost.php?p=9516979&postcount=3)

---

