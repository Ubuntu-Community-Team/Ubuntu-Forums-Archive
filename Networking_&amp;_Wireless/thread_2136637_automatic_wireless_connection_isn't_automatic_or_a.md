---
title: "automatic wireless connection isn't automatic or available to all"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by Muketeer on 2013-04-18
Please can someone help me?  I've just installed Lubuntu 12 on an old Dell Optiplex as a computer for my kids to use, but i want to keep administrative rights over it, so i can control what they do on it, to some extent.  I've got 3 accounts set up, one for me (with full sudo admin priveleges) and one each for them.  Problem is with wireless networking.  To connect to the internet using the RaLink wireless dongle requires me to both enter the WPA authentcation key (which is really long) and also my lubuntu admin password.  When i do this, i ensure that "connect automatically" and "available to all users" is checked.  However, on re-boot, i have to do this again (if i log in as me), and so would my children (if they log in as themselves).  I don't want to i) type in the password every time (it's a pain) and i don't want to have to give my children my admin password either.  How can i set up the system so that the wireless internet starts, whoever logs in, and without requiring either WAP or admin passwords?

Any help anyone can offer would be much appreciated.

---

### Post by Muketeer on 2013-04-18
I found this on an LXDE forum... could this help?  It provides some stuff to paste into the [COLOR=#333333][FONT=Lucida Grande] [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**/etc/network/interfaces**[/FONT][/COLOR]

I wonder if it'll work for all accounts?

[http://forum.lxde.org/viewtopic.php?t=46&f=6](http://forum.lxde.org/viewtopic.php?t=46&f=6)

---

### Post by Muketeer on 2013-04-19
Well, i've now tried installing a different GU and controller (WICD) but that had trouble getting the modem to recognised the passkey. Perhaps it was interfering with the gnome network manager that was already running?  I've also now tried editing the startup options by entering into terminal

sudo leafpad /etc/network/interfaces

and adding

[COLOR=#2E8B57][FONT=Monaco]auto wlan1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]iface wlan1 inet dhcp[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   wireless yes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   wireless-mode managed[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   wireless-essid <homenetwork>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]   wireless-key <homekey>
[FONT=arial]
But this didn't work either.  I think that the spaces and punctuation that are present in both the name of my home network and my passkey (which is a sentence, with apostrophes and all) are confusing things.  However, it did detect that there was something going on with the networks after a reboot, so this is the right thing to change.  Any ideas what i need to do to connect automatically at boot, so everyone has wireless access without using my admin password?[/FONT][/FONT][/COLOR]

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by Muketeer on 2013-04-20
Well I probably don't need to use lubuntu (the Optiplex has an Intel Pentium 4 2.8 GHz CPU and 1 gig of RAM) and a 34GB hard drive.  However, i was running XP on it before and it had become painfully slow with endless updates and geological timescales for booting.  On lubuntu it boots in about 30 seconds - Lovely!  I'd previously installed Ubuntu ages ago on another older machine (edgy eft?) but with each new update the OS was getting too big for the machine.  Lubuntu is committed to being small and neat, so i'd hope it remains fast on this machine.  All of which doesn't solve the problem, though.  Is there some way i can adapt the script above to enable me to enter my home network and lengthy, space-filled passkey?  I think it should work, but i don't know how to deal with the spaces...  i guess these are the problem.

---

### Post by Muketeer on 2013-05-15
In the end i have sorted this, though not quite sure how. I set it up using "users and groups" so that all users were administrators, and that seemed to sort it out.

---

