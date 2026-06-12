---
title: "Cannot access Ubuntu Samba server using Windows XP/7"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by killbuddy on 2011-03-04
I cannot access my Ubuntu samba server using windows XP or 7.  I keep getting prompted for a username/password.  I have created both a unix username with password and a samba username with the same password i used for the unix user.  When windows prompts me for the username/password i give it the same one i created on the samba server, but it still will not take it.  I know samba is running because i can view the shares but cannot access them without getting prompted for username/password.  I just have the one user for now while i am testing, but there will be more.  

I am using Ubuntu Desktop 10.04.

Thanks for the help in advance.

---

### Post by prshah on 2011-03-04
> **killbuddy said:**
> I keep getting prompted for a username/password.

I don't know how to do this via GUI, but you can do this through the terminal (Applications-Accessories-Terminal): ```
sudo vi /etc/samba/smb.conf
```

Then, locate your share (within []), and uncomment/enable the guest parameter```
guest ok = yes
```

You will need to reboot / restart samba service for changes to take effect```
sudo service samba restart
```

---

### Post by killbuddy on 2011-03-04
I will give that a try.

thanks

---

