---
title: "Internet connection problem using 3g huawei usb modem"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by jomski on 2009-05-30
Hi,
I'm a newbie to ubuntu but I have some familiarity with Linux. I recently installed version 9.04 server to try out and I had this setup
Server with wired interface eth0 which ws dhcp enabled and connected to my laptop via a switch.
I enabled internet connection sharing (windows) on my laptop and the server was able to reach the internet just fine.

After reading several tutorials on how to setup a 3g usb modem, I think I got it right (using wvdial) and it does make a successfult dial up connection on the server. However, I cannot seem to get on internet or ping any domain or make any updates.

Using webmin, I see that the connection is successful and active.
I'm suspecting that it may be my default gateway setting or something to do with pointing the machine to the ppp0 interface. I'm a little stumped here and I would really appreciate any help I can get now.

Thanks.

Jomski

---

### Post by pauna on 2009-05-30
I have got 3G working with my Huawei by just configuring the 3G network with Network Manager applet. In 8.04 I was playing around with wvdial, but in 9.04 I don't need to anymore.

Go to the Network manager applet, right click, "Edit connections" and select "Mobile Broadband". Create a new configuration item for your provider and fill the required information. Pay close attention to the APN name, it needs to be correct for net access.

If you select the "Connect automatically" option, you just need to plug in the USB device and 3G should start rolling automatically.

---

### Post by dnairb on 2009-05-30
In Jaunty, Network Manager is version 0.7.x and has mobile broadband support built-in.

**For "3" mobile:**

Right-click the nm icon in your panel and select "edit connections" (or System -> Preferences -> Network Connections)

Click the "Mobile Broadand" tab, and click "Add". Then:

Select "Create a GSM Connection" and click OK
Number is already "*99#". Type "3internet" in the APN field.
Give the connection a name and selcet "connect automatically" if preferred.
Click OK

---

