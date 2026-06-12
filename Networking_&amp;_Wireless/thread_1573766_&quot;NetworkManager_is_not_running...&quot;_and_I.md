---
title: "&quot;NetworkManager is not running...&quot; and I can't restart it"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2010-09-13
Approximately two days ago my nm-applet changed from the up & down arrows to a wireless graphic with a red exclamation point.  I lost my network connection.  I was playing a video game at the time.  I did not install any applications, change the network settings, have any non-included crons executing, run update-manager manually, or reboot my machine within the past 24 hours of this happening.

I completely removed network-manager & gnome-network-manager via Synaptic, configured my /etc/network/interfaces file properly, and rebooted.  I have my network connection working via the interfaces file.

Then, I found every file I could that mentioned "NetworkManager" and deleted them.  I re-installed network-manager and rebooted.  The deleted files were re-created upon reboot.  My network connection was working because of the /etc/network/interfaces file but NetworkManager was not and nm-applet was showing the wireless icon with the red exclamation point.

I have been trying to figure out what happened to NetworkManager.  When I click on nm-applet, it says "NetworkManager is not running..."  I tried to restart network-manager with the following commands and their respective errors:```
xk@localhost:~$ sudo stop network-manager
stop: Unknown instance:
xk@localhost:~$ sudo start network-manager
network-manager start/running, process 3704
xk@localhost:~$ ps -ae | grep 3704
xk@localhost:~$ sudo service network-manager stop

## notice - no output from process 3704 that is supposedly running

stop: Unknown instance: 
xk@localhost:~$ sudo /etc/init.d/network-manager stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
xk@localhost:~$ sudo /etc/init.d/network-manager start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start network-manager
network-manager start/running, process 3885
xk@localhost:~$ sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 3920

xk@localhost:~$ sudo restart network-manager
restart: Unknown instance: 
xk@localhost:~$ sudo stop network-manager
stop: Unknown instance: 
xk@localhost:~$ sudo start network-manager
network-manager start/running, process 4024
xk@localhost:~$ ps -ae | grep 3704
xk@localhost:~$
```

Here is a list of all the googling I have done.  The searches have been compressed because of Google's long url's:

Googled keywords:  [LIST=1]
[*][http://is.gd/f8lHs](http://is.gd/f8lHs)
[*][http://is.gd/f8lQP](http://is.gd/f8lQP)
[*][http://is.gd/f8lWw](http://is.gd/f8lWw)
[*][http://is.gd/f8m1T](http://is.gd/f8m1T)
[/LIST]

Here's a list of all the UF threads I've consulted already:[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=505636](http://ubuntuforums.org/showthread.php?t=505636)
[*][http://ubuntuforums.org/showthread.php?t=1456491](http://ubuntuforums.org/showthread.php?t=1456491)
[*][http://ubuntuforums.org/showthread.php?t=1485088](http://ubuntuforums.org/showthread.php?t=1485088)
[*][http://ubuntuforums.org/showthread.php?t=1313289](http://ubuntuforums.org/showthread.php?t=1313289)
[*][http://ubuntuforums.org/showthread.php?t=1559987](http://ubuntuforums.org/showthread.php?t=1559987)
[*][http://ubuntuforums.org/showthread.php?t=1458215](http://ubuntuforums.org/showthread.php?t=1458215)
[*][http://ubuntuforums.org/showthread.php?t=1310645](http://ubuntuforums.org/showthread.php?t=1310645)
[*][http://ubuntuforums.org/showthread.php?t=1354159](http://ubuntuforums.org/showthread.php?t=1354159)
[*][http://ubuntuforums.org/showthread.php?p=8020984](http://ubuntuforums.org/showthread.php?p=8020984)
[*][http://ubuntuforums.org/showthread.php?p=9782906](http://ubuntuforums.org/showthread.php?p=9782906)
[*][http://ubuntuforums.org/showthread.php?p=7961552](http://ubuntuforums.org/showthread.php?p=7961552)
[/LIST]

I looked in syslog at the time of the event and there was nothing relevant to this "crash".  I know I can completely remove network-manager, delete all the associative files that it leaves behind, and install Wicd.  I do not want to do that because that is not a solution.  Can you please help me determine what the problem is?  Thanks!

---

### Post by Iowan on 2010-09-13
> **strAlan said:**
> 
[COLOR="Red"]I completely removed network-manager & gnome-network-manager via Synaptic[/COLOR], configured my /etc/network/interfaces file properly, and rebooted.  I have my network connection working via the interfaces file.

I have been trying to figure out what happened to NetworkManager.  When I click on nm-applet, it says "[COLOR="Red"]NetworkManager is not running[/COLOR]..."  I tried to restart network-manager with the following commands and their respective errors:

I'm sure it isn't this simple... Did you re-install Network Manager?

---

### Post by MaindotC on 2010-09-13
Yes I did - I'll edit my post to specify that.

---

