---
title: "Ubuntu 12.10 server and Zenoss - problem with install."
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by kolomiro on 2013-03-10
Hello
I'm sorry for my english. 
Maybe someone have some experience with network monitoring tool ZENOSS. 
I am novice user linux but I can handle with most things. Now I try to install on the Ubuntu Server 12.10 in accordance with tuttorial [http://www.howtoforge.com/zenoss_network_monitor_ubuntu](http://www.howtoforge.com/zenoss_network_monitor_ubuntu) but I have problem. 
To 16 point everything  it's correct but when I try install (point 17 - ./install.sh) I have error:

```
[COLOR=#2E8B57][FONT=Monaco]zenoss@ubuntu-server:~/zenossinst$ ./install.sh[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]This installer actually builds Zenoss.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]For a simpler installation try the VMPlayer Appliance image,[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]or use RPMs for Redhat based systems.[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Building...[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]Setting SVNSERVER=dev.zenoss.org[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Setting SVNTAG=trunk[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]autoconf is not in the path[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]zenoss@ubuntu-server:~/zenossinst$[/FONT][/COLOR]
```


I don't know what is wrong and where I can to write correct path to autoconf. May be I missing something?
Maybe someone can help me?


Thanx

---

### Post by chili555 on 2013-03-10
It can't find autoconf because it's probably not installed. I suggest you go through the README, if there is one, and be sure all the prerequisites are installed before you proceed. You can install autoconf with:```
sudo apt-get install autoconf
```DISCLAIMER: I know less than zero about Zenoss, whatever that is. I know a tiny bit about installing packages.

---

