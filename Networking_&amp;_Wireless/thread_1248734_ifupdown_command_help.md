---
title: "ifup/down command help"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by @echo off on 2009-08-24
When I enter:
```
sudo ifdown wlan0
```
I am told that the device is not configured. 

and if I enter:
```
sudo ifup wlan0
```
it tells me that it is "Ignoring unknown interface wlan0=wlan0

I know that my card works because Im on now. I would like to know how to connect to a network using the terminal. I have a network manager but it doesn't hurt to learn new things.

---

### Post by spd106 on 2009-08-24
In order to use the ifup/down helper scripts you need to have the interface (wlan0) defined in the /etc/network/interfaces file.


Something like the following should do for starters. But see the [interfaces]("http://www.annodex.net/cgi-bin/man/man2html?interfaces") man page for further details.
```
auto wlan0
iface wlan0 inet dhcp
```

N.B. Doing this will cause Network-Manager to ignore the interface, so you will lose it's helpful auto-configuration.

---

### Post by @echo off on 2009-08-24
but commenting it out later would bring it back should I choose to do so right?

---

### Post by spd106 on 2009-08-24
That's correct.

[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6)

The above page is very out of date now, but this commenting out the interfaces still holds true. If you want to be certain then you can always create two versions of the file and swap them when needs be.

---

### Post by @echo off on 2009-08-24
Thank you for the help

---

### Post by @echo off on 2009-08-24
Do i have to over write whats there all ready or add to it? Right now it contains:
```

auto lo
iface lo inet loopback 

``` 

I used nautilus to edit and save the file, but it doesn't save and is restored back to the way it was before I changed it.

---

