---
title: "automatic logon to the telnet sessions - gnome-terminal"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by floorripper on 2011-10-03
Hello,


Have you ever been wondering how to log automatically to the telnet sessions to avoid typing password every-time you open a new session?


Lets say that you have a default username and password for all  devices on the network (cisco-routers)
[I]
username1
password1[/I]

so you open a terminal and type telnet 10.1.1.2 the terminal asks you about the username and password. 

[SIZE=1][COLOR=Navy]
oot@laptop# telnet 10.149.100.3
Trying 10.149.100.3...
Connected to 10.149.100.3.
Escape character is '^]'.

Username: username1
Password: ******[/COLOR][/SIZE]


Do you have any idea how to force ubuntu to fill those fields automatically for us? There is a function in Win program secure CRT where you can sepecify fields expect: Username, and Password, then you can insert your credentials and Secure crt will log you every time automatically.

Is there anything like this which can be used in **Ubuntu Gnome-terminal** please?
Some kind of automatic login/script/settings of telnet or terminal?

Thanks,
Floorripper

---

