---
title: "Can't update nor open terminal"
date: 2010-10-21
forum: Mythbuntu
---

### Post by larsolav on 2010-10-21
Dear all,
I have 10.04 with autobuilds enabled.For a few weeks i have not been able to udate the machine. After I click on the arrow with the "!" in on the upper right corner and tell the manager to update in the pop up window, the updates download but upon it trying to install the updates I get this error:
> e: install-info: subprocess installed post-installation script returned error exit status 139
I also am not able to open a terminal to try to update manually...
Anything else I can do to troubleshoot? Other than this, Myth works fine..

Thanks!

---

### Post by LowSky on 2010-10-21
CTRL+ALT+F1

login

then type

```
sudo apt-get update && sudo apt-get upgrade
```

to return to GUI

CTRL+ALT+F7

---

### Post by larsolav on 2010-10-21
Thanks LowSky for the quick response,
This is weird: when I try CTRL+ALT+F1 my screen goes blank!I get the screen back with CTRL+ALT+F7. Strange.
Also, I'm not able to SSH into the box from another machine using Putty.

---

### Post by larsolav on 2010-10-21
Just tried "sudo apt-get update && sudo apt-get upgrade" from ALT-F2 with Run in erminal checked, A terminal pops up, but then upon the password being entered, it goes away..

---

### Post by larsolav on 2010-10-23
Hmmmm, still not working. May just have to reinstall the OS. Oh, well. Will give me an opportunity to install 10.10 I guess...
I have seen others reporting the "error exit status 139" but no one has a solution. According to [this link]("http://www.slac.stanford.edu/BFROOT/www/Computing/Environment/Tools/Batch/exitcode.html"), it is as Segmentatation violation, whatever that means...

---

### Post by larsolav on 2010-11-09
I'm about to buy a new compact flash card to install a fresh copy of 10.10. I would like to backup the current database on my 10.04/0.23.1 setup. But how can I run ```
/usr/share/mythtv/mythconverg_backup.pl
```if I can't get a terminal? What do I do?

---

