---
title: "Unable to load cut list"
date: 2007-11-16
forum: Mythbuntu
---

### Post by jackliddlephysics on 2007-11-16
Hello,

I'm playing around with my new mythbuntu install.  My problem is I don't seem to be able to load cut list from the commecial flagging.

I'm certain the commercial flagging has taken place.  For my test case I have rerun it and it claims to have flagged 2 commercials breals.

When I view the program and press 'e' to edit it claims no seektable, pressing 'z' doesn't seem to load the cut table.

Anyone able to see something I can't?

Thanks

---

### Post by superm1 on 2007-11-16
> **jackliddlephysics said:**
> Hello,

I'm playing around with my new mythbuntu install.  My problem is I don't seem to be able to load cut list from the commecial flagging.

I'm certain the commercial flagging has taken place.  For my test case I have rerun it and it claims to have flagged 2 commercials breals.

When I view the program and press 'e' to edit it claims no seektable, pressing 'z' doesn't seem to load the cut table.

Anyone able to see something I can't?

Thanks
Try to repair your mysql database.

---

### Post by jackliddlephysics on 2007-11-16
Excellent, that did it.

For future thread searchers it issued
```
mysqlcheck -r -u root -p  mythconverg
```

but I don't know if thats the best way to do things.

Thanks very much

---

