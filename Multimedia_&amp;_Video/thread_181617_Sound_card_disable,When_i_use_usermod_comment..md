---
title: "Sound card disable,When i use usermod comment."
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by semgok on 2006-05-24
Hi all,
Normally x users in y group but i want to add x users => y and z groups

```
usermod -G y,z x
```


When i use usermod,my sound card disabled and i cant use flash disk.
and i cant mount my flash disk.What can i do ?

Thanks all.

Semih.

---

### Post by mpvano on 2006-05-24
Usermod does not ADD groups, it REPLACES THE ENTIRE GROUP LIST WITH THE ONE YOU TYPE!

Go back to the gnome System->Administration->Users and Groups control panel and reset your group memberships for your account by selecting yourself and using the "User Privileges" tab in the dialog to reenable all the functionality you normally use.

From then on, if you want to use usermod -G, you need to first list ALL the groups you belong to with the "groups" command. You then need to list ALL these groups, separated by commas WITH NO INTERVENING WHITESPACE, followed by the group name you want to add. For example:

usermod -G youracctname,adm,audio,lpadmin,scanner,admin,THENEWGROUP

where THENEWGROUP is the group you are trying to add.

You may, however have already screwed things up by revoking your own administrative rights!

You may need to reboot using a recovery mode system entry in grub. This will give you a root command line and you can then use the correct usermod command to reenable your admin privileges something like this:

usermod -G youracct,adm,audio,lpadmin,admin   youracct

where "youracct" is your account name. After rebooting again, you should be able to login in the usual fashion and then use the gnome control panel as indicated above.

I suggest carefully reading the man page for terminal commands before attempting to use them, since you can do a lot of damage to your system by issuing administration commands without understanding them.

hope this helps,

Mario

---

