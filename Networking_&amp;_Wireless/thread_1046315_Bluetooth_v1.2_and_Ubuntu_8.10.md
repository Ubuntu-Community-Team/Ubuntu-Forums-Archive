---
title: "Bluetooth v1.2 and Ubuntu 8.10"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by laeg_ on 2009-01-21
I bought a Bluetooth v1.2 USB dongle and when I plugged it in the Bluetooth icon came up in the system tray and half of the time I'm able to successfully pair my phone and the dongle if not from one then the other but even when they are paired I'm never able to browse the files on my phone, when I try I get the error...

```
Could not display "obex://[00:23:B4:8F:AB:C4]/".

Error: Connection to the device lost
Please select another viewer and try again.
```

I also have Bluetooth File Sharing installed and running.

I've also tried:

```
laeg@skyrocket:~$ sudo apt-get install gnome-vfs-obexftp
```

and a

```

laeg@skyrocket:~$ sudo /etc/init.d/bluetooth restart
```

and even a computer reboot. I've also tried removing the pairing many times from both devices, re-establishing it and still I can never browse the phone and keep getting the same error. While not being able to browse I was successfully able to send a file from each device once but every other time the phone tells me bluetooth connection failed and nautilus says push file transfer unsupported while bluez says org.openobex.ErrorConnectionAttempt failed.

I have my cordless telephone dock unplugged from the mains in case that matters even though I can transfer and browse files no problem with the same devices under Windows.

---

### Post by CryptSphinx on 2009-01-21
[http://ubuntuforums.org/showthread.php?t=580347&page=5](http://ubuntuforums.org/showthread.php?t=580347&page=5)

check out reply 47 - does that help at all

---

### Post by laeg_ on 2009-01-21
No, tried everything in that thread already, thanks though.

---

