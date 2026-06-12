---
title: "Catalyst 8.02  - Guild Wars problem"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by mafiatfc on 2008-02-19
I have the Catalyst 8.02 (8.455.3 I believe) installed but Guild Wars will not work.  My card is a X300 and direct rendering and such is working.  The issue I have is Guild Wars worked with a previous ATI fglrx driver from the repos, but not the new driver.

Here is what I get.

err:ntdll:RtlpWaitForCriticalSection section 0x7e608640 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0045, blocked by 0033, retrying (60 sec)
err:seh:setup_exception stack overflow 380 bytes in thread 0045 eip 7efadd58 esp 72525e84 stack 0x72526000-0x72636000

Anyone know why this is?

---

