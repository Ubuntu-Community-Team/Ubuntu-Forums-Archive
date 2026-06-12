---
title: "Catch 22 setting up dial-up without the proper apps."
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by djen9999 on 2010-11-02
I'm sure this has been covered before but how does one go about setting up a dial-up Internet connection without wvdial or gnome ppp?

My brother lives in a remote area with only dial-up Internet service.  I got him set up with an external serial modem plus a disc with Ubuntu 9.04 and WUBI.  Apparently wvdial is not included in the basic install.  I will be visiting him in a few days and I would like get him going with his dial up.  He currently has Windows XP and WUBI installed.  I tried sending him a disc with wvdial but it didn't include the dependencies.  Is there any way I can download a package on a disc?  All suggestions are welcome.

---

### Post by grahammechanical on 2010-11-02
Until recently I used a dial up modem. Go in a terminal and type

```
sudo pppconfig
```

This will run a text based program to set up a serial modem. Follow the instructions on the screen. If you keep the name of the provider as "provider" then to dial up you type

```
sudo pon
```

and to disconnect you type

```
sudo poff
```

If you put in a different name then you will have to type the name you put it and it may be a longer name. The modem port is ttyS0 for com 1. I used Dynamic DNS

Regards.

---

### Post by djen9999 on 2010-11-02
Great!  If all else fails, we'll try this.  At this point it seems to be the most logical.  This can at least get us on line to get wvdial and gnome ppp.

Thanks

---

