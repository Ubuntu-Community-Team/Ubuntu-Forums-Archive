---
title: "LCDproc server CLi: 1 Scr: 7"
date: 2008-08-17
forum: Mythbuntu
---

### Post by DustWolf on 2008-08-17
Hello,

I have a MSI Media Live with MythBuntu 8.04. In order to make the Fatuba dm140 LCD display functional, I had to install a program pointed to in the wiki (LCDd) and start it up with /etc/init.d/miscboot.sh (I added a line for it there).

The LCD works fine, but I see the problem described [here]("http://www.mailinglistarchive.com/mythtv-users@mythtv.org/msg62986.html"). Basically the LCD works fine initially, but when Myth does some "theme calibration", the clock disappears and the LCD is showing "LCDproc server" and "CLi: 1 Scr: 7".

I have read that this is caused by an invalid command at reload and can be solved by restarting mythlcdserver (basically killing it and waiting for it to reappear) after the reload. I have tried this manually and it works great.

I have tracked down where mythfrontend is loaded and set a "pkill mythlcdserver" command at the end of the script after a 10 second delay ("sleep 10"), but it's not working.

How do I do this properly?

Thanks for any help in advance.

---

### Post by axelsvag on 2008-08-18
I get the same but after going to the appearance menu and back to the main menu the right info comes back.

---

### Post by DustWolf on 2008-08-23
Working solution:
1. Edit /usr/share/mythtv/mythfrontend.sh
2. Scroll to the bottom
3. Add ' &' at the end of the line 'exec /usr/bin/mythfrontend.real "$@"'
4. Add 'sleep 10' and 'pkill mythlcdserver' at the bottom of the whole script
5. Save and reboot

---

### Post by mike.wilmoth on 2010-02-13
All you really need to do is uncomment the following line in /etc/LCDd.conf:

ServerScreen=no

I had the same concern, uncommented this after reading the user guide: [http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#server-section](http://lcdproc.sourceforge.net/docs/stable-0-5-x-user.html#server-section)

---

