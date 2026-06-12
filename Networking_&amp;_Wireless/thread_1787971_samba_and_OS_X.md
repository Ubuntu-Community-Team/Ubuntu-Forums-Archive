---
title: "samba and OS X"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by banff2010 on 2011-06-21
I set up a directory as a file server using GUI samba server configuration. Everything works fine. My Mac can see the folder. But It does not take the correct password, keep saying the password is wrong.

---

### Post by luvshines on 2011-06-22
I too faced this issue

Did you add the user to Samba ```
smbpasswd -a <user-name>
```

Did you set the 'netbios name' of the Samba server ?

I had mine set to 'luvshines' and the username which I had to specify while accessing from mac is luvshines\<user-name>

---

### Post by banff2010 on 2011-06-22
I solved it. Kept reading many things, loaded netatalk, swat etc. Apparently swat is no longer supported netatalk look too intimidating. I went back to samba gui configurator deleted all the users and shares first. Then follow the instructions and it worked. It was working earlier in a guest mode. Now I have no guest mode. Even though I gave  my Mac's user name, it wanted samba user name (which had to be a user in ubuntu machine, with a different password) .

I think since my usb drive is NTFS formatted, I could use samba, otherwise I am stuck with some other method. Will try it with a unix format file later.

Thanks luvshines' for your input.

---

