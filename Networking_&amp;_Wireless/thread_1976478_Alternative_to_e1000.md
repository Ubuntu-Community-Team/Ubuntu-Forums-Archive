---
title: "Alternative to e1000?"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by lordbah on 2012-05-08
With the upgrade to 12.04 I can no longer recompile the e1000 driver, as I have done for the past dozen or so releases in order to get it to make a Gigabit connection. (I had to build it with a flag to force master mode). Do I have any other driver option for Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)?

---

### Post by chili555 on 2012-05-08
I am a curious student but, by no means an expert, on various Intel drivers. I am not aware of an alternative to e1000. I have started my research here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/309211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/309211)

Does it help if you add the driver parameter to the built-in e1000?```
sudo modprobe -r e1000
sudo modprobe e1000 AutoNeg=0x28
```

---

### Post by lordbah on 2012-05-08
The modprobe -r never returns. syslog says a task blocked for more than 120 seconds and has a stack trace showing e1000_down_and_stop -> cancel_work_sync -> ... rb_erase -> dequeue_entity. I can grab the whole thing if you think it'll help - it's just more tedious without a working network.

---

### Post by chili555 on 2012-05-08
I wonder if you have to down the interface first. If you haven't already, I'd get out of 'modprobe -r' with Ctrl+c. Then try:```
sudo ifconfig eth0 down
sudo modprobe -r e1000
sudo modprobe e1000 AutoNeg=0x28
sudo ifconfig eth0 up
```Then I'd look for gigabit connection clues in ethtool and dmesg.

---

### Post by lordbah on 2012-05-08
The ifconfig down hangs. syslog shows warning at e1000_main.c:1447 in e1000_close, but I don't see where it says what it is warning about. It has a line about "ifconfig Tainted", then a call stack which has e1000_close -> warn_slowpath_common -> printk.

---

### Post by chili555 on 2012-05-08
Yikes! Is this a result of a failed e1000 compile or...?? Anything interesting here?```
dmesg | grep e100
```If it's easier, you can put it here and give me the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Thanks.

---

### Post by lordbah on 2012-05-08
syslog: [http://paste.ubuntu.com/977195/](http://paste.ubuntu.com/977195/)
dmesg.txt: [http://paste.ubuntu.com/977197/](http://paste.ubuntu.com/977197/)

---

### Post by chili555 on 2012-05-09
Yikes again!!! I see lots of these:> [   60.927052] init: udev-fallback-graphics main process (1198) terminated with status 1
[   61.909271] init: atd main process (1287) terminated with status 1
[   61.909316] init: atd main process ended, respawning
[   61.927200] init: gdm main process (1349) killed by TERM signalAnd these:> [   77.665634] init: nmbd main process (2481) terminated with status 1
[   77.665685] init: nmbd main process ended, respawning
[   77.706916] init: nmbd main process (2499) terminated with status 1
[   77.706962] init: nmbd main process ended, respawning
[   77.741892] init: nmbd main process (2506) terminated with status 1
[   77.741937] init: nmbd main process ended, respawning
[   77.770242] init: nmbd main process (2511) terminated with status 1
[   77.770288] init: nmbd main process ended, respawning
[   77.799168] init: nmbd main process (2516) terminated with status 1
[   77.799213] init: nmbd main process ended, respawning
[   77.827449] init: nmbd main process (2521) terminated with status 1
[   77.827492] init: nmbd main process ended, respawning
[   77.856392] init: nmbd main process (2526) terminated with status 1
[   77.856435] init: nmbd main process ended, respawning> [   88.297059] init: ssh main process (3146) terminated with status 255
[   88.297100] init: ssh main process ended, respawning
[   88.313172] init: ssh main process (3149) terminated with status 255
[   88.313221] init: ssh main process ended, respawning
[   88.331655] init: ssh main process (3152) terminated with status 255
[   88.331705] init: ssh main process ended, respawning
[   88.347440] init: ssh main process (3155) terminated with status 255
[   88.347494] init: ssh main process ended, respawningAnd, as well, e1000 can't be unloaded and reloaded at all. In a properly operating system, it is drama-free.

I see other less-serious messages as well.

If you Google some of these errors, you will see it is indicative of a system with some possibly serious errors that need correcting. It is well beyond the scope of e1000 and networking and well beyond my expertise.

I suggest you dig deeper over on General Help. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by lordbah on 2012-05-15
I burned a 12.04 CD and booted from it on the problem system. It makes the same lousy 10 Mb/s connection, but does not show the crashes/tracebacks. After modprobe e1000 AutoNeg=0x28, it will not connect ("link is not ready"). That matches my recollection of what would happen in the days before I began rebuilding the e1000 driver with MASTER=1.

Next I tried a different Intel NIC, PWLA8391GT, and got the same results, 10 Mb/s only. Came to find out that lspci identifies this board as 82541PI, same as my old board. I think I've been wasting time with this second board, testing the exact same thing, caught by the fact that the model number sold is not what is reported by lspci.

So I'm ready to throw money at the problem. Who's got a PCI card (not PCI-E) which will make a gigabit connection with a NetGear GS105 switch on Ubuntu 12.04 out of the box? It no longer matters to me if it's not made by Intel.

---

### Post by bomski on 2012-07-20
Hi lordbah; did you ever find a fix for the e1000 driver issue? I have a Dell poweredge 2800 which is unable to achieve gigabit speed on 12.04...

---

