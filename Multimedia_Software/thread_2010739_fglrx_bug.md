---
title: "fglrx bug"
date: 2012-06-26
forum: Multimedia Software
---

### Post by JBudOne on 2012-06-26
Hey guys! I finally got fglrx properly installed on my computer (Ubuntu 12.04 Precise; with the Mobility RadeonHD 3650). For a while I was running into a bug anytime I tried to run the installer; actually a lot of people ran into this similar situation too, but no solutions were posted online. So here's what I ran into, and the workaround I used to get it working.

**THE PROBLEM**

Anytime I try to install fglrx (either via `sudo apt-get install fglrx` or  System -> Additional Drivers -> ...), I would run into this error,
```

kernel includes at /lib/modules/3.2.0-25-generic-pae/build/include do not match current kernel.
they are versioned as "3.2.18"
instead of "3.2.0-25-generic-pae".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```



**THE FIX**

Note: run `uname -r` for your current kernel, for me its `3.2.0-25-generic-pae`
```

cd /lib/modules/3.2.0-25-generic-pae/build/include
grep -r '3.2.18' .

```

Each of these files listed should be backed up, and then replace every instance of '3.2.18' with '3.2.0-25-generic-pae'  . Then try installing fglrx again

Also a side note: I was hoping to instead add this to the cchtml wiki ( [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting) ) where this solution belongs, but apparently the troubleshooting page is locked for editing :(
Another side note: This solution is a WORKAROUND just to get fglrx working. I'm sure there's a reason that the versioning was listed off in those files, and that there must be a much better way to fix this.

---

