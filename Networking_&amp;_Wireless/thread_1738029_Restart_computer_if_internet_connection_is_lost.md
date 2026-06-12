---
title: "Restart computer if internet connection is lost"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by doubler007 on 2011-04-24
Hi all, this is my first thread.
Like the title says, is there a way to restart the computer if the internet connection is lost?
Is this possible on ubuntu?

Thanks in advance

---

### Post by leviathan8 on 2011-04-24
You know... you don't really have to restart the computer if the connection is lost. Right click on the Network Manager applet in the notification area and uncheck "Enable Networking", then check it again to reconnect. It's unlikely that your internet connection will just stop working.
However, if you still insist that restarting the computer is better, just hit CTRL + ALT + DEL and this should bring up a shutdown dialog.

---

### Post by dineshs on 2011-04-25
> You know... you don't really have to restart the computer if the connection is lost. Right click on the Network Manager applet in the notification area and uncheck "Enable Networking", then check it again to reconnect or just run ```
sudo service network-manager restart
``` in a terminal.

---

### Post by rich-york on 2011-04-25
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Lucida Grande]I like this internet site because so much useful stuff on here : D.

Richard
[/FONT][/COLOR][/FONT][/COLOR]

---

