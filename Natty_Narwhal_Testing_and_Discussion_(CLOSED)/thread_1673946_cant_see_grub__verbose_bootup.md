---
title: "cant see grub  verbose bootup"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-01-23
when i'm booting, the screen turn black till plymouth. So i've removed "quiet splash" to be able to see the verbose bootup, but the screen is always black. This is with natty i386 and nvidia 260.19.21 (compiz not installed)

---

### Post by efflandt on 2011-01-23
That is currently normal, although, background of that menu and blank screen is actually dark purple unless your screen is dim.  Natty has been the same for awhile in 64-bit with same video drivers.  That is apparently due to a **vt.handoff=7** kernel boot parameter that is included in grub.cfg even if you delete **quiet splash** from /etc/default/grub.

If you want to see boot messages while booting, you apparently have to do a (recovery) boot.  That was the only way I could tell why Kubuntu Natty was dropping into BusyBox when attempting to boot an installed system on USB (Kubuntu grub erroneously used root=/dev/sdc kernel parameter instead of a UUID, so wrong drive).

---

### Post by mc4man on 2011-01-23
> apparently due to a vt.handoff=7 kernel boot parameter 
The new grub should be removing that or one can do themselves
> grub2 (1.99~rc1-1ubuntu2) natty; urgency=low

  * Don't add vt.handoff=7 if splash isn't going to be used (LP: #700686).

The only ? may be if you get a low res or higher res text, usually have been getting a high one though sometimes get a lower res for reasons unknown here

---

### Post by ronacc on 2011-01-23
you can also safely remove vt.handoff=7 .

---

### Post by dino99 on 2011-01-23
Thanks guys,

have already found that handoff tip. My issues are not about resolution but about booting:

- need several tries to boot, generaly 3, as i get kernel panic (filled report against wrong lspci identication #689181) because of hard time when checking sata & usb.

- curiously grub countdown work only the first time, then it dont exist at all, even after a cold boot. So i suppose that the shutdown is in a bad state, or else.

Thats why i want to check the verbose mode on bootup, as this is not (sadly) logged.

---

### Post by mc4man on 2011-01-23
> My issues are not about resolution but about booting:

If you can get the higher res text than you might get more useful info when a panic occurs (more  lines visible

If you can get the EIP: then post it, I've never ever had a panic before natty on several machines - get one occasionally on 2 installs on vastly different hardware, the EIP is always the same on both. 
(started about a month ago.

---

### Post by dino99 on 2011-01-23
> **mc4man said:**
> If you can get the higher res text than you might get more useful info when a panic occurs (more  lines visible

If you can get the EIP: then post it, I've never ever had a panic before natty on several machines - get one occasionally on 2 installs on vastly different hardware, the EIP is always the same on both. 
(started about a month ago.

Sorry i've forgotten my decoder :( what is EIP ? Sadly there is no way to log the bootup time verbosing.

note: the kernel panic is due to: cant mount rootfs on unknown block, or so.

---

### Post by cariboo on 2011-01-23
I wonder if enabling the boot log, /var/log/boot,  would help in this case?

Go to /etc/default/boologd, and change no to yes.

---

### Post by mc4man on 2011-01-23
> what is EIP 
Honestly I  don't have a clue, as mentioned, before natty never had a panic so never spend any time reading up on (even if I did may not matter anyway
Someone I know who does know a bit more wanted that line and several more if I could provide. (haven't heard back yet

The only thing in common w/ the 2 machines that get these panic's is - 
both dual boot w/ maverick
both have nvidia
both use a custom kernel in maverick

Also I've found the likelihood of a panic is vastly increased when -  from a cold boot where the last boot was maverick or restarting from maverick into natty. (though there is no consistency
> if enabling the boot log,
I did try that, unfortunately, (at least here), the log stops about when the panic starts. (right after the battery check usually

---

### Post by Harry33 on 2011-01-23
> **dino99 said:**
> Sorry i've forgotten my decoder :( what is EIP ? Sadly there is no way to log the bootup time verbosing.
note: the kernel panic is due to: cant mount rootfs on unknown block, or so.

I found this info:

EIP - Instruction Pointer
    This holds the address of the next CPU instruction to be executed,
and it's saved onto the stack as part of the CALL instruction. As well,
any of the "jump" instructions modify the %EIP directly.

    The abort occurs when the control unit is unable to store a meaningful value in the "eip" register, which is supposed to contain the memory address of the instruction that caused
an exception fault. In other words, this seems to point to a hardware issue.

---

### Post by dino99 on 2011-01-24
> **cariboo907 said:**
> I wonder if enabling the boot log, /var/log/boot,  would help in this case?

Go to /etc/default/boologd, and change no to yes.

good point :)

but it need a custom kernel as i understand:

***
Bootlogd works by redirecting the output of the console
        console device (hence, requires Bootlogd
        Management PTY in kernel configuration). It copies this output
        to the actual device and the console to a log file. It
        is no way to obtain with certainty the actual device
        console if you have the new type of device / dev / console
        (major number 5, Minor 1). Bootlogd therefore analyzes the command line
        kernel to find console =... and deduce the device
        real. If this syntax is changed by the kernel or one type of
        unknown Bootlogd console is used, then only work Bootlogd
        not.
****

---

### Post by dino99 on 2011-01-24
Tweaking around, here is what i've found:

- by default, if splash is used then vt.handle=7 is added
- removing vt.handle=7 from boot menu resolve my booting issue, but make segfault if splash is not removed too.
- bootlogd=Yes dont seem to work with kernel from genuine repo

---

