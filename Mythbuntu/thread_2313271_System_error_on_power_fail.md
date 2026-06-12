---
title: "System error on power fail"
date: 2016-02-11
forum: Mythbuntu
---

### Post by nmw01223 on 2016-02-11
On my 14.04.3 / 0.27.6 system I am using ACPI wakeup. Since my (ASRock) motherboard will not restart on timer from soft power down, I am using the 'suspend' mechanism as described in [https://www.mythtv.org/wiki/ACPI_Wakeup](https://www.mythtv.org/wiki/ACPI_Wakeup). Basically this puts the m/c into suspend to RAM part way through the shutdown/reboot sequence, then when it wakes again it immediately reboots.

It works OK.

However, it means the m/c spends large amounts of time in suspend to RAM state, as opposed to truly powered down, so there is a good chance of short power failures (we live in the country, get lots) when in that state. It does come back up again, but having simulated this (power off and on again), a dialog always pops up on the desktop after boot saying 'Ubuntu has encountered an internal error - report?'.

I have two questions
 - is this serious, can it lead to system / disk corruption, or is it just that the system has detected the shutdown did not complete?
- if it is not serious, how can I hide the message?

(I have tried 'suspend to disk' but could not get it to work).

---

### Post by aelfric55 on 2016-02-11
Any time you have a dirty shutdown there's some danger of data corruption or even hardware component failure from the possible accompanying surges when the power is restored. If this is happening when the system is suspended, it must also be happening occasionally when the system is active, where the potential for data corruption/hardware failure is much greater. You might consider a UPS backup unit to keep  the system powered during the brief but frequent outages.

---

### Post by ian-weisser on 2016-02-11
> **nmw01223 said:**
> a dialog always pops up on the desktop after boot saying 'Ubuntu has encountered an internal error - report?'

Look in /var/crash for the crash file that the system wants to report.
The system will keep asking to report the *same* crash file until you say 'yes' or delete the crash file.
The information in that crash file will also tell you if the issue is serious or not. If in doubt, post the file here.

---

### Post by nmw01223 on 2016-02-13
Thats for your reply. The crash report merely says that failure occurred during suspend. The top of the file is:

```
ProblemType: KernelOops
Annotation: This occured during a previous suspend and prevented it from resuming properly.
Architecture: amd64
Date: Tue Feb  9 22:07:16 2016
DistroRelease: Ubuntu 14.04
ExecutablePath: /usr/share/apport/apportcheckresume
ExecutableTimestamp: 1447090102
Failure: suspend/resume
InterpreterPath: /usr/bin/python3.4
Package: linux-image-3.16.0-60-generic 3.16.0-60.80~14.04.1
ProcCmdline: /usr/bin/python3 /usr/share/apport/apportcheckresume
```

I think I will look into a small UPS as well, though.

---

