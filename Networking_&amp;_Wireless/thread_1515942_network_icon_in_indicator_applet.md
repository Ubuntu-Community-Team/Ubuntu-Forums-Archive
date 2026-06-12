---
title: "network icon in indicator applet"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by sameer.india on 2010-06-23
I have been using lucid since its beta 2 version. about a week ago though the network icon in indicators applet disappeared wiyhout running updates or anything i was offline since a week before that. i figured some error must have occured with network manager. so i entered 'nm' in the terminal and it gave an error that 'a.out' not found. i don't know how to connect to a network using that machine now that i can't see the icon anymore.

---

### Post by dineshs on 2010-06-23
[http://ubuntuforums.org/showthread.php?t=1311790](http://ubuntuforums.org/showthread.php?t=1311790)
When you have problems with NM icon pl check these
1) Go to system-preferences-startup applications and see that Network Manager is ticked
2) Right click on panel and click add to panel then add "Notification Area" from the list.
3) I have observed NM icon missing when
a)nm-system-settings.conf says *managed=false*
To solve
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
OR
b)/etc/network/interfaces contain anything other than
```
auto lo
iface lo inet loopback

```
To solve this comment out other lines(or backup the file and edit it so that it contains only these lines)
Should restart the machine after doing this
Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

---

### Post by sameer.india on 2010-06-24
thanks the icon has reappeared but 
/etc/init.d/networking restart gives a warning that 'ifup -a' is disabled and i must set 'managed=false' in nm-system-settings.conf.

---

### Post by sameer.india on 2010-06-25
> **sameer.india said:**
> thanks the icon has reappeared but 
/etc/init.d/networking restart gives a warning that 'ifup -a' is disabled and i must set 'managed=false' in nm-system-settings.conf.
the problem persists

---

### Post by dineshs on 2010-06-25
> /etc/init.d/networking restart gives a warning that 'ifup -a' is disabled and i must set 'managed=false' in nm-system-settings.conf.
I understand that the older linux distros used network-admin for managing networks ([https://help.ubuntu.com/community/NetworkAdmin)and](https://help.ubuntu.com/community/NetworkAdmin)and) the command used to restart network was  **sudo /etc/init.d/networking restart** .Now since you are using Network manager the command to restart-I think - would be **sudo service network-manager restart**   I am not sure

Pl check if this can help
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

---

