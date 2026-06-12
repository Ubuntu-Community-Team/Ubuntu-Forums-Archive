---
title: "Unlock Login Keyring when launching Gwibber or Empathy"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Ender985 on 2010-05-16
Hey all,

I'm not sure if this is the correct section to ask this question, so mods please move if needed.

This happens with a freshly installed Lucid 64 bit, 2.6.32-22-generic kernel. Each time I boot into the system I get prompted for my password:

"Unlock Login Keyring

Enter password to unlock your login keyring

The login keyring did not get unlocked when you logged into your computer."


At first I thought it was the wireless network problem, so I already checked my wireless as "Available to all users", but this didn't stop the prompt. Doing a little bit more of research, if I cancel the dialog without entering my password, I can access the web without any problems (so again it is not the wireless connection problem), but then if I try to launch Gwibber I get the prompt again (two times actually, if I press Cancel the first time), or if I launch Empathy as well (three times in a row if I press Cancel; probably it has to do with the fact that I'm logged into 3 different accounts, facebook, gmail and hotmail?).

Furthermore, this two nice pieces of sofware offer almost zero configuration options to the user, at least GUI-wise, so there is no checkbox for "Available to all users" or anything simmilar for the matter. For instance, in gwibber I have spell-check turned on by default and there is no way to turn it off. So I guess I'll have to tweak some configuration file in some obscure folder, any guesses?


Thanks a lot!

---

### Post by Ender985 on 2010-05-17
C'mon, anyone?

---

### Post by DavidFourer on 2010-05-17
I found this in the in a Lucid beta testing forum from April 2010:
[http://ubuntuforums.org/showthread.php?t=1448143](http://ubuntuforums.org/showthread.php?t=1448143)

> look at your /etc/pam.d/gdm-autologin file, it should look like this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
session optional        pam_gnome_keyring.so auto_start
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
@include common-password
```
I found lines 6,10 missing.  I added them.
auth    optional        pam_gnome_keyring.so
session optional        pam_gnome_keyring.so auto_start

I rebooted and all seems fine so far.
Can anyone explain this?  

I have also read comments about wifi connection causing this.  Some people say don't connect wifi on start-up and that fixes it.  Did not work for me.

---

### Post by Ender985 on 2010-05-17
Yep that worked for me, thanks!

Even though I find it wierd that this strange behavior was spotted in the Lucid beta and was not fixed for release. For the record, I am using an autoconnecting wirless network, as well as autologin. Lines #6 and #10 of /etc/pam.d/gdm-autologin were also missing for me, adding them stopped the prompt at login.

---

### Post by daveysan on 2010-06-02
That worked for me too - thanks for that. I don't use wireless on my Lucid PC, but following your instructions the problem went away. Thanks for that!

---

### Post by hunt.topher on 2010-06-11
> I found lines 6,10 missing.  I added them.
auth    optional        pam_gnome_keyring.so
session optional        pam_gnome_keyring.so auto_start

I rebooted and all seems fine so far.
Can anyone explain this?  

I have also read comments about wifi connection causing this.  Some people say don't connect wifi on start-up and that fixes it.  Did not work for me.

Hm, to me it looks like those lines get deleted if you change settings to auto-login. When I switched to autologin, the keyring prompt started appearing, which I found highly annoying, so I turned autologin off, but the keyring did NOT automatically unlock with logon now; the prompt stayed. Thanks for this fix!

---

### Post by woodbrick on 2010-06-25
Thanks for this post. Very helpful. This is the most annoying feature of Lucid and this is a far better fix than is suggested in other posts; which is to save the keyring password as blank.

---

### Post by DavidFourer on 2010-06-25
I eventually had to get rid of auto-login.  See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/555342]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/555342")

---

### Post by woodbrick on 2010-07-07
The solution posted here:

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

by bishop9226 worked for me.

---

