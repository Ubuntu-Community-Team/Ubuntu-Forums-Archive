---
title: "connection internet only on reboot"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by ubu499 on 2011-07-29
[SIZE=3]hi all,
I have ubuntu 10.10 gnome desktop

I hava a modem ethernet for internet connection on eth0
If i reboot my laptop the connection is on
If my laptop is already running and i want to connect i'm unable to connect
I try with ```
sudo dhclient eth0
``` but [/SIZE][SIZE=3]unsuccessfully
nor [/SIZE][SIZE=3]```
sudo /etc/init.d/networking restart
```[/SIZE][SIZE=3]
I get internet only with restart
any suggestion ?
Thanks all
[/SIZE]

---

### Post by ubu499 on 2011-08-06
any suggestions ?

---

### Post by Lampi on 2011-08-06
Does your /etc/network/interfaces look like this?
```

auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
auto eth0
iface eth0 inet dhcp
```

---

### Post by Pennybear77 on 2011-08-07
I have a similar problem on Ubuntu 10.04    My /etc/network/interfaces has the following text      auto lo      iface lo inet loopback   Do I need to change the text to that as described in Lampi's post?  Do I change the text within that file and save as (my file opens as read only), or is there another place to change the setting?    This is a relatively new problem for me on Linux and a month or so ago I did not have this problem.   Thanks

---

### Post by ubu499 on 2011-08-07
Thanks Lampi,
My interfaces miss this row:
> allow-hotplug eth0
Now it seems to work properly!!!

For [Pennybear77]("http://ubuntuforums.org/member.php?u=1316624"): your file open in read-only because outside the user directory
You must install the Nautilus Extension "Open as Administrator" following this link [http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html](http://www.watchingthenet.com/ubuntu-tips-for-windows-users-add-open-as-administrator-to-nautilus-right-click-menu.html)
Then you navigate to the directory /etc/network and open it as admin
Then open interface and modify it.
I hope you solve your problem like me....bye

---

### Post by Pennybear77 on 2011-08-10
Thanks ubu499 and Lampi, my internet connection seems to be working properly now!

---

