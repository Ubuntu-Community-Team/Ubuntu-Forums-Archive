---
title: "Disable channel icons? Generalized database cleanup?"
date: 2009-01-26
forum: Mythbuntu
---

### Post by mathog on 2009-01-26
Two quick questions:

1.  How does one disable the display of channel icons?  (Channel numbers are good enough.)

2.  Is there a way to have the Mythtv database do some sort of consistency check / generalized cleanup?

Thanks.

---

### Post by mathog on 2009-01-26
> **mathog said:**
> Two quick questions:

1.  How does one disable the display of channel icons?  (Channel numbers are good enough.)

2.  Is there a way to have the Mythtv database do some sort of consistency check / generalized cleanup?

Thanks.

Found 1.  It is in Utilities/Setup -> Setup -> Tv Settings -> Program Guide.

Still need an answer to the 2nd one though.

Thanks.

---

### Post by ian dobson on 2009-01-27
Hi,

I run this script once a week or so to cleanup/opimize the db:-

[http://www.adspeed.org/2007/01/mysql-shell-script-to-optimize-all.html](http://www.adspeed.org/2007/01/mysql-shell-script-to-optimize-all.html)

I just call it with ./optimize_db.sh  --optimizeAll

Regards
Ian Dobson

---

### Post by movieman on 2009-01-27
Mythweb has database optimise and repair options, though I've never used them.

---

