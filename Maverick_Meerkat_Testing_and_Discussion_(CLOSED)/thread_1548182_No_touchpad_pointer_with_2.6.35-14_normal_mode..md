---
title: "No touchpad pointer with 2.6.35-14 normal mode."
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by k3lt01 on 2010-08-07
Yesterday I updated to Maverick and had to do the kernel mode workaround for the intel chipset to get Ubuntu graphics to work in normal mode. However, I have no mouse pointer in normal mode and the only way I can get it is to boot into Recovery Mode, FailsafeX. I still have Lucid and Karmic kernels available and it is fine in them but not in Maverick's 2.6.35-14. Has anyone else come across this issue?

Btw I used the forum search to search this forum, also searched Launchpad, but nothing comes up. It didn't for another problem yet after manually going through the forum I found a post on the other issue.

---

### Post by dorutz on 2010-08-08
Same problem here, my machine IBM X40 with i855 graphics... Probem was not present in MMalpha1 or MMalpha2. Cursor gone in MMalpha3.

Actually, the cursor exiists, but is invisible... clicking and dragging works, but all as if i'm bllind.

As a temporary fix, I enabled the option of showing cursor location (circles) when pressing ctrl... still, i'd like my cursor.

---

### Post by teh603 on 2010-08-08
File a bug report against X ?

---

### Post by susebruger on 2010-08-08
Have a look at bug LP #614199 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614199](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614199)

---

### Post by TKbuntu on 2010-08-08
> **dorutz said:**
> Same problem here, my machine IBM X40 with i855 graphics... Probem was not present in MMalpha1 or MMalpha2. Cursor gone in MMalpha3.

Actually, the cursor exiists, but is invisible... clicking and dragging works, but all as if i'm bllind.

As a temporary fix, I enabled the option of showing cursor location (circles) when pressing ctrl... still, i'd like my cursor.

Same issue on my Thinkpad R51 laptop. Comment added to the bug mentioned above.

---

### Post by k3lt01 on 2010-08-09
> **dorutz said:**
> Same problem here, my machine IBM X40 with i855 graphics... Probem was not present in MMalpha1 or MMalpha2. Cursor gone in MMalpha3.

Actually, the cursor exiists, but is invisible... clicking and dragging works, but all as if i'm bllind.

As a temporary fix, I enabled the option of showing cursor location (circles) when pressing ctrl... still, i'd like my cursor.
Apart from the machine this is exactly what is happening to me. What have they done to the kernel to cause this? Testing Lucid threw up problems with the i855 chipset and kernel settings but that was an easy fix.

I shall check the bug report posted above. Thanks for the tips.

---

### Post by dorutz on 2010-08-09
No problem.

Cursor works in recovery mode... strange...

What kernel change could possibly cause this?

---

### Post by k3lt01 on 2010-08-09
> **dorutz said:**
> No problem.

Cursor works in recovery mode... strange...But it doesn't in normal mode,so I would consider that a problem :)

> **dorutz said:**
> What kernel change could possibly cause this?Maybe more changes that affect the i855 chipset like the ones that started manifesting themselves in Lucid Testing.

---

### Post by Catharsis on 2010-08-09
[http://launchpad.net/bugs/614176](http://launchpad.net/bugs/614176)

Bad Commit:
> commit b690e96cf9e6a6cde6f0393de47bdd6317ddb5de
Author: Jesse Barnes <jbarnes@virtuousgeek.org>
Date: Mon Jul 19 13:53:12 2010 -0700

    drm/i915: add pipe A force quirks to i915 driver

    Ported over from the old UMS list. Unfortunately they're still
    necessary especially on older laptop platforms.

    Fixes [https://bugs.freedesktop.org/show_bug.cgi?id=22126](https://bugs.freedesktop.org/show_bug.cgi?id=22126)

---

