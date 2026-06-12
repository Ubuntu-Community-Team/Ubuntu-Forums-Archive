---
title: "Nvidia blue tint bug fix"
date: 2012-10-30
forum: Multimedia Software
---

### Post by Statia on 2012-10-30
[FONT=Arial]I saw the annoying blue-people bug in Flash can be solved by installing the 310.14 Nvidia drivers:

[http://ubuntuxtreme.com/howto/how-to-install-nvidia-310-14-drivers-major-changes/](http://ubuntuxtreme.com/howto/how-to-install-nvidia-310-14-drivers-major-changes/)

I already fixed the bug by installing the patched libvdpau1 from the 
[/FONT][FONT=Arial]ppa:tikhonov/misc
repository. Is it advisable to reinstall the regular libvdpau1 when installing the 310.14 driver?

[/FONT]

---

### Post by madinc on 2012-10-30
> **Statia said:**
> [FONT=Arial]I saw the annoying blue-people bug in Flash can be solved by installing the 310.14 Nvidia drivers:

[http://ubuntuxtreme.com/howto/how-to-install-nvidia-310-14-drivers-major-changes/](http://ubuntuxtreme.com/howto/how-to-install-nvidia-310-14-drivers-major-changes/)

I already fixed the bug by installing the patched libvdpau1 from the 
[/FONT][FONT=Arial]ppa:tikhonov/misc
repository. Is it advisable to reinstall the regular libvdpau1 when installing the 310.14 driver?

[/FONT]

[B]Lightspark, a free, open source Flash player

see here [/B][http://lightspark.github.com/](http://lightspark.github.com/)

---

### Post by monkeybrain2012 on 2012-10-30
That happens only on Youtube apparently. But you don't even need flash for Youtube.  
  [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) :)

---

### Post by Statia on 2012-11-01
No, it does not only happen on Youtube, it happens with Stage Video, which is most prominently, but not exclusively, used by Youtube.
For Youtube I use HTML5 where possible anyway.

---

### Post by Statia on 2012-11-03
People, my question is not "what is an alternative for Flash?".
My question is whether it is better to install an unpatched libvdpau1 if I am going to use the latest Nvidia driver.

---

### Post by nardis_Miles1 on 2012-12-04
I installed 3.10.19 and I still have the blue man problem.

---

### Post by pippinsplugins on 2012-12-04
I have the same problem as well.

---

### Post by Statia on 2012-12-05
> **nardis_Miles1 said:**
> I installed 3.10.19 and I still have the blue man problem.

Really? For me it was gone with 310.14 and I did revert to the original libvdpau1.

---

