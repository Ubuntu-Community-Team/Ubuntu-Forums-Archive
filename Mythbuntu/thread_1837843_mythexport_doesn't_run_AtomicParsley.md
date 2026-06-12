---
title: "mythexport doesn't run AtomicParsley"
date: 2011-09-02
forum: Mythbuntu
---

### Post by melevittfl on 2011-09-02
Hi,

I've got mythexport installed and it is transcoding files. However, it is not setting the metadata with AtomicParsley. 

I've been trying to figure out why, but I've looked through the mythexport Perl code and can't even see where it tries to call AtomicParsley.

So,  can anyone point me to where mythexport calls AtomicParsley?

Thanks,
Mark

---

### Post by rhpot1991 on 2011-09-11
Unfortunately this is a side effect of the new configuration method.  The main daemon used to run this, but all external commands have been moved to a configuration.  The configuration doesn't currently know the information that AtomicParsley needs, so you will have to re-add AtomicParsley to the daemon if you want it to run.

You should be able to figure out what to re-add from here: [http://bazaar.launchpad.net/~mythbuntu/mythexport/trunk/revision/93#usr/bin/mythexport-daemon](http://bazaar.launchpad.net/~mythbuntu/mythexport/trunk/revision/93#usr/bin/mythexport-daemon)

Go ahead and open up a bug here as well: [https://bugs.launchpad.net/ubuntu/+source/mythexport](https://bugs.launchpad.net/ubuntu/+source/mythexport)

---

### Post by shortbg on 2012-07-17
I did not see a bug report for this issue. Has there been any change in the status?

---

### Post by rhpot1991 on 2012-07-17
> **shortbg said:**
> I did not see a bug report for this issue. Has there been any change in the status?

Nope, the new config method does not handle this currently.

---

