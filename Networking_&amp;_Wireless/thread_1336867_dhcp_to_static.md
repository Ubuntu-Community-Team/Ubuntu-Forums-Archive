---
title: "dhcp to static"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by kwickcut on 2009-11-24
Hello all i am new to Ubuntu server but i do run a mandrake server and it has been 6 years from my last install and setup so i am real rusty.


i have started to the setup for static ip

through putty i logged in as user changed to root then ran this line

```
vi /etc/network/interfaces
```it returns 

```
auto eth0
iface eth0 inet dhcp

```i see how to edit it so i changed it to below but my numbers are set to my network useing fake numbers for posting

```
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```when done how do i save this i have added a screen shot see in the bottom left it is set to insert 


i am at a real loss i have been trying to save this for almost 3 hours trying different things but i am lost  




thanks


kwick

---

### Post by capscrew on 2009-11-24
Welcome to the VI editor.  :D

Hit the ESC key to exit the edit mode.

Then use SHIFT + colon to bring up the command interface.

The type this: wq 

Hit enter and your done!

wq = write to file and quit.

---

### Post by kwickcut on 2009-11-25
thank you soooo much that worked like a charm i just need to get back into this and really learn it lol



kwick

---

### Post by jacobs444 on 2009-11-25
try using nano instead of vi, is so much easier

---

