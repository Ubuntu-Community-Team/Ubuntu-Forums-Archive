---
title: "How do I turn off Adaptive Overclocking for nvidia cards?"
date: 2022-03-12
forum: Multimedia Software
---

### Post by 98cwitr on 2022-03-12
Have a 1660 Super and I want to turn off Adaptive Overclocking. 

It appears to be possible

> Attribute 'GPUAdaptiveClockState' (somewhere:1[gpu:0]): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).


However, it says that it's a read-only attribute

> 'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.


So what will actually turn this off? Coolbits value is 28.

---

### Post by Yellow Pasque on 2022-03-13
> Coolbits value is 28
Do you have "PowerMizer" settings showing in the Nvidia control GUI? If not, it could be that the card vendor has a special GPU BIOS with preprogrammed settings and it doesn't allow manual control. If that's the case, then you're looking at BIOS-flashing a GPU and there are better places to get advice on that than this site.

---

