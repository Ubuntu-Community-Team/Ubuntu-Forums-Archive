---
title: "Mythweb php errors"
date: 2012-01-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-06
Just clean installed mythbuntu 11.10 and I'm seeing the following errors/warnings when viewing the scheduling options and details for a show.

```
Warning at /usr/share/mythtv/mythweb/modules/tv/detail.php, line 310:
!!NoTrans: Invalid argument supplied for foreach()!!
```

```
Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:150)!!
```

Both seem to appear every time.

---

### Post by ubnewbie2 on 2012-01-06
Problem has gone away.  I think an update fixed it.  Sorry, don't know which one.

---

