---
title: "N300 Belkin Micro USB adapter"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by sosaudio1 on 2012-01-31
OK. I know we have several threads on this, but, my intention here is to see if we can't make this thread THE GO TO thread for this product.

Here is the deal. I can't seem to get my N300 Micro USB working on Ubuntu 11.10 with the 3.0.0.15 generic kernel. I have have done the fix that rebuilds the kernel. [http://ubuntuforums.org/showthread.php?t=1743385]("http://ubuntuforums.org/showthread.php?t=1743385")That got me the ability to get to my router, but not to connect. At that time, it wouldn't pass authentication and kept kicking me back to "enter your password". It also would not connect to any neighboring un-secured networks.

Ndiswrapper (Ndisgtk), would not load the module. Blank error. 
Some people have had success with it and I think they are running the 32bit version vs 64bit which is what I am on. In the threads we have to be careful to explain how people got their systems to run and what system the running N300 (or any hardware for that matter) on whether it is 32bit or 64bit.

Since the first thread said that it was based on another thread, here [http://ubuntuforums.org/showthread.php?t=1515747]("http://ubuntuforums.org/showthread.php?t=1515747")I tried it as well....no joy here and the subsequent files that were built have been removed.

Just saw something about the latest 12.04 release. 
[https://answers.launchpad.net/ubuntu/+question/185669]("https://answers.launchpad.net/ubuntu/+question/185669")
Is that showing potential for this USB dongle, or do I need to move on?

Someone posted before to have a breakdown of the HOW-TO to get the N300 Belkin Micro to work. Here would be an opportunity...

What do you need from me to get this thread going?


Here are the particulars I have so far

Ubuntu 11.10
Kernel is 3.0.0.15
lsub says Belkin Product
ifconfig does not show anything

Thanks
Rich

---

### Post by sosaudio1 on 2012-01-31
bump

---

### Post by sosaudio1 on 2012-01-31
Saw someone else having problems with the 8192cu driver....didn't wanna hijack his thread but the commands asked for I did to try to shine some light on this problem.

dmesg | grep 819 gives me:```
$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880077c00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[   25.408193] MCE: In-kernel MCE decoding enabled.
[   25.551165] 8192cu: disagrees about version of symbol filp_open
[   25.551172] 8192cu: Unknown symbol filp_open (err -22)
[   25.551305] 8192cu: disagrees about version of symbol filp_close
[   25.551307] 8192cu: Unknown symbol filp_close (err -22)

```

uname -a gives me: ```
$ uname -a
Linux rich 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```


HELP!! Hate being tethered

Rich

---

### Post by sosaudio1 on 2012-02-01
> **sosaudio1 said:**
> OK. I know we have several threads on this, but, my intention here is to see if we can't make this thread THE GO TO thread for this product.

Here is the deal. I can't seem to get my N300 Micro USB working on Ubuntu 11.10 with the 3.0.0.15 generic kernel. I have have done the fix that rebuilds the kernel. [http://ubuntuforums.org/showthread.php?t=1743385]("http://ubuntuforums.org/showthread.php?t=1743385")That got me the ability to get to my router, but not to connect. At that time, it wouldn't pass authentication and kept kicking me back to "enter your password". It also would not connect to any neighboring un-secured networks.

Ndiswrapper (Ndisgtk), would not load the module. Blank error. 
Some people have had success with it and I think they are running the 32bit version vs 64bit which is what I am on. In the threads we have to be careful to explain how people got their systems to run and what system the running N300 (or any hardware for that matter) on whether it is 32bit or 64bit.

Since the first thread said that it was based on another thread, here [http://ubuntuforums.org/showthread.php?t=1515747]("http://ubuntuforums.org/showthread.php?t=1515747")I tried it as well....no joy here and the subsequent files that were built have been removed.

Just saw something about the latest 12.04 release. 
[https://answers.launchpad.net/ubuntu/+question/185669]("https://answers.launchpad.net/ubuntu/+question/185669")
Is that showing potential for this USB dongle, or do I need to move on?

Someone posted before to have a breakdown of the HOW-TO to get the N300 Belkin Micro to work. Here would be an opportunity...

What do you need from me to get this thread going?


Here are the particulars I have so far

Ubuntu 11.10
Kernel is 3.0.0.15
lsub says Belkin Product
ifconfig does not show anything

Thanks
Rich

Ongoing saga.....

Reinstalled Ubuntu 11.10 applied all updates while on wired network. Updated to latest kernel with updates after new, fresh install. Then followed this:
[http://ubuntuforums.org/showthread.php?t=1743385]("http://ubuntuforums.org/showthread.php?t=1743385")

Now it sees the network but won't authenticate and connect to the network. I have rebooted the router (down for 60 seconds) and retried no change. I have set it to AES only....rebooted the computer....and tried to connect no connection. 

Trying to find a unsecured router to connect to in the area and none exist yet. Going to try again this afternoon.

Someone suggested unplugging the USB dongle and then replugging it and that may fix. I will try when I get home and let you know.

Anything I should try?

---

### Post by sosaudio1 on 2012-02-01
> **sosaudio1 said:**
> Ongoing saga.....

Reinstalled Ubuntu 11.10 applied all updates while on wired network. Updated to latest kernel with updates after new, fresh install. Then followed this:
[http://ubuntuforums.org/showthread.php?t=1743385]("http://ubuntuforums.org/showthread.php?t=1743385")

Now it sees the network but won't authenticate and connect to the network. I have rebooted the router (down for 60 seconds) and retried no change. I have set it to AES only....rebooted the computer....and tried to connect no connection. 

Trying to find a unsecured router to connect to in the area and none exist yet. Going to try again this afternoon.

Someone suggested unplugging the USB dongle and then replugging it and that may fix. I will try when I get home and let you know.

Anything I should try?


BUMP BUMP...Running out of time to take it back. Really wanna figure out how to make this run so that I can say I did and help out.

Thanks everyone!!!!!!

---

### Post by sosaudio1 on 2012-02-01
> **sosaudio1 said:**
> BUMP BUMP...Running out of time to take it back. Really wanna figure out how to make this run so that I can say I did and help out.

Thanks everyone!!!!!!


The saga continues....its connected....but....at the expense of security. It took a while but when I disabled all security to the router, it connected.

Signal strength all over the map....and now it is gone...reattempted to attach..no joy...back to the tether....

OK so this is a step in a direction....What am I missing???

---

