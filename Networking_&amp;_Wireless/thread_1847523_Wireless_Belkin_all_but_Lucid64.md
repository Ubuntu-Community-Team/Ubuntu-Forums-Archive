---
title: "Wireless Belkin all but Lucid64"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by Unterseeboot_234 on 2011-09-20
I have English-locale Win7-64, Natty-64 and effortlessly install ndiswrapper, then the vendor-supplied CD ->Belkin N300 -> XP64 driver. Works great, fast transfer rate.

But when I installed ndisgtk on Lucid64, set to German language interface, I get no gui for Windows Wireless after it asks for password once and silently fails. No password dialog after that first effort, even with a reboot. The terminal starting of ndisgtk posts the following error.

```
(process:1782): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 53, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```



Any ideas? I have even tried to make sure I downloaded a German package, rebooted. I do not have internet access on the computer I am trying to fix and I use the launchpad debs, copy to speed stick, shutdown, restart. Trying to use the LiveCD as a repository does not work at all in Synaptic.

---

### Post by Unterseeboot_234 on 2011-09-21
Okay, I made a partition and installed Natty 11.04. The wireless almost works with USB Belkin N300 (on front panel socket only, rear panel gives RFI), and using a built NDISWrapper. The connection gets established. When I log onto the Internet I get a system crash. The screen goes black with a long list of interrupts and errors.

At this point I blame the CPU hexacore, although the Belkin N300 works very well with Win7-72, and on my single-core AMD box. Download speeds are 300kb. The Ubuntu LiveCD for Natty downloaded in 39 minutes on my single-core AMD.

At this point I am ready to try anything that 'works out of the box'. Does anyone have a USB solution that works on Natty without ndiswrapper?

---

