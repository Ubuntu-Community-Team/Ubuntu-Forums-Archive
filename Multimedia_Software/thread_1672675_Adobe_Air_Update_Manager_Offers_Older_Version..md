---
title: "Adobe Air Update Manager Offers Older Version."
date: 2011-01-21
forum: Multimedia Software
---

### Post by gencon on 2011-01-21
Using: Ubuntu Lucid

The Update Manager has placed me with an odd dilemma, it says that:

"adobeair (version 2.5.1.17730) will be upgraded to version 1:2.0.4.13090-1lucid1"

So 'updating' version 2.5 with version 1.2 !!

I think this has happened because Adobe Air updates itself (asking permission first of course) using it's own dialog box from time to time when I run BBC iPlayer Desktop.

What should I do, update or not?

Thanks.

---

### Post by blujay on 2011-02-07
The problem is that the partner repository has an epoch number in its version number.  It's an older version but the epoch indicates to apt that it's newer.

---

### Post by gencon on 2011-02-08
Thanks for the explaination. I'll just ignore the repository updates.

---

