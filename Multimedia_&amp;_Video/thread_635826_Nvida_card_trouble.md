---
title: "Nvida card trouble"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by computer-sez-no on 2007-12-09
I have a navida 8400 graphics card and I was told I needed navida-glx-new and I tried and it told me I needed to install navida-glx to install navida-glx-new but now instead f it telling me it needs navida-glx it says it coinflicts with navida-glx.

What should I do?

---

### Post by lizzard on 2007-12-09
Try to uninstall nvidia-glx.

```
 sudo aptitude remove nvidia-glx 
```Then use the "restricted-manager" to install the correct nvidia-driver. (->System -> Administration -> restricted-manager)

---

### Post by pbcartwright on 2007-12-09
you might want to install envy;
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

envy works with ubuntu and will install NVIDIA and ATI video card drivers for you..

---

