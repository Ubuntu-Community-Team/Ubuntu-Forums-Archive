---
title: "wireless port disappeared after synaptic upgrade 10.04"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by hodad on 2010-11-28
After getting my wireless usb device working (very painstakingly over a week), I did an Updat Manager update, and when I was done, my wireless port was gone.   

Can't seem to find any relevent solutions on earlier posts (but there are many with the same problem).   

Something got hosed by the update.  Does anyone have any ideas what wireless related files may have been overwritten during the upgrade?

Thanks!

---

### Post by uncaspi on 2010-11-28
Probably the new kernel don't support the wireless card. Issue this command:

sudo lspci -nn

and please post the result.

---

### Post by hodad on 2010-11-28
Thanks for your help - but - I got it back a couple of minutes ago.   It looks like something disabled the driver for the USB device.  I decided to make a clean re-install of the driver, and it came back OK (I'm transmitting on it now).

Once again, thanks!

---

### Post by uncaspi on 2010-11-28
Remember to put [SOLVED] on the thread:D

---

### Post by hodad on 2010-11-28
How?

I looked for a Solved button, but couldn't see one (?).

---

### Post by uncaspi on 2010-11-29
I think you must type it in the title.

---

### Post by NoNameWill on 2010-11-29
Look at thread tools right about your first post from the drop menu you can select [solved] 

I had the same thing happen a few days ago. What driver and usb are you using? I used the ath9k_htc-installer to get mine to work but with the kernal update it wouldn't work. Even after rolling back the kernel.

---

### Post by hodad on 2010-11-29
I am using a D-Link DWA-125 USB wireless based on a Ralink 2870 chipset.  On another thread, I got help from "Chili".  We first tried a rt2870sta driver, because the device uses the Ralink rt2870 chipset.  After almost a week, we gave up on that driver, and went with the driver for the next generation chipset.  The device came up right away using the rt3370sta driver (but still had encryption probelms, which are ongoing).   I guess that the new chipset uses much the same settings, hence the driver works for the most part.  Perhaps more importantly, the Ralink site says that the 3370 driver supports WPA/WPA2 encryption (and doesn't say that about the 2780 driver, tho I thnik it must).  I think that's why Chili chose it (but he may respond otherwise).

---

