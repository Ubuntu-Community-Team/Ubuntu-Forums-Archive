---
title: "Easytether SIOCSIFADDR error"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by tidmarsh on 2011-08-24
This morning when the campus network was out, I tried to tether my Android phone to my laptop running Ubuntu 11.04. The "easytether connect" command worked fine, but when I ran the "sudo dhclient easytether0" command in a separate window, I got a "SIOCSIFADDR error."

A quick search turned up [a previous thread]("http://ubuntuforums.org/showthread.php?t=1530546"), which reported a similar error and was marked as [SOLVED], but the steps outlined there did not fix my problem. A google search for "siocsifaddr" directed me to two [blog]("http://muffinresearch.co.uk/archives/2008/07/13/vmware-siocsifaddr-no-such-device-eth0-after-cloning/") [entries]("http://blog.kabisa.nl/2009/12/11/xen-how-to-fix-siocsifaddr-no-such-device/") describing problems with SIOCSIFADDR errors in a slightly different context. In one case the error was caused my an incorrect MAC address in /etc/udev/rules.d/z25_persistent-net.rules and in the other by an incorrect MAC address in /etc/udev/rules.d/70-persistent-net.rules.

One solution involved erasing everything in the persistent-net.rules file, one involved renaming the file, and a third involved editing the file. After a full shutdown, the problem was reported to go away.

I navigated to /etc/udev/rules.d and found 70-persistent-net.rules.

The least destructive (and most easily reversible) method seemed to me to rename the rules file, so I typed
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.old
```to rename the old file, and then shut down the computer.

When I rebooted, lo and behold, easytether worked just fine and the 
SIOCSIFADDR error disappeared.

Hopefully these instructions might save someone the hour or so it took me to diagnose and fix my problem.

---

### Post by praseodym on 2011-08-24
Hello,

just a tip/question:

a new "70-persistent-net.rules"-file can be applied by:

```
sudo udevadm trigger
sudo service udev reload
```
Maybe the "shutdown/reboot"-procedure is obsolete?!

---

### Post by tidmarsh on 2011-08-24
Vielen dank!

I'll try to remember that if I have this problem again.

---

