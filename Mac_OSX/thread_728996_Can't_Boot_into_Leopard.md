---
title: "Can't Boot into Leopard"
date: 2008-03-19
forum: Mac OSX
---

### Post by Black Mage on 2008-03-19
Hey, I'm having a problem with my Mac.

My Mac will not boot after the lastest update, it just hangs at the initial start-up. So I did a cmd -V to see what could be causing the problem, and it goes into a loop with this message:

code
mDNSResponder mDNSResponder 153:starting
sandbox-compilerd[5]: find compiler pthread_condPtimewait e=60
sandbox-compilerd[5]: bootstraop_look_up_per_user failure (kr=49, duration =18.829517) unknown error code
mDNSResponder[5]: WARNING: sandbox_init_error Cannot apply profile '(version 1)\n\n; WARNING: The sandbox rule....': Connection refused
mDNSResponder[5]: SessionGetInfo(0 xfffffff) - > Mach 1102
/usr/sbin/mDNSResponder[5]: SessionGetInfo(0 xfffffff) - > Mach 1102
/usr/sbin/mDNSResponder[5]: SessionGetInfo(0 xfffffff) - > Mach 1102
mDNSResponder163 mDNSKeyChainSecrets: could not copy keychain default
mDNSResponder163setDomainSecrets: mDNSKeyChainSecrets failed eeor 2313 CFArrayRef 0000000000
mDNSResponder163 Dameon start: mDNS_initFailed 226
mDNSResponder163 Daemon start: mDNSDaemonInitialize failed

[/code]

Has anyone had this problem or possibly know how to get around it?

---

### Post by Infinite Recursion on 2008-03-23
Hrm, I've seen problems with booting after an update (especially after the massive 10.5.2 update), but I haven't had anyone go into Verbose mode as you did.  The best recommendation I have for resolving this is to run Disk Utility's "Repair Disk" from the OS X installation CD.  That has usually resolved update-related startup problems in the past for me.

---

### Post by handy on 2008-03-24
[***_DiskWarrior_***]("http://www.alsoft.com/DiskWarrior/") may save you?

---

