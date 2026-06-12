---
title: "Thunderbird failure to connect"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by snakep on 2009-05-19
Hello,

I have a new problem with my Thunderbird.  Since this morning, I get this message when I try to download my mail:

```
Failed to connect to server pop.gmail.com.
```

I have checked the settings in Thunderbird, and they are as they should be to download from gmail.  Also, nothing in the account has changed, and it was working fine until today.  My internet connection is working fine, and I can log in to the web-based version of my gmail account.

I have installed some updates recently, but it has been at least a week since I installed any Thunderbird updates.

Does anybody have an idea what the problem could be?

Thanks,
Jeremiah

---

### Post by rmikio on 2009-06-29
Same problem here.
It seems that Thunderbird 2.0.0.22 at ubuntu Jaunty 9.04 64-bit is not able to see the Internet connection, although it exists.
I tried to configure a REAL account and a FAKE one. both of them returned the same message. Not only Google, but it happens to other servers as well.
I have executed Thunderbird manually as root also in order to check if there were permission problem, but the problem persists.
I will try some other things, but I am really a NEWBIE. So, if some expert is available, we could use some help here.
Oh.. And before someone ask: YES, I have configured the e-mail servers (incoming and outgoing) as recommended by GMail, including the SSL security issues. And NO, I am not using IMAP, only POP.

Thank you and regards,
RM

---

### Post by Failbot on 2009-06-29
Sorry, can't really offer any useful advice, except to say I've been using Thunderbird to check multiple gmail accounts for a couple of years without any problems, or setting changes. I use POP3, but IMAP has worked whenever I've set it up.

Currently running Jaunty 64bit, Thunderbird 2.0.0.22, all updates installed.

Only thing I can suggest is if you need to use proxy settings then you'll need to configure Thunderbird to use them.

---

### Post by zwei_zucker on 2009-08-18
I have the same problem ! what's weird is that firefox connect without problem but, Thunderbird 2 don't see my Internet Connection ( wireless btw ). My Evolution client work without any problem ! Someone have fix this yet ?

---

### Post by JoshStrobl on 2009-08-18
I've never had that problem with my Mozilla Thunderbird and I have like...5 emails going to search for mail every minute. The easiest solution I'd say would be:
1. Record your information (is in username, password, POP3 settings, etc) temporarily.
2. Uninstall Thunderbird
3. Reinstall and put the settings back in and check mail 
:popcorn: Hope it works.

---

### Post by sahabcse on 2009-08-18
Hi

Try to reinstall thunder after taking the backup of mail and profile

For backup and restore follow below url

[http://ubuntulinux.co.in/backup-thunderbird-mail.php](http://ubuntulinux.co.in/backup-thunderbird-mail.php)

---

### Post by zwei_zucker on 2009-08-24
Thanks all ... reinstalled Thunderbird, reboot, up and running now :) sorry for not replying sooner !

---

