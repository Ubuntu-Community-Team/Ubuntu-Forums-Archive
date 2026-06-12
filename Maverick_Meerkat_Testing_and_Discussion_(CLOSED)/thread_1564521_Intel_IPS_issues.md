---
title: "Intel IPS issues"
date: 2010-08-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bprins on 2010-08-30
Hi,

I've got some strange messages during boot and runtime in Maverick regarding Intel IPS. It looks like its a graphical device which encounters problems, no clue if its a big problem. All I know that I don't have these problems in Lucid.

from dmesg:
```

[B][   20.071308] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   20.071334]   alloc irq_desc for 21 on node -1
[   20.071337]   alloc kstat_irqs on node -1
[   20.071345] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.071477] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[/B][   20.084705] lib80211: common routines for IEEE802.11 drivers
[   20.084709] lib80211_crypt: registered algorithm 'NULL'
[   20.087776] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.087780] Disabling lock debugging due to kernel taint
**[   20.146760] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535**

```

from kern.log
```

Aug 30 22:34:11 ubuntu-lt kernel: [  574.724554] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Aug 30 22:34:16 ubuntu-lt kernel: [  579.717730] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Aug 30 22:34:21 ubuntu-lt kernel: [  584.710912] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

```

Apparently something is not proper with expected and current temperatures.

Should I act on this information? Do I have incorrect drivers?

Thanks.

Bas

---

### Post by bprins on 2010-08-30
Hmm, found this:

[http://kerneltrap.org/mailarchive/linux-kernel/2010/8/25/4610979](http://kerneltrap.org/mailarchive/linux-kernel/2010/8/25/4610979)

So wait for updates I guess.

---

### Post by MacUntu on 2010-08-30
See also: [https://lists.ubuntu.com/archives/ubuntu-devel/2010-August/031361.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-August/031361.html)

---

### Post by julienr on 2010-10-02
I have an Intel GMA HD and I have the same message at boot.

I don't know if it is related, but I have horrible graphic performances in Maverick. In lucid, I was using the [fix described here]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/554569") and I had some reasonable graphic performances. Around 100 FPS when playing Quakelive, whereas it is now 10.

---

### Post by soumster on 2010-10-03
I too face the same issue. My dmesg output is as follows:

[   14.743896] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   14.743925] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.744117] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   14.747086] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535

After boot, I get an error message saying Kernel encountered a serious error.

Any help please?

---

### Post by bprins on 2010-10-07
Still haven't got any solution.

This is quite an annoying issue. There are some discussions on the web where developers and testers are debating this issue, but I don't read anywhere how we can get rid of this problem.

It's a kernel issue as far as I understand it.

The annoying thing is, the warning is thrown every 5 secs spamming my kern.log. 

Does anybody have any idea how to get rid of this issue? Graphics device "seems" to work fine..

Thanks a lot in advance.

Bas

---

