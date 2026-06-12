---
title: "ndiswrapper driver shows available networks but doesn't connect"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by charrah on 2009-08-29
Hi, I'm using Ubuntu Jaunty on x86. My wireless adapter is a Belkin F5D7050 (lsusb gives it an ID of 050d:705e). I noticed that when using Windows I'll never have any wireless problems, but on Linux there will be a few spans in any given day when I'll be unable to do anything online, and occasionally I'll get a bunch of messages in Pidgin about messages possibly not being sent- so I assumed this was because the proprietary Windows driver was better somehow.

So I tried installing the Windows driver with ndiswrapper and it was able to tell me what networks were available, their signal strength, and their encryption level, but when trying to connect it would just try for a few minutes, then ask me if I typed the password right (I know I did, because when I switch back to the Linux driver it is at least possible to connect).

What should I try to make this work? I noticed a bug report for this kind of thing for ndiswrapper, but none of the workaround posted worked for me (I installed ndiswrapper from source, used wicd as my network manager, tried unplugging/replugging adapter, and running the command they gave, but to no avail.

---

### Post by w00ly on 2009-08-29
I had the same problem you mentioned here: [http://ubuntuforums.org/showthread.php?t=1252816](http://ubuntuforums.org/showthread.php?t=1252816) You can find my solution at the bottom but basically there's a module conflicting with ndiswrapper over the wireless device and dhcp wont pull an IP. Just add > blacklist *modulename* to the bottom of /etc/modprobe.d/blacklist.conf 
You might be lucky and the module name be what it says in lshw -c Network under the driver section, but mine showed rt2500usb (which it's always been called...) but if after blacklisting that module you still cant connect, try to find a similar module name with one of the other commands and blacklist that...good luck :)
Seems like the ndiswrapper gtk program (windows wireless drivers) should do this itself but mine didnt

---

### Post by charrah on 2009-08-29
Well I'm pretty sure the module is called rtl8187; I always *rmmod* or *modprobe -r* it before I load the ndiswrapper module. But maybe one of its dependencies is what's causing the issue here so I'll try it and post results.

---

### Post by charrah on 2009-08-30
If I blacklist rtl8187 then it doesn't see any wireless networks until I load the ndiswrapper driver, but it has the same issue. Adding e100 to the blacklist does... nothing. e100 is still listed in lsmod, and it doesn't show a dependency on another driver, so I don't know how that works. Where should I look for other possibilities of what to blacklist?

---

### Post by greg0ry on 2009-09-01
Perhaps we have a common problem.
[http://ubuntuforums.org/showthread.php?t=1245187](http://ubuntuforums.org/showthread.php?t=1245187)

The output of 'sudo lshw -C network' should show you which driver/module is controlling your wireless interface. Somewhere it should read "driver=ndiswrapper+...".

The output of 'lsmod | grep -e ndis -e rtl8187' should show if ndiswrapper is running and that rtl8187 is indeed blacklisted. Only ndiswrapper should be listed in the output.

If these are the case, you shouldn't have to blacklist anything else.

My apologies if I told you what you already know. Or if I am dead wrong.;)

I personally am still without solution.

---

### Post by charrah on 2009-09-19
Sorry I waited so long to respond; I was unable to get ndis working. The driver shown in lshw was different but unloading it didn't help.

---

