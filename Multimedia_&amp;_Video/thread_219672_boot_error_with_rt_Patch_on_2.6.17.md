---
title: "boot error with rt Patch on 2.6.17"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by hanzomon4 on 2006-07-20
I patched the 2.6.17 kernel with the rt patch(rt1,rt6 and rt7). It patches and compiles with no errors, but when I try to boot the 2.6.17-rt*(6 or 7)I get this message, right after it says booting the kernel
> -----------cut here----------
       kernel BUG at kernel/rtmutex_common.h:74!
       invalid opcode:0000[#1]
       PREEMPT SMP
       Modules linked in :
       CPU:0
       EIP: 0060:[<c013b743] Not tainted VLI
       EFLAGS:00010092 (2.6217-rt1 #1)
       EIP is at wakeup_next_waiter 0x12b/0x1b8
       eax: 00000026 ebx: c0359248 ecx: 00000000 edx: c0304600
       esi: 00000000 ebi: fffffff4 ebp: c035e000 esp: c035ff38
       ds: 007b es: 007b ss: 0068 preempt: 00000067
       Process swapper (pid: 0, threadinfo=c035e000 task=c0304600 stack_left=7940 worst
c035ffb0 00000000 0009fc00 c035ff94 c035ffb0 c0204c96 00000000 e000040e
I don't know where to look for the message(to cut and paste it), So I had to copy it by hand. Anyway it just stops at that screen.
I have compiled the 2.6.17 kernel with out the realtime patch and it boots fine. I tried the rt1 rt6 and rt7 patch for the 2.6.17 kernel but both give me the same error.
If any more information is need I'll gladly post it

---

### Post by linuxnewbie946 on 2006-07-20
> **hanzomon4 said:**
> I patched the 2.6.17 kernel with the rt patch(rt6 and rt7). It patches and compiles with no errors, but when I try to boot the 2.6.17-rt*(6 or 7)I get this message, right after it says booting the kernel, that starts with this


I don't know where to look for the message(to cut and paste it), but it has some other stuff. Anyway it just stops at that screen.
I have compiled the 2.6.17 kernel with out the realtime patch and it boots fine. I tried the rt6 and rt7 patch for the 2.6.17 kernel but both give me the same error.
If any more information is need I'll gladly post it

The patch itself most likely has a bug.

---

### Post by hanzomon4 on 2006-07-20
I'll try a to patch a 2.6.16 kernel to see if that works.....

Success!! With the 2.6.16 kernel and rt29 patch I don't Know whats wrong with the 2.6.17 rt patches, but any thanks for all the help...and the howto

---

### Post by floogy on 2006-08-13
Is there still the same bug in rt8?

---

