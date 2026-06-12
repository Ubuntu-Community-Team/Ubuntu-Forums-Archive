---
title: "&quot;render error detected&quot; after standby/restart"
date: 2009-12-16
forum: Multimedia Software
---

### Post by tizio59 on 2009-12-16
Hi,

After 9.04 - 9.10 upgrade I get the following after a suspend & restart:

```

[  678.212992] render error detected, EIR: 0x00000010
[  678.212996] page table error
[  678.212998]   PGTBL_ER: 0x00000100
[  678.213004] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[  678.213020] render error detected, EIR: 0x00000010
[  678.213022] page table error
[  678.213024]   PGTBL_ER: 0x00000100

```

The graphics is garbled but I can clearly identify screen objects (9.04 worked just fine).

I have an Intel based graphics chip, on a fairly old laptop. 

I discovered that I can workaround the problem by switching to a console view and back. alt-ctrl+F1   and back alt-ctrl+F7  but quite annoying. Any hints?

---

### Post by susanw on 2009-12-30
This could be the bug mentioned in the following thread on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064)

---

