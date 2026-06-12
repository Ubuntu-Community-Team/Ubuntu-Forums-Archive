---
title: "ATI Binary Drivers -- problems"
date: 2008-09-23
forum: Multimedia Software
---

### Post by bjtuna on 2008-09-23
I have an ATI Radeon XPress200 and I am trying to install the latest (Catalyst 8.9) ATI fglrx drivers using the instructions for Hardy at 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

and when I reach the last step, I get an error:

```

sudo aticonfig --input=/etc/X11/xorg.cnf --tls=1
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  147 (ATIFGLEXTENSION)
  Minor opcode of failed request:  7 ()
  Serial number of failed request:  8
  Current serial number in output stream:  8


```

Any ideas? I'm kinda afraid to reboot now....

---

### Post by bjtuna on 2008-09-23
Quick update:  I rebooted and it works.  Hmm.

---

### Post by markbuntu on 2008-09-23
There is a typo in that command. It should be xorg.conf, not xorg.cnf.

---

### Post by bjtuna on 2008-09-23
That has nothing to do with the problem I was seeing. I got the same error if I typed 'aticonfig --help'.

It's okay, the problem was resolved upon reboot, and I will be reporting the bug to ATI when I get a chance.


> **markbuntu said:**
> There is a typo in that command. It should be xorg.conf, not xorg.cnf.

---

