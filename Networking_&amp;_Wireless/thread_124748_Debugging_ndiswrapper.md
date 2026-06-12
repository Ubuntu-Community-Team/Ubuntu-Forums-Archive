---
title: "Debugging ndiswrapper"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by andy101 on 2006-02-02
I am having problems with ndiswrapper (it hangs during modprobe). I have altered /proc/sys/kernel/printk to make it print debug messages to the console (though only in safe mode). However it doesn't seen to put it into any of the log files. I even used grep to search all the log files for a phrase I knew was in the debug output. Anyone know how I can get this debug output written to a file as well as on screen? I think its the system logger not actually ndiswrapper that displays the messages on the terminal.

Any help will be much appreciated.

Thanks.

Andy.

---

