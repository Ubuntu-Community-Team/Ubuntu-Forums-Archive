---
title: "Actiontec 11n wireless driver not working"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by youbantwo on 2011-10-07
Hello,

I'm trying to install the drivers for my usb wireless card on ndiswrapper on ubuntu lucid. I have the .inf and .sys in the same directory with the same name (except for the file extension). However, this is what ndiswrapper is displaying:
```

installing wlanuhnv32 ...
couldn't find models section "DeviceList" -
installation may be incomplete

```

lsusb is showing my wireless card. I'm not for sure what's wrong and googling the error didn't show any relative pages. Does anybody know what could be wrong?

Thanks

---

### Post by chili555 on 2011-10-09
Dr. Chili doesn't like the look of this. Please let us see:```
lsusb
```Also, what are the names of the .inf and .sys files? Where did they come from?

---

