---
title: "Desktop dual monitors won't work - nividia"
date: 2009-06-16
forum: Multimedia Software
---

### Post by nitroguy on 2009-06-16
Hi there.

I have been successfully running ubuntu on my laptop at home for quite some time, but when I tried to install it to my work computer (with dual monitors) the second monitor won't show up. Since I haven't encountered this problem with my laptop, I'm not sure what to do.

I've attached a screenshot of my NVIDIA X Server settings window. As you can see, the second monitor shows up, but everything is "unknown". Any ideas?

Thanks.

[IMG]http://lh5.ggpht.com/_vtfcDT5Qu0k/SjfBLFwxU5I/AAAAAAAABJM/wAQYSdsDXhg/s800/Screenshot-NVIDIA%20X%20Server%20Settings.png[/IMG]

---

### Post by Forlornity on 2009-06-16
Seeing as we're going for screenshots, show us the `X Server Display Configuration` section there.

- Forlornity

---

### Post by nitroguy on 2009-06-16
Ah ha! Apparently I have to click the "enable" button to get things to work (stupid me!)

Thanks for pointing that out!!

---

### Post by SuperSonic4 on 2009-06-16
If you're changing settings in nvidia-settings you'll need to be root since you're editing the xorg.conf file.

Back up xorg: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

and launch nvidia-settings as root: ```
gksu nvidia-settings
```

---

### Post by nitroguy on 2009-06-16
Thanks, that worked great!

---

### Post by Forlornity on 2009-06-16
I'm fairly sure nvidia-settings backs up your old config before writing settings so no need to backup before modifying :)

---

