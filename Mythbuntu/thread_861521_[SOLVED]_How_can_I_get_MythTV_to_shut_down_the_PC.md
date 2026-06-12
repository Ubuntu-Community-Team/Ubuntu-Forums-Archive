---
title: "[SOLVED] How can I get MythTV to shut down the PC"
date: 2008-07-16
forum: Mythbuntu
---

### Post by GuiGuy on 2008-07-16
In the front end settings I have configured to have the reboot and shutdown options show on the exit menu.

However, selecting reboot or shutdown only takes me to the desktop. It doesn't shutdown.

Does anyone know how to fix that so it works as expected?

TIA

---

### Post by laga on 2008-07-16
Somewhere in the settings, you can enter shutdown and reboot commands. What entries do you have there?

---

### Post by GuiGuy on 2008-07-16
> **laga said:**
> Somewhere in the settings, you can enter shutdown and reboot commands. What entries do you have there?

The "Halt" command = halt
The "Reboot" command = reboot

These settings were the default, i.e. I did not enter them. The install did. 

NB: I tried "Halt=poweroff" as suggested in  the wiki. Made no difference.

Thanks

---

### Post by laga on 2008-07-16
You can try /usr/share/mythtv/myth-reboot.sh and /usr/share/mythtv/myth-halt.sh respectively. 

These use a rather naive approach to HAL to shutdown your computer.. if it doesn't work, you'll have to use sudo and modify /etc/sudoers accordingly. Let me know how myth-halt.sh works for you.

---

### Post by GuiGuy on 2008-07-16
> **laga said:**
> You can try /usr/share/mythtv/myth-reboot.sh and /usr/share/mythtv/myth-halt.sh respectively. 

These use a rather naive approach to HAL to shutdown your computer.. if it doesn't work, you'll have to use sudo and modify /etc/sudoers accordingly. Let me know how myth-halt.sh works for you.

Cheers. I'll give a go tonight after work.

---

### Post by freymann on 2008-07-16
> **GuiGuy said:**
> In the front end settings I have configured to have the reboot and shutdown options show on the exit menu.

However, selecting reboot or shutdown only takes me to the desktop. It doesn't shutdown.

Does anyone know how to fix that so it works as expected?



I believe what you need to do is set the shutdown command in the setup to:

sudo /sbin/halt

and then, in a terminal window, you have to:

sudo visudo

and add a line that reads:

%mythtv ALL=NOPASSWD: /sbin/halt

I don't know if you need to reboot before this works.

---

### Post by GuiGuy on 2008-07-19
> **freymann said:**
> 

sudo visudo

and add a line that reads:

%mythtv ALL=NOPASSWD: /sbin/halt

I don't know if you need to reboot before this works.

Didn't work. But thanks anyway. 

BTW, the people who invented visudo. Do they look like real geeks? ;)

Cheers

---

### Post by GuiGuy on 2008-07-19
> **laga said:**
> You can try /usr/share/mythtv/myth-reboot.sh and /usr/share/mythtv/myth-halt.sh respectively. 

That worked! Thanks

---

### Post by laga on 2008-07-19
Cool! I'm glad it worked.

---

