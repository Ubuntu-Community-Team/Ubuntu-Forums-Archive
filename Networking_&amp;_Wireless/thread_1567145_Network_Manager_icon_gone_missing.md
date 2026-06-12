---
title: "Network Manager icon gone missing"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by gummbahla on 2010-09-03
(Ubuntu 10.04)
I've been struggling for over a week now to get the network-manager icon back in the notification applet. I don't exactly know how and when it disappeared, but I have not been able to get it back eversince. I need it to start a VPN connection.

To be clear:
- The notification applet is running (battery icon etc is showing)
- Network manager is running
- Wireless connection works flawlessly

What I've tried so far:

**Solution 1**** (did not work)**
```
 sudo nm-applet --sm-disable
```Gives me 
```
 An instance of nm-applet is already running.
```[B]

Solution 2 (did not work)[/B]
Editing nm-system-settings.conf, set managed = false to true.

**Solution 3 (did not work)**
```
sudo service network-manager restart
```Does restart network-manager, but no icon appears.

[B]Solution 4 (did not work)
[/B]Remove and add back notification applet


Anyone with another solution?

---

### Post by wesleybailey on 2010-09-03
Try this it is worth a shot...

> **fmurrieta said:**
> I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:

All I need to do to fix the missing nm-applet was1.- Login as your first user
[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT]Hope thi*s can save you* some time!


Fernando Murrieta


Latest Tutorial: [Convert .uif to .iso ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by gummbahla on 2010-09-04
Thanx that did help for the first user! However, if login remotely (FreeNX) while I'm logged on locally as well, the icon is not visable in the remote session (all other notification icons are present). Any way to change this?

---

### Post by gummbahla on 2010-09-15
*bump*
Maybe this needs a little clarification: when I logon to the machine locally, the icon is visible.
If I then logon remotely (FreeNX) with the **same** user account, the icon is NOT visible. 

Is this a (known) bug, or is there a way to fix this behaviour?

---

### Post by candtalan on 2010-09-21
I found the applet was not fully working with connected wireless if I was using the broadcom proprietary STA driver, might not be your solution though.
[http://ubuntuforums.org/showthread.php?t=1578402](http://ubuntuforums.org/showthread.php?t=1578402)

---

### Post by dineshs on 2010-09-21
```
sudo gedit /etc/network/interfaces
```should contain only```
auto lo
iface lo inet loopback

```
(you may try editing the file after saving a copy)

---

### Post by candtalan on 2010-09-21
> **dineshs said:**
> ```
sudo gedit /etc/network/interfaces
```should contain only```
auto lo
iface lo inet loopback

```
(you may try editing the file after saving a copy)

Thanks, in my case, it contains this.

---

