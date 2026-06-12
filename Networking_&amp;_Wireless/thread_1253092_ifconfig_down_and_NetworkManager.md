---
title: "ifconfig down and NetworkManager"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by diggle on 2009-08-29
Two issuse both sort of related.  My notebook has and internal wireless card but its a little weak so I like to use my usb one.

Gnomes NetworkManager doesnt appear to have an option for "No connection" and always tries to connect to a network.  For me this is an issue in itself.

I thought a work around would be to do "ifconfig eth1 down" but eth1 doesnt go down and stays active.

No error messages are given with "ifconfig eth1 down", it's run as root. theres no messages give in /var/log/messages or dmesg and i'm using ubuntu 9.04 with all the latest patches.

Thanks for any help.

---

### Post by Iowan on 2009-08-29
Gnome's Network Manager DOES have an option to "Connect automatically". You can uncheck that option (if it is set).

---

### Post by diggle on 2009-08-29
ah yes thank you.

Hidden away in some right click menu I've found it.  However this doesnt solve the problem of why "ifconfig eth1 down" doesnt work, well not as expected anyway.

---

### Post by Iowan on 2009-08-30
> **diggle said:**
>  However this doesnt solve the problem of why "ifconfig eth1 down" doesnt work, well not as expected anyway.*Might* be Network Manager "managing" the interface.

---

### Post by diggle on 2009-09-10
Hmm I see.

Is there a way of taking the network down with ifconfig without closing NetworkManager?  Closing NetworkManager and then starting it again latter when I need it seems to cause all sort of problems which only a reboot can resolve.

---

### Post by Iowan on 2009-09-10
Network Manager also lets you "Click" on a connection to disconnect... but it will reconnect if "Connect automatically" is checked (I just tried it). I haven't tried forcing down a connection, but trying to override NM seems like a way to cause different problems.

---

