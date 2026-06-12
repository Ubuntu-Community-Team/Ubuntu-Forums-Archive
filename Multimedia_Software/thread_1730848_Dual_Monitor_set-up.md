---
title: "Dual Monitor set-up"
date: 2011-04-16
forum: Multimedia Software
---

### Post by amerinde on 2011-04-16
ok, i got 2 acer monitors, I cant drag from one screen to the other. Is it possible to do that?

---

### Post by howefield on 2011-04-16
If you are using the proprietary driver, use nvidia-settings to configure and set them to twinview.

```
gksudo nvidia-settings
```

---

### Post by amerinde on 2011-04-16
i tried that, error:

Failed to set MetaMode (1)DFP-0:nvidia-auto-select
@1920x1080+0+0, DFP-2:nvidia-auto-select
@1920x1080+1920+0'(Mode 3840x1080,id:50) on X 
screen 0.

---

### Post by BicyclerBoy on 2011-04-16
What nvidia driver version are you using ??

I would think you would want 270+ for your h/w..
(actually nvidia say 195.36.24 supports 470/480 but that was first rushed release)

---

