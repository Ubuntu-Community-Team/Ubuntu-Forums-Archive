---
title: "nm-applet disappeared after using  pppoeconf"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by Kompost on 2011-03-25
hi, i have some trouble connecting to the wireless of the dormitery where i live in.

so that is what i already did:

[LIST=1]
[*]connecting to the hidden wireless network via nm-applet
[*]i typed in my personal user data using "sudo pppoeconf"
[*]connecting to the internet using "pon dsl-provider"
[/LIST]

so after i did that everything was working out very well and i was able to use the internet without a problem! but after i restarted the computer the nm-applet was gone so i can't connect to the hidden wireless network anymore...

if i try to start nm-applet manually the terminal says:
```
jonas@jonas-K50AD:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:1962): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

jonas@jonas-K50AD:~$ 
```

if i end nm-applet using the system monitor and try to restart it again i get the following output:

```

jonas@jonas-K50AD:~$ nm-applet
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:2025): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2025): DEBUG: old state indicates that this was not a disconnect 0

```

i hope someone may has a solution :)

---

### Post by An Sanct on 2011-03-25
I have the experience, that Ubuntu has a problem with hidden wireless networks (hidden SSID). I always had to manually re-connect. So I gave up and made the network visible.

I your case, you cannot do that (I guess, since you are in a dorm), you can use wifi radar, it supports hidden SSIDs.

---

### Post by Kompost on 2011-03-25
no idea anyone?

---

### Post by Icche Ghuri on 2011-03-25
Open a terminal and type:
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```
in this file change "managed=**false**" to "managed=**true**". Then restart your pc. Hope you'll get your NM Applet icon back.
You have to connect the pppoe by typing:
```
sudo pon dsl-provider
```
in a terminal every time you start/restart your pc.

---

### Post by Kompost on 2011-03-26
that worked! :) thanks a lot!

---

### Post by sureshatt on 2011-10-02
Thanks dude, it worked. You saved the day

---

### Post by Vishal Agarwal on 2011-10-06
> **Icche Ghuri said:**
> Open a terminal and type:
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```in this file change "managed=**false**" to "managed=**true**". Then restart your pc. Hope you'll get your NM Applet icon back.
You have to connect the pppoe by typing:
```
sudo pon dsl-provider
```in a terminal every time you start/restart your pc.

It Worked for me too. Thanks a lot.

---

