---
title: "Always disable wireless in Jaunty"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by iyepb0 on 2009-05-16
Hello everyone,

I need a few clue here.
I just upgrading my Ubuntu to 9.04 then compiling new kernel 2.6.29 using this tutorial [http://ubuntuforums.org/showthread.php?p=3912290]("http://ubuntuforums.org/showthread.php?p=3912290") 
Because i had a problem with booting here [http://ubuntuforums.org/showthread.php?p=7256166]("http://ubuntuforums.org/showthread.php?p=7256166")

But, my wireless card now is always disable, even if i turn on the kill switch.

I've tried this trick
[http://ubuntuforums.org/showpost.php?p=4871564&postcount=18]("http://ubuntuforums.org/showpost.php?p=4871564&postcount=18")
Still not working after boot. I always need to modprobe the driver to make it work.

Anyone with clue?

Thank you

Regards,
iyepb0
Open Source Your Mind

---

### Post by iyepb0 on 2009-05-18
Got It!!!

Try wicd: sudo apt-get install wicd

thanks

---

