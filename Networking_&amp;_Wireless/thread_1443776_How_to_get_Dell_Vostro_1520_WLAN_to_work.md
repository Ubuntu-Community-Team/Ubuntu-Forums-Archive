---
title: "How to get Dell Vostro 1520 WLAN to work"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by DrScum on 2010-03-31
I just installed 9.10 on a brand new Dell Vostro 1520. The WLAN card does NOT work out of the box. Here is what you have to do.

After install and rebooting insert the live CD
go to software sources (system > software sources)and check the "officially supported restricted copyright" box

you are then asked to update the available software list, do so. 

You will receive an error message since you are not (yet) connected to the internet and all the other repositories are not available.

Now you should be notified that restricted drivers are available, if not you can go to system > hardware. Anyway, now you should be able to activate the Broadcom STA driver.

After rebooting you can connect to available wireless networks.

Alternative (in case you are not asked, which happened to me on another Vostro system) system>administration>syaptic package manager
search for broadcom
mark b43-fwcutter and bcmwl-kernel-sources for installation
reboot (who said there is no rebooting required in linux)
the adapter should be up and running

---

### Post by ptn107 on 2010-07-27
After enabling Broadcom STA in Hardware Drivers I also had to add **wl** to /etc/modules to make the wireless work after each restart.

---

### Post by Razor_bmw123 on 2010-07-27
I have also installed Ubuntu 10.04 on my Dell 1320 laptop as dual boot with Windows 7. I have installed the Broadcom STA wireless driver via physical LAN cable from the internet and activated the driver. When I activate I can connect to the internet through Wireless. But each time when I reboot my system I cannot see any available wireless connection though I can see that the Broadcom STA wireless driver I activated. So everytime when I log in to Ubuntu 10.04 I need a physical LAN cable first of all to use the internet.
 
How can I load/downlaod the driver automatically when I log in to Ubuntu???

---

### Post by ptn107 on 2010-07-27
After you install the STA drivers via Hardware Drivers applet, open a terminal and do this:
```
echo "wl" | sudo tee -a /etc/modules
```

---

### Post by Razor_bmw123 on 2010-07-28
Thx.....:)....it worked!!!!!!!!!!!!!!!1:p

---

