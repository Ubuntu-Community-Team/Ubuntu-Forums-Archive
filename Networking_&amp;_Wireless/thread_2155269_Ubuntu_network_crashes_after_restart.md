---
title: "Ubuntu network crashes after restart"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by Thetha on 2013-06-17
[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]I am using Ubuntu 12.04 and everything was working fine. I restarted the computer today morning and the Wired network stopped working. I am using static ip address and the /etc/network/interfaces has all the necessary details.[/COLOR][/FONT]

[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]If I go to command prompt and type [/COLOR][/FONT][COLOR=#333333][FONT=UbuntuRegular]start networking or stop networking:  I get the following message:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]"[/FONT][/COLOR][COLOR=#434343][FONT=Consolas]Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory"[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
I tried the following so far:[/FONT][/COLOR]

[LIST=1]
[*]Graphical network connections: Can click add button but cannot edit ipv4 connections to add a new wired connection.

[*]I tried /etc/init.d/networking restart - Says running /init.d/networking is depreciated as it may not enable some interfaces, also says that ifup -a is disabled in favour of network manager.

[*]/etc/init.d/networking stop - Computer hangs!!!! and also gnome loses menus etc.

[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Any help is hightly appreciated[/FONT][/COLOR]

---

