---
title: "Terminal commands for switching proxy mode"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by mrpadie on 2012-03-21
Hi all.

I'm looking for the terminal commands to switch my proxy mode from none to manual, and visa versa. Basically, I've set up cntml to run while I'm at my university, which uses NTML authentication. When I'm at home however, internet connections are direct.

Basically, I am creating a script that will run once WiFi is connected. It'll test to see if cntml can be started (meaning it can connect to the proxy, and hence I'm on campus), and if so, change my proxy settings to manual, which routes all traffic to localhost, which is where cntml is listening.

I'm using Unity - the settings are already stored in the Network Settings menu, so all I need to essentially do is switch from none to manual or visa versa when needed, but from a terminal command.

I'm using 11.10.

Thanks for the help,
MrP.

---

### Post by eGelor on 2012-03-21
Hope this will help U 
[http://ubuntuforums.org/showthread.php?t=1390260](http://ubuntuforums.org/showthread.php?t=1390260)
and this 
[http://ubuntuforums.org/showthread.php?t=858016](http://ubuntuforums.org/showthread.php?t=858016)

---

### Post by mrpadie on 2012-03-22
Thanks for the reply.

I've seen those commands before. They seem to only work while using the GNOME shell, where as I'm using stock Unity. I did try the commands, even tried to change the value in the proxy file myself, but the changes weren't recognized in the Network Settings GUI, nor did they actually do anything to my access.

Weirdly though, that file (gconf/system/proxy) contains my settings. It just doesn't seem to change the proxy mode when modified.

Any other ideas?
MrP.

---

### Post by eGelor on 2012-03-22
I realy don't know whats unity but.
There's nothing to do with gnome shell
If you are using terminal i suggest terminator and i hope you know the apt-get cmd.
so with the locate cmd as $locate proxy |more i find that in my case proxy is not at /system/proxy but at ~/.gconf/system/proxy
try again. is you gconftool as a cmd works?
and don't forget to use emacs as an editor. 
Hope that i help U. bye

---

