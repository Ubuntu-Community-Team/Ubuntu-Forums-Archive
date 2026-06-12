---
title: "Mirobridge plugin"
date: 2009-10-17
forum: Mythbuntu
---

### Post by rothgar on 2009-10-17
I have Mythbuntu 9.10 beta installed and updated to MythTV 0.22-rc1 but I don't have the mirobridge plugin installed and didn't see it as an option in the mythbuntu-control-centre. I tried installing the plugin manually but seem to be having some problems so I wanted to know if it would be included in a update or final release of 9.10.
Please let me know if it is going to be an optional plugin or if I should continue to try to install it manually. Thank you.

---

### Post by superm1 on 2009-10-17
Currently there is no GUI for it.  You'll find it in /usr/share/doc/mythtv-backend/contrib though.  Just follow the wiki page to set it up.  You'll want the cron job running as your own user.

---

### Post by dibuntux on 2010-01-22
The wiki for Mirobridge is VERY confusing. I've everything required installed, but I get only "command not found"... if I test ./mirobridge.py -v

Any ideas? TIA

---

### Post by tgm4883 on 2010-01-22
> **dibuntux said:**
> The wiki for Mirobridge is VERY confusing. I've everything required installed, but I get only "command not found"... if I test ./mirobridge.py -v

Any ideas? TIA

Either not installed, you are not in the right directory, or that file isn't executable

---

### Post by Archmage on 2010-01-23
It seems that you must install it all manual, e.g. copying it to script, making it executable and so on.

I'm also hoping that with the next Mythubuntu release it will be better installed.

---

