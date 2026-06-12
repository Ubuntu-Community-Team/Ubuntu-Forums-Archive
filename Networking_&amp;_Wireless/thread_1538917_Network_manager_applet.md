---
title: "Network manager applet"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by shashanksingh on 2010-07-25
Once after booting, my network manager applet has suddenly dissapeared from the notification area.

I run nm-applet on the terminal and it says an instance of the applet is already running...
How do I get its icon on the notification area again????

---

### Post by dineshs on 2010-07-25
You can check
1)system-preferences-startup applications tick network manager
2)Right click on the top panel-click add to panel-select notification area -click add
3)Ensure that the file /etc/network/interfaces contain only [I]auto lo
iface lo inet loopback[/I]
For this first backup the existing file using
```
sudo cp  /etc/network/interfaces /etc/network/interfaces.bak
```
Then run
```
gksudo gedit /etc/network/interfaces
```
copy and paste the following (the file should contain only this)
```
auto lo
iface lo inet loopback

```
Links to network manager issues.
[http://ubuntuforums.org/showpost.php?p=9631393&postcount=7](http://ubuntuforums.org/showpost.php?p=9631393&postcount=7)
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
-You may add sudo before the commands post by DavorC 
[http://ubuntuforums.org/showthread.php?p=5132230#post5132230](http://ubuntuforums.org/showthread.php?p=5132230#post5132230)
post#3 by RomeReactor
If your problem is solved kindly let us know How

---

