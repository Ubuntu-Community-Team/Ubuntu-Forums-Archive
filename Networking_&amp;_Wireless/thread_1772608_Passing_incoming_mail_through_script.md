---
title: "Passing incoming mail through script"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by ash_n on 2011-05-31
Hi there,

I'm running Postfix and everything is working fine, except for this.

In my /etc/aliases file, I have the following set:
```

<user>: <user>, "|/usr/local/bin/mailing/<user>.sh"

```When I try sending mail to <user> through Gmail, I get the following error in Gmail:

```

<[EMAIL="support@tuiimage.net"]<user>@<mydomain>[/EMAIL]>: Command died with status 2:
    "/usr/local/bin/mailing/<user>.sh". Command output:
    /usr/local/bin/mailing/<user>.sh: 4: cannot create log: Permission denied

```The mail still gets through to the user's inbox but I'm guessing there are some permission issues preventing execution of the script. The script simply contains:

```

!#/bin/bash
touch tmp

```Thanks in advance,
Ash

---

