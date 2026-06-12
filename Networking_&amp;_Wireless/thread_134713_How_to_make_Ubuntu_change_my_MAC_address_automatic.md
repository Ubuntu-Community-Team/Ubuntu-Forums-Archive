---
title: "How to make Ubuntu change my MAC address automatically?"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by Starlight on 2006-02-22
Hi! I've found out that my internet connection works only if I change the MAC address of my network card. Is there way to do it automatically, when the system starts? :confused:

---

### Post by heimo on 2006-02-22
Edit /etc/network/interfaces and add hwaddress line. (man interfaces for syntax)

---

### Post by nmastae on 2006-02-22
[QUOTE=heimo]Edit /etc/network/interfaces and add hwaddress line. (man interfaces for syntax)[/QUOTE]
I have this problem too. Can you be more explicit? I'm a newbie here...

I can get to  /etc/network/interfaces, but I don't know what to do next.
What, exactly, do I add, and how?

Thank you.

---

### Post by heimo on 2006-02-22
Here's a thread about same topic:
[http://ubuntuforums.org/showthread.php?t=6315]("http://ubuntuforums.org/showthread.php?t=6315")
EDIT: It's very old, but interfaces file syntax is still the same.

---

### Post by Starlight on 2006-02-22
Thank you so much! I'm going to do it now, and if I don't have any more problems, I'm going to use my new Ubuntu more often than Windows! :D

---

### Post by nmastae on 2006-02-22
[QUOTE=heimo]Here's a thread about same topic:
[http://ubuntuforums.org/showthread.php?t=6315]("http://ubuntuforums.org/showthread.php?t=6315")
EDIT: It's very old, but interfaces file syntax is still the same.[/QUOTE]


$ sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
[COLOR="Red"]hwaddress ether XX:XX:XX:XX:XX:XX [/COLOR](insert here your old MAC)
name Ethernet LAN card

auto eth0

[COLOR="Red"][COLOR="Blue"]Okay, so I ran the first line in Terminal and got:

$ sudo gedit /etc/network/interfaces
bash: auto: command not found
j@...:~$[/COLOR][/COLOR]

What now? Can somebody walk me through this?

Thanks.

---

### Post by heimo on 2006-02-22
[quote=nmastae]What now? Can somebody walk me through this?[/quote]

Open a terminal window and use this command to edit interfaces file:
```
 gksudo gedit /etc/network/interfaces
```

You'll get an error message like:[COLOR=Red][COLOR=Blue] 
> bash: auto: command not found
[/COLOR][/COLOR]if you try to run a command "auto", which doesn't exist.

---

### Post by aysiu on 2006-02-23
[QUOTE=nmastae]Okay, so I ran the first line in Terminal and got:```
$ sudo gedit /etc/network/interfaces
bash: auto: command not found
j@...:~$
```

What now? Can somebody walk me through this?

Thanks.[/QUOTE] Can you type these commands? ```
cd /etc/network
ls
``` For example, when I do that, I get this: ```
user@ubuntu:~$ cd /etc/network
user@ubuntu:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces  options  run
``` *cd /etc/network* changes to the /etc/network directory.

*ls* lists the contents of that directory.

---

### Post by nmastae on 2006-02-23
[QUOTE=heimo]Open a terminal window and use this command to edit interfaces file:
```
 gksudo gedit /etc/network/interfaces
```

You'll get an error message like:[COLOR=Red][COLOR=Blue] 

[/COLOR][/COLOR]if you try to run a command "auto", which doesn't exist.[/QUOTE]
Okay, but how, exactly, do I edit the interfaces?
What, exactly, do I type in there, and where?

---

### Post by aysiu on 2006-02-23
[QUOTE=nmastae]Okay, but how, exactly, do I edit the interfaces?
What, exactly, do I type in there, and where?[/QUOTE] Theoretically, you can do ```
sudo nano /etc/network/interfaces
``` or ```
sudo gedit /etc/network/interfaces
``` Apparently the latter didn't work, which is why I wanted you to go to /etc/network and see if there actually is a file there called *interfaces*.

To break it down, the command ```
sudo gedit /etc/network/interfaces
``` basically means "with administrative privileges" (sudo) "edit with the program *gedit*" (gedit) "the file *interfaces* in the folder *network* that lives within the folder *etc*."

The other command edits the same file using *nano* instead of *gedit*.

---

