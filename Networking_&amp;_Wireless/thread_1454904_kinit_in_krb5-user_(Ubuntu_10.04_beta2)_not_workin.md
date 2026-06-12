---
title: "kinit in krb5-user (Ubuntu 10.04 beta2) not working"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by theoryl on 2010-04-15
Hi,

To use Kerberos, I installed the ssh-krb5 & krb5-user package in Ubuntu 10.04 beta 2, but when I call kinit, it gives the following error message:

No supported encryption types (config file error?) while getting initial credentials

Does anybody know what causes this error? I believe I have the correct /etc/krb5.conf and /etc/ssh/ssh_config (GSSAPIDelegateCredentials is set to 'yes'). Thank you


Regards,

---

### Post by chenel on 2010-05-03
I had this same problem.  The reason for me was that my KDC requires des-cbc-crc encryption, which is apparently deprecated as of 10.04.  After a Google search, I found:

"Please also note, that des-cbc-crc encryption is depreciated and, starting with Ubuntu 10.04, is no longer supported by default in the Kerberos libraries. For nfs4 to work, you need to add allow_weak_crypto = true  to /etc/krb5.conf"

on [this page]("https://help.ubuntu.com/community/NFSv4Howto").

Adding allow_weak_crypto = true as suggested to my /etc/krb5.conf fixed it.

Hope this helps.

---

### Post by theoryl on 2010-05-04
Hi,

Thank you for the help! I can confirm that adding 
'allow_weak_crypto = true' (without quotes)
under [libdefaults] section in /etc/krb5.conf works

Regards,

---

### Post by d0.higgs on 2010-07-02
Thank you very much for the tip.
I can confirm that adding this line, **allow_weak_crypto = true**, under *libdefaults* solved the problem.
Thank you again,

~d0.higgs

---

