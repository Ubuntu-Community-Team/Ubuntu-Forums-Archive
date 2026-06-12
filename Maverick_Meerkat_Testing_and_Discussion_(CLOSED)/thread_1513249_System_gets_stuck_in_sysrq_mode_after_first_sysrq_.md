---
title: "System gets stuck in sysrq mode after first sysrq key press"
date: 2010-06-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2010-06-19
Today I discovered that my system crashed after some key combination, and now I figured out that it was caused by sysrq stealing my keyboard.

The process to trigger the bug is to hit the SysRq key (FN+F10 in my laptop) and then Alt+F2 (I think it works with other F** too).
After having done this, every key you press will result in a SysRq call EVEN IF SYSRQ KEY IS NOT PRESSED!
To leave this mode you have to press ALT+F2 a few times (until you get the Run Application dialog), bot the mode is not completely left, because when you'll hit SysRq again you'll be jumped into this mode again.

Does this happen to you?

---

### Post by Reiger on 2010-06-19
I'm not sure but the trick I can do is this:

(1) Press PrintScrn
(2) Watch the X server roll over and die/stall.
(3) Notice how the system no longer responds to keyboard input.

But I figured that's part of the promised X breakage, so will be sorted when X server 1.9 hits the repositories?

---

### Post by yelo3 on 2010-06-19
You are right, also pressing PrintScrn triggers this problem, but in my case an Alt+F2 (or maybe other F too) is needed as long as the press of a char (for exaple c, which triggers a sysrq crash).

Please do this:
- open a terminal
- tail -f /var/log/message
- hit PrintScrn
- hit Alt-F2

see if you see a message like this:
> SysRq : HELP : loglevel(0-9) reBoot Crash terminate-all-tasks(E) memory-full-oom-kill(F) kill-all-tasks(I) thaw-filesystems(J) saK show-backtrace-all-active-cpus(L) show-memory-usage(M) nice-all-RT-tasks(N) powerOff show-registers(P) show-all-timers(Q) unRaw Sync show-task-states(T) Unmount force-fb(V) show-blocked-tasks(W) dump-ftrace-buffer(Z) 


To avoid the crash hit ALT+F2, and then try with the key 's': if you are out of the sysrq mode you'll see the char 's' printed instead of a emergency sync message

---

### Post by yelo3 on 2010-06-19
This seems to be a kernel issue, I booted with an older kernel and I don't see it.

---

### Post by moviemaniac on 2010-06-19
Can't trigger it on my custom .35-rc3 too

---

### Post by yelo3 on 2010-06-19
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257)

I found other people with this bug in a mailing list [https://patchwork.kernel.org/patch/105079/](https://patchwork.kernel.org/patch/105079/).
Are you sure that 2.6.35-rc3 works for you?
Please follow the instructions found on the bug report.

---

### Post by mc4man on 2010-06-19
On a desktop cannot reproduce a crash  or behavior as you've described.

Can however see that there is an issue with Alt and  PrintScrn.

Basically PrintScrn works until Alt is used, from then on it becomes non-functional till a reboot.

Obviously this also renders using Alt+PrintScrn to take a screenshot useless.

---

### Post by Nr90 on 2010-06-20
When I hit sysrq and then press alt F2 and a couple of keys I get a fatal kernel error and it flashing a bunch of errors and freezes up.
FATAL sync error

---

