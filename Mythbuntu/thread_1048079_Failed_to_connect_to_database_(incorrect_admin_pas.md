---
title: "Failed to connect to database (incorrect admin password)"
date: 2009-01-23
forum: Mythbuntu
---

### Post by ian dobson on 2009-01-23
Hi,

On my backend when I try to update using apt-get update -V, I'm seeing the following error:-

```

Setting up mythtv-database (0.21.0+fixes19789-0ubuntu0+mythbuntu2) ...
Failed to connect to database (incorrect admin password)
Failed to create or modify database (incorrect admin username/password?)

```

I then run sudo dpkg-reconfigure mythtv-database and reconfigure the admin user and password but the error keeps on poping up whenenver apt tries to upgrade mythtv-database. Myth works and I'm 100% sure that the password I entered is correct.

Anyone got any ideas?

Regards
Ian Dobson

---

### Post by klc5555 on 2009-01-23
> **ian dobson said:**
> Hi,

On my backend when I try to update using apt-get update -V, I'm seeing the following error:-

```

Setting up mythtv-database (0.21.0+fixes19789-0ubuntu0+mythbuntu2) ...
Failed to connect to database (incorrect admin password)
Failed to create or modify database (incorrect admin username/password?)

```

I then run sudo dpkg-reconfigure mythtv-database and reconfigure the admin user and password but the error keeps on poping up whenenver apt tries to upgrade mythtv-database. Myth works and I'm 100% sure that the password I entered is correct.

Anyone got any ideas?

Regards
Ian Dobson

Maybe your password is correct but the user is wrong: even though you're running the command "sudo", try "mythtv" as the username instead of "root" (if you haven't already tried this) and see if it gives better luck.

All the best. :)

---

