---
title: "mt-daapd server doesn't restart properly upon reboot"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by khm on 2009-07-20
I recently installed the package mt-daapd for a music server. Everything works fine. I made some small modifications to the configuration file.

My problem is that the server has issues after a reboot. Most sources seem to indicate that the server has automatically restarted and is up and running without error. I checked the web host ([http://localhost:3689](http://localhost:3689)) as well as actually stopping at starting it again from the command line (/etc/init.d/mt-daapd start|stop). Everything here indicates that it is fine.... except for the fact that neither iTunes nor rhythmbox can see the server. In order to get the server back to functioning capacity, I must use apt to remove and then re-install the package (same config file is used). As soon as the package is finished installing, everything works just fine.

Why do I have to re-install?

---

### Post by khm on 2009-07-22
anyone?

---

### Post by ad_267 on 2009-08-16
I've had the same problem but found this fix:

[http://colinnwn.blogspot.com/2009/06/setting-up-firefly-mt-daapd-with.html](http://colinnwn.blogspot.com/2009/06/setting-up-firefly-mt-daapd-with.html)
[http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes](http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes)

I also found somewhere that said to run:
```
sudo update-rc.d mt-daapd defaults
```

I haven't tried that myself though and the previous fix worked for me.

---

### Post by khm on 2009-08-18
> **ad_267 said:**
> I've had the same problem but found this fix:

[http://colinnwn.blogspot.com/2009/06/setting-up-firefly-mt-daapd-with.html](http://colinnwn.blogspot.com/2009/06/setting-up-firefly-mt-daapd-with.html)
[http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes](http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes)

I also found somewhere that said to run:
```
sudo update-rc.d mt-daapd defaults
```

I haven't tried that myself though and the previous fix worked for me.

Yep, that fixed it. 
THANKS!

---

