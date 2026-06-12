---
title: "Using an Atheros ar242x without ndiswrapper"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by NCSmokeEater on 2009-01-08
Hey guys,

I had ran into some issues getting my internal wireless card running on 8.10, but ndiswrapper did the trick in less than 5 minutes. I'm thrilled I don't have to carry around my Belkin USB wireless adapter anymore! haha There is one small problem though, so I figured I'd see if anyone had any advice.

Ndiswrapper doesn't support monitor mode. I'd really like to be able to use it, but for now I can't.

Does anyone know of a way to get an Atheros ar242x card working *without* ndiswrapper?


Any help would be appreciated!

---

### Post by superprash2003 on 2009-01-08
how about this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by NCSmokeEater on 2009-01-08
> **superprash2003 said:**
> how about this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

Well I followed it word for word but still no joy. Thanks for the input though, I appreciate it.

I find it odd that I have an ar242x card but the driver I'm using (works flawlessly) through ndiswrapper shows up in the restricted drivers as "Support for 5xxx series of Atheros 802.11 wireless LAN cards.". It works though, so I don't know. I just wish I could find a work-around for ndiswrapper. It's not quite as feature filled as I need, but hell, it works so I can't complain.

---

### Post by NCSmokeEater on 2009-01-13
got it working. thanks for the advice though. i figured it out. if anybody else wants to know how, let me know.

---

### Post by us3rX on 2009-01-13
> **NCSmokeEater said:**
> got it working. thanks for the advice though. i figured it out. if anybody else wants to know how, let me know.


Still trying to get my wifi working, with or without ndiswrapper, makes no difference to me, i just want my wifi to work. XD

Any help or info you have would be greatful.

~us3rX :twisted:

---

### Post by NCSmokeEater on 2009-01-15
> **us3rX said:**
> Still trying to get my wifi working, with or without ndiswrapper, makes no difference to me, i just want my wifi to work. XD

Any help or info you have would be greatful.

~us3rX :twisted:

id be glad to help. im gonna assume youre using the ar242x/ar5007... try this and let me know how it works.


```

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work


```

i hope this helped. credit goes to formol on miniurl.com/98

let me know if it works for ya! if not i can give you some other links to try a different approach :)

---

### Post by us3rX on 2009-01-15
Maybe I am doing something wrong, followed what you said, went to System>Admin>Hardware Drivers and disabled both Wifi. Then installed ndiswrapper and the driver, rebooted and still no wifi. It says Hardward Present: No. Yet I know I have the Atheros AR242x card >.<

jer3my@jer3my-laptop:~$ lspci | grep Wireless
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev ff)


~us3rX :twisted:

---

