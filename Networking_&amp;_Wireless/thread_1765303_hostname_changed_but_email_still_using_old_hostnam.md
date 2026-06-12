---
title: "hostname changed but email still using old hostname"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by abubin on 2011-05-22
Hi,

I have an ubuntu 10.04 server with hostname "abc.domain.com". However, due to migration, we had to change to hostname to something else, "xyz".

I have done changing /etc/hosts and /etc/hostname and run /etc/init.d/hostname start.

Checking the hostname and all shows it is now using hostsname of xyz. However, email sending out is still using old hostname. We have some scripts that will send out alerts like failed rsync or hdd space full to my email account. But I see the sender is still "root@abc.domain.com".

How do change that to xyz? I am using postfix. I have edited main.cf and restarted postfix but no go.

---

### Post by abubin on 2011-05-22
ah...found the solution

anyone having similar problem can do this:

dkpg-reconfigure postfix

---

### Post by samhamilton on 2011-09-25
> **abubin said:**
> ah...found the solution

anyone having similar problem can do this:

dkpg-reconfigure postfix

Small correction for the typo, the command is dpkg-reconfigure postfix

---

