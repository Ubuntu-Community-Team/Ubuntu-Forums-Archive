---
title: "Netgear WG111 v1 ndiswrapper"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by Travisty on 2006-05-31
I have been reading through the posts on the forum for over an hour and trying other peoples suggestions but I still can not get my adapter to work.

I am running the 64 bit version of Dapper and so far no one has mentioned what version they are running (32 or 64 bit). I think the problem is that I dont have a 64 bit driver.

I have ndiswrapper version 1.8 loaded with the driver netwg111 installed. Its telling me tha the driver and hardware are both present.

Here is the output of dmesg | grep ndiswrapper:
[   58.402186] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   58.447947] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[   58.447952] ndiswrapper (load_sys_files:218): couldn't prepare driver 'netwg111'
[   58.448344] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[   58.448348] ndiswrapper: probe of 2-8:1.0 failed with error -22
[   58.448359] usbcore: registered new driver ndiswrapper

Anyone have any ideas on how to get this to work?

---

### Post by eternalsword on 2006-07-14
Unfortunately, netgear has now 64-bit drivers.  You might want to try compiling acx from new source.  should work on dapper now.  see [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

