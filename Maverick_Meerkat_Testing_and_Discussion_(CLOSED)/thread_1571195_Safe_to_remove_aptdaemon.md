---
title: "Safe to remove aptdaemon?"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2010-09-09
If i remove USC, is it safe to remove aptdaemon? Wasnt sure if theres anything else that depends on it for Maverick.

---

### Post by ranch hand on 2010-09-09
You may want to leave that where it is.  Synaptic, I believe, needs it and Apt does need it.

---

### Post by Longinus00 on 2010-09-09
> **ranch hand said:**
> You may want to leave that where it is.  Synaptic, I believe, needs it and Apt does need it.

Neither apt or synaptic depend on aptdaemon.

---

### Post by 23meg on 2010-09-09
> **Slug71 said:**
> If i remove USC, is it safe to remove aptdaemon? Wasnt sure if theres anything else that depends on it for Maverick.

Why don't you just look at the reverse dependencies see for yourself? Go to the properties of the package in Synaptic, and select "Dependent packages" in the "Dependencies" tab. Or just look it up on packages.ubuntu.com. Or just try "apt-get remove"ing it and see what else apt-get wants to remove.

---

