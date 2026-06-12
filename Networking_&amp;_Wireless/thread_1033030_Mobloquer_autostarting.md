---
title: "Mobloquer autostarting"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Richie2010 on 2009-01-06
Hello,

I have Mobloquer version 0.5 GUI for Moblock working fine. The GUI pops up but The only thing is that i have to manually key in my root password  there in the Manage Tab Lower left corner under MoBlock Control - Start.

Is there a way that i can make this starts without me having to key root password to change it from Moblock is stopped to MoBlock is up and running.

Thank you for your help

---

### Post by jre on 2009-01-07
You can make mobloquer remember your **user** password with sudo. Just make sure that under *Options - Settings - Sudo Frontend* [FONT="Courier New"]/usr/bin/gksu[/FONT] is set (if you are under Gnome) or keep the default [FONT="Courier New"]/usr/bin/kdesu[/FONT] (if you are under KDE).

If you want to start moblock automatically everytime, then just set in /etc/moblock/moblock.conf (and make sure /etc/default/moblock does not have that value in it):
MOBLOCK_INIT="1"

---

### Post by Richie2010 on 2009-01-07
Thank you for your kind reply.  The strange thing is that everything is as you stated.

I have to enter my password every time i do any main system functions that require password. And after i login to the main OS it is not passing the password to Mobloquer.

again if i manually click start then it will ask for password and then moblock starts blocking ips.  Very odd.  well its no big deal i have been manually starting it for months so i can just keep doing it that way :)

---

### Post by jre on 2009-01-07
Giving the sudo password is not the same as logging in to the system (although it is the same password).

Anyway, perhaps you once told mobloquer not to remember the password. Just remove in your home directory the folder .config/mobloquer and try again.

---

