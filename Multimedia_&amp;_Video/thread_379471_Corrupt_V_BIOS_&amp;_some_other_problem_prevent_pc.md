---
title: "Corrupt V_BIOS &amp; some other problem prevent pc starting with nvidia driver"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by Hakimio on 2007-03-08
Ok, here is the BIG problem:
Because of corrupt V_BIOS stupid nvidia driver was only able to detect CRT-0 and TV-0 and it even didn't detect any monitor when it was connected to DVI port. So I used "IgnoreDisplayDevices" "DFP, TV" (If I use "CRT, TV" it still finds only CRT-0 and TV-0) and "ConnectedMonitor" "DFP-0" and now it correctly recognizes that I have CRT-0, CRT-1, DFP-0, TV-0 and correctly assigns my monitor to DFP-0 port but it still reports that it can not read EDID, it incorrectly reports most of the values and when starting computer, after usplash shows that everything has loaded, I get black screen for awhile and then my monitor turns off, my keyboard seems not to respond, but if I wait few minutes I can hear the login sound. I have also tried "UseEDID" "False" and manually setting frequencies as tseliot suggested, but I still get only black screen.
However I have no problem with nv driver and if I start my pc with nv driver, change my xorg.conf and restart gnome desktop manager, nvidia driver works fine. Also legacy drivers works for me, but 3d looks distorted (no distortion with the latest drivers).

Here are my specs:
Graphic card: nvidia GeForce 6600 GT
LCD Monitor: [Philips 190x7fb](http://www.consumer.philips.com/consumer/catalog/tree/en/gb/consumer/pc_products_gr_gb_consumer/lcd_monitors_ca_gb_consumer/ce/_productId_190X7FB_00_GB_CONSUMER/LCD_monitor+190X7FB_00?proxybuster=CE2HXLXIBQ005J0RMRESHQFHKFSEKI5P&activeTab=specifications)
Nvidia driver: 8776 (installed with apt), also tried the latest (9746), but had the same problem as with this one.
Kernel: 2.6.17-11-generic
OS: Ubuntu 6.10
I have attached Xorg logs which I get with nvidia driver and with nv driver (verbose 6).

Please help me deal with this problem, cause I am searching for solution already more than a week, I'm out of ideas and I still really want to use Ubuntu with Beryl.

---

