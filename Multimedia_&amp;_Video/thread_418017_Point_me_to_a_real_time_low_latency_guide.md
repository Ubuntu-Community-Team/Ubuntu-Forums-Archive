---
title: "Point me to a real time low latency guide"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by dahouse on 2007-04-22
Hey guys,

I was wondering if you could point me to a guide for low latency real time kernel guides for great audio performance on Kubuntu.

I've tried google to no avail

Thanks

---

### Post by heimo on 2007-04-22
Obvious start would be to install prepackaged lowlatency kernel. This "linux-image-2.6.20-15-lowlatency" seems to be available in Feisty. Have you done that? (Sorry, no links to any guides, I'm not expert on this subject.) Are you using jack audio server?

---

### Post by dahouse on 2007-04-22
But won't I need to recompile or modify grub or anything?

---

### Post by heimo on 2007-04-22
> **dahouse said:**
> But won't I need to recompile or modify grub or anything?

No. Grub configuration is changed for you automatically. And as it's precompiled / prepackaged, you don't need to compile it. :) I've used it with jack and it works nicely.

---

