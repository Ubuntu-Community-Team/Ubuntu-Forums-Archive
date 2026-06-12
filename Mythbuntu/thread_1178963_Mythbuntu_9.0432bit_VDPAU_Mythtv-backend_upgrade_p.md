---
title: "Mythbuntu 9.04/32bit VDPAU Mythtv-backend upgrade problems"
date: 2009-06-05
forum: Mythbuntu
---

### Post by Lester_Burnham on 2009-06-05
Hi,

After adding the JYA repositories for VDPAU and upgrading, everything works fine, but the mythtv-backend fails to upgrade, as can be seen in the screenshot attached. This has happened twice now I think.

Any idea how I can chase this up and fix it.

Thanks,
Lester

---

### Post by jbman on 2009-06-05
did you manually shut down the backend first?

---

### Post by Lester_Burnham on 2009-06-05
Nope never had to before, but it did make me think I may have to.

---

### Post by jyavenard on 2009-06-05
> Nope never had to before, but it did make me think I may have to. 

You'll get the same error using the weekly mythbuntu packages.

While you get an error, it's related to the update failing to stop / restart the mythbackend process (actually, it doesn't stop it which is why it gives an error).

It's safe to ignore it.

---

### Post by Lester_Burnham on 2009-06-05
Thanks JYA and jbman.

---

