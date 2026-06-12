---
title: "Video Problem in 10.10, Maverick"
date: 2010-11-26
forum: Multimedia Software
---

### Post by pimparello on 2010-11-26
Hello everybody,

I upgraded to 10.10 and now videos start getting slow after a short time. It's impossible to even watch youtube videos without problems. 

```
wolff@feivel2:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

The Laptop is a Acer Timeline 1810tz, I never had any issues with 10.04 and video works fine under Win7. 

What can I do? What data do you need, to help me?

Thanks a lot!

---

### Post by sikander3786 on 2010-11-26
Try reconfiguring your graphics by

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Test and see if it improves any thing.

---

