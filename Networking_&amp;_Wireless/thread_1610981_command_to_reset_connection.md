---
title: "command to reset connection"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by anthalamus on 2010-11-01
Hi everyone,

I'm writing a script to automatically reset my connection when it's lost (while using a bittorrent client, apparently a common problem people have). I usually lose the connection after a few hours of use, and reseting it manually from the GUI (gnome) works well, so I thought I should automate this

however, using the shell I can disconnect, but not reconnect. I've read these various threads:
[http://ubuntuforums.org/showthread.php?t=731251](http://ubuntuforums.org/showthread.php?t=731251)
[http://en.kioskea.net/faq/1141-linux-restarting-the-network-interface-using-command-lines](http://en.kioskea.net/faq/1141-linux-restarting-the-network-interface-using-command-lines)
[http://ubuntuforums.org/showthread.php?t=1324599](http://ubuntuforums.org/showthread.php?t=1324599)
[http://www.linuxquestions.org/questions/linux-networking-3/how-to-stop-start-network-in-ubuntu-10-04-a-820543/](http://www.linuxquestions.org/questions/linux-networking-3/how-to-stop-start-network-in-ubuntu-10-04-a-820543/)

and got out of it that I should use (as sudo):
```

ifdown eth0 # or
ifconfig eth0 down

```to disconnect and
```

ifup eth0 # or
ifconfig eth0 up

```to reconnect

in my case, neither ifdown/ifup work, and only "ifconfig eth0 down" does ("up" doesn't). when I restart networking in general using
```

/etc/init.d/networking restart

```I get "networking stop/waiting"

"ifconfig" confirms that I use "eth0" and as I said earlier, manual resetting (connection quick icon + click on "Auto eth0") works fine, so I find it a bit odd that command line does't work :confused:
Anyone as got any idea what could be wrong?

Thanks!

---

