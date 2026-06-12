---
title: "Why is there a difference in Video Performance between Ubuntu and Mythbuntu?"
date: 2009-02-15
forum: Mythbuntu
---

### Post by deepee_oz on 2009-02-15
Hi All

I have a working Mythbuntu system that I dislike because of the limitations of xbuntu.

On another hard disk I installed Mythtv on a fully updated standard desktop Ubuntu 8.10 system.

Using the same NVIDIA restricted drivers with exactly the same settings as the Mythbuntu system as well as the same TV settings display profile (CPU+) I get poor results. Unacceptable video tearing on panned images and speed blur are the main issues.

It is a dual core AM2 5000 CPU with 4GB and NVIDIA onboard 8200 graphics so it isn't struggling.

Any ideas as to why video performance should vary so much between the two installations?

Should mention that Mythbuntu is also 8.10 fully updated
Thanks

---

### Post by superm1 on 2009-02-15
> **deepee_oz said:**
> Hi All

I have a working Mythbuntu system that I dislike because of the limitations of xbuntu.

On another hard disk I installed Mythtv on a fully updated standard desktop Ubuntu 8.10 system.

Using the same NVIDIA restricted drivers with exactly the same settings as the Mythbuntu system as well as the same TV settings display profile (CPU+) I get poor results. Unacceptable video tearing on panned images and speed blur are the main issues.

It is a dual core AM2 5000 CPU with 4GB and NVIDIA onboard 8200 graphics so it isn't struggling.

Any ideas as to why video performance should vary so much between the two installations?

Should mention that Mythbuntu is also 8.10 fully updated
Thanks
The xorg.conf is set up a little bit differently in mythbuntu 8.10.  There are a few very useful flags that come out of it.

---

### Post by lavinog on 2009-02-15
is desktop effects enabled?

---

### Post by deepee_oz on 2009-02-16
> **superm1 said:**
> The xorg.conf is set up a little bit differently in mythbuntu 8.10.  There are a few very useful flags that come out of it.

Thanks superm1, so there is a difference.
I'll try copying the xorg.conf from the Mythbuntu install to the Ubuntu install and see what happens.

---

### Post by deepee_oz on 2009-02-16
> **lavinog said:**
> is desktop effects enabled?

Thanks for the pointer lavinog. I think desktop effects are switched on by default in new installs. I'll check when I get home.

---

