---
title: "Wifi works perfectly on Windows, but drops on Ubuntu"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by alecrn on 2011-02-02
I have a dual-boot computer with Windows XP on one  partition and Ubuntu 10.10 on the other.   In Windows XP I can connect to  a hidden wireless network (WPA-PSK AES) perfectly, and I was finally  able to install the driver for the adapter on Ubuntu (RNX-N180UBE,  hardware id RTL8191SU).


  It works fine when I first boot the computer and log in, but then  after a few minutes the network suddenly stops working completely.   If I  try to reconnect it, the network manager claims to have connected, but  in actuality it's still down.


  At some points, I have been able to connect to a public network even  while the private network didn't work, but that eventually wouldn't work  at all either.

---

### Post by dasking on 2011-02-02
did you try restarting the wifi

---

### Post by ghostborg on 2011-02-02
I had a similar problem with my Dlink usb in the past where Ubuntu would say I was connected but was not.
For me it turned out that I needed a driver.
A quick google for RTL8191SU gave me this page:
[http://www.wireless-driver.com/realtek-rtl8191su-wlan-windows-linux-drivers/]("http://www.wireless-driver.com/realtek-rtl8191su-wlan-windows-linux-drivers/")

It looks like there is a Linux driver to download.
download1 looks to be the same zip file as download2, just mirrors.

---

### Post by whatthefunk on 2011-02-02
I had the same problems.  I installed a new driver using ndiswrapper to make the connection faster and installed Wicd to replace the default program, Network Manager.  If your connection is quick, but drops all the time, my guess is that Network Manager is to blame.

```
sudo apt-get install wicd
```

Then do a reboot.  You should see a new icon in the task bar next to the Network Manager icon.  You should have better luck connecting now, but you'll probably have to uninstall Network Manager to get it going perfectly.

```
sudo apt-get purge network-manager
```

You may have to run the wicd install command again to get Wicd to work properly.

---

### Post by alecrn on 2011-02-02
Thanks for the quick replies!

I'll try these out right now, hopefully they'll work!

---

### Post by alecrn on 2011-02-02
I installed the wicd manager, and so far so good.  I'll get back to you tomorrow to see if it keeps up.  Either way, thanks a lot!

---

### Post by whatthefunk on 2011-02-02
I hope it keeps working for you!  Glad to help.

---

### Post by alecrn on 2011-02-04
It's working perfectly!  Thank you so much!  Now I can enjoy Ubuntu fully, finally.

---

