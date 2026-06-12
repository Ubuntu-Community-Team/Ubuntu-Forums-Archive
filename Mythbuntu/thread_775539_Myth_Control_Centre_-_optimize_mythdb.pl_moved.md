---
title: "Myth Control Centre - optimize_mythdb.pl moved?"
date: 2008-04-30
forum: Mythbuntu
---

### Post by jb5 on 2008-04-30
Hi - First let me explain the upgrade path for this installation.

Clean install of Gutsy.
Install Myth 0.20
Upgrade to Myth 0.21 (via gutsy-backports)
Upgrade to Hardy.

OK after a few teething problems got my system working well again. One of the few remaining issues is :-

From within Myth Control Centre (MCC) - when I click optimize tables button, instead of opening a terminal and running the script as used to happen now a terminal opens and shuts almost immediately!

After some digging, it seems that the script has moved from where it should be :-

```
/usr/share/doc/mythtv-docs-0.21/contrib/optimize_mythdb.pl

to

/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```

(I'm typing this on another computer so I hope the "-" & "_" are in the right places!)

So first, should this have happened, and second, is there an easy way to change where the optimize tables button in MCC points to?

---

### Post by superm1 on 2008-04-30
> **jb5 said:**
> Hi - First let me explain the upgrade path for this installation.

Clean install of Gutsy.
Install Myth 0.20
Upgrade to Myth 0.21 (via gutsy-backports)
Upgrade to Hardy.

OK after a few teething problems got my system working well again. One of the few remaining issues is :-

From within Myth Control Centre (MCC) - when I click optimize tables button, instead of opening a terminal and running the script as used to happen now a terminal opens and shuts almost immediately!

After some digging, it seems that the script has moved from where it should be :-

```
/usr/share/doc/mythtv-docs-0.21/contrib/optimize_mythdb.pl

to

/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```(I'm typing this on another computer so I hope the "-" & "_" are in the right places!)

So first, should this have happened, and second, is there an easy way to change where the optimize tables button in MCC points to?
Can you file a bug against mcc in Hardy?  We'll see what we can do about a fix at some point.

---

### Post by jb5 on 2008-04-30
OK done, (correctly I hope)!

[Bug reprot](https://bugs.launchpad.net/ubuntu/+bug/224780)

---

### Post by markofealing on 2011-07-29
Just to keep us on our toes, the scrips have been moved again in MythTV 0.24 (Mythbuntu 11.04) and can now be found in: 

**/usr/share/doc/mythtv-backend/contrib/maintenance**

You can run the script from this directory by entering

**perl optimize_mythdb.pl**

Unfortunately the MythTV wiki still points to the old location!

---

