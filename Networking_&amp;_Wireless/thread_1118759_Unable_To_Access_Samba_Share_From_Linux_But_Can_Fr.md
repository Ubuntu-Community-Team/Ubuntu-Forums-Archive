---
title: "Unable To Access Samba Share From Linux But Can From Windows"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by nodrog1952iii on 2009-04-07
I have successfully installed Samba on several CentOS machines but I am having problems attaining complete success on a Ubuntu Hardy machine.  The Ubuntu machine's configuration file is very simple and looks like this:

[global]
       server string = Samba Server
       security = USER
       workgroup = workgroup
       log file = /var/log/samba/%m.log
       max log size = 50
       dns proxy = No

[pamuser]
       comment = Secure User's Home Directory
       path = /home/secureuser
       valid users = secureuser
       read only = No

[public]
       comment = Public file sharing space
       path = /home/public
       read only = No
       guest ok = Yes

This machine's name is ubuntu and it is within a network with several other Windows machines and one CentOS machine.  The pamuser is a passworded pam user. Samba runs successfully in this config except that I am unable to access the pamuser's share from the very same ubuntu machine using smbclient \\\\ubuntu\\pamuser.  Instead, the following error message appears (after password dialog) :

session setup failed: NT_STATUS_LOGON_FAILURE

Otherwise, the above config works fine in that I can access the ubuntu pamuser share from the other Windows and CentOS machines and I can also access shares on these other machines from the ubuntu machine.

Now, when I then change the security setting to security = SHARE then I am again able to access the pamuser ubuntu machine from all other Windows machines, however, I cannot access the pamuser share from the very same ubuntu machine or the CentOS machine.  With security = SHARE I get a different error message as follows:

tree connect failed: NT_STATUS_WRONG_PASSWORD

So, in summary, with security = USER, I can access the pamuser share from everywhere (Windows and CentOS) except from the very ubuntu machine where the pamuser resides.  Whereas, with security = SHARE, I can access the pamuser share from all Windows machines but not from the CentOS machine or the ubuntu machine where the pamuser resides.

I have already spent the better part of two days trying to figure this out and I have googled it to death.  I hope that a samba expert on this forum can offer a solution.

Many Thanks,

Gordon Dickens

---

### Post by superprash2003 on 2009-04-07
post output of cat /etc/samba/smbusers

---

### Post by nodrog1952iii on 2009-04-07
> **superprash2003 said:**
> post output of cat /etc/samba/smbusers

The content of my /etc/samba/smbusers file is:

pamuser = pamuser

Please let me know if you have any suggestions.

Thanks!

Gordon

---

### Post by nodrog1952iii on 2009-04-07
Hey Supertrash2003,

Sorry, I had previously done testing with and without the smbusers file, however, I just went back and retested and now everything is working from Ubuntu (with the smbusers file present) as long as security = USER.  However, I still get errors with security = SHARE.  I want to be able to view the ubuntu machine's shares, and access the public share without a password as well as access the pamuser share with a password, so I would like to be able to set security = SHARE. Otherwise, can this be configured with security = USER?

Thanks,

Gordon

---

