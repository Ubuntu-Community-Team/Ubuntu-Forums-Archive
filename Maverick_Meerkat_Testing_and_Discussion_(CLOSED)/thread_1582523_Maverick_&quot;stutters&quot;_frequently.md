---
title: "Maverick &quot;stutters&quot; frequently"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pmateti on 2010-09-26
I have Lucid and Maverick, both Kubuntu, installed on separate partitions.  Both updated to current packages (Sep 26, 2010). Every thing/device in Lucid works fine.

Maverick "stutters" frequently.  It happens in all KDE, KDE+openbox, LXDE.  Some examples:

(i) In a command shell, I type "ls", several seconds later you see the output.  I have top running in another window.  Load average below 0.90.

(ii) In a multitab browser, I click on a tab.  Does not get raised for several seconds.

There are no suspicious messages in dmesg/ messages/ syslog/ kernlog.

What is happening?  I saw other messages about mouse freezing etc.  In my case, the mouse pointer never stops responding to mouse movement. The clicks, however, are ignored several times.

System: Biostar N61PB-M2S, AMD Athlon 64 X2 4600+, 2x2GB RAM, etc. uname -a => Linux sunshine 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

---

### Post by kerry_s on 2010-09-26
i'm running unity.
everything was fast, then after updates things got slow.
just wait it out, hopefully the next updates will fix.

---

### Post by BwackNinja on 2010-09-26
try adding "intel_idle.max_cstate=0" to your boot parameters.

---

### Post by kerry_s on 2010-09-26
> **BwackNinja said:**
> try adding "intel_idle.max_cstate=0" to your boot parameters.

what are you doing? you don't even know if he has intel. do you even know what that does? are you just assuming he has a acpi problem?

---

### Post by pmateti on 2010-09-27
I added details re my system.

---

### Post by NightwishFan on 2010-09-27
Back in an earlier beta I found my touchpad went out of sync. I believe it was a 2.6.35 kernel issue as 2.6.34 works. It seems to have been fixed for me in updates. When things stutter, try switching to a virtual console and back. (ctrl+alt+5 then ctrl+alt+7(or 8 sometimes)

---

### Post by BwackNinja on 2010-09-27
> **kerry_s said:**
> what are you doing? you don't even know if he has intel. do you even know what that does? are you just assuming he has a acpi problem?

I've seen a few threads here and there involving a laggy desktop with actions happening slowly, unless for example the mouse is moving. This workaround is associated with [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702) but now that he has posted his specs, the option would not help because he has an AMD processor not an Intel one. I do actually know what the option does, it disables the intel_idle module and allows the system to use the acpi_idle module instead (which had been used previously for affected processors). The intel_idle module was added/enabled in 2.6.35-18 or -19, and has caused problems for some people, including not being able to boot for some or a laggy desktop for others. I personally had the latter problem. The module itself does better power management for the processors it affects when idle, so it can go into a deeper sleep, be cooler, and use less power. The workaround is even mentioned on the git commit associated with adding intel_idle to the kernel.

---

### Post by psychok7 on 2010-10-02
> **BwackNinja said:**
> try adding "intel_idle.max_cstate=0" to your boot parameters.

what is boot parameters? i try adding this line when the boot drops to a shell or something. but it says /bin/sh: intel_idle.max_cstate=0 not found..

please help

---

### Post by BwackNinja on 2010-10-02
> **psychok7 said:**
> what is boot parameters? i try adding this line when the boot drops to a shell or something. but it says /bin/sh: intel_idle.max_cstate=0 not found..

please help

First, note that this ONLY applies to INTEL processors (and only some of them). The boot parameters are the extra options passed through grub. If you are using grub2, it is the "linux /boot/vmlinuz-...etc" line. You can try to see if this fixes things for you by just pressing 'e' at the grub menu when you have the correct item you want to edit selected, and add "intel_idle.max_cstate=0" (no quotes of course) to the end of that line after it says "quiet splash". ctrl+x to boot that entry after you're done editing.

With grub1, it is the same thing except the line starts with "kernel /boot/vmlinuz-...etc" and you press 'b' to boot the modified entry.

---

### Post by psychok7 on 2010-10-10
> **BwackNinja said:**
> First, note that this ONLY applies to INTEL processors (and only some of them). The boot parameters are the extra options passed through grub. If you are using grub2, it is the "linux /boot/vmlinuz-...etc" line. You can try to see if this fixes things for you by just pressing 'e' at the grub menu when you have the correct item you want to edit selected, and add "intel_idle.max_cstate=0" (no quotes of course) to the end of that line after it says "quiet splash". ctrl+x to boot that entry after you're done editing.

With grub1, it is the same thing except the line starts with "kernel /boot/vmlinuz-...etc" and you press 'b' to boot the modified entry.

for some reason i couldnt mount the partitions with a live cd to fix it..anyways the final release is out is the fix for the problem already there?

---

