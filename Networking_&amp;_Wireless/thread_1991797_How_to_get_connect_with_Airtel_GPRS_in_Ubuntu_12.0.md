---
title: "How to get connect with Airtel GPRS in Ubuntu 12.04?"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by mitultechs on 2012-05-31
Hello,

I am having problem connecting with the Airtel GPRS. However I have created the mobile broadband profile into my Ubuntu 12.04. 
I have search over the Google. It gives the idea of linux command to have change the wvdialconf file. But I didn't get any file at etc/wvdialconf.

 Is any body help me? I am new to the Ubuntu...

Thanks

---

### Post by prshah on 2012-05-31
> **mitultechs said:**
> However I have created the mobile broadband profile into my Ubuntu 12.04. 

But I didn't get any file at etc/wvdialconf.


You don't need to use wvdial any longer. Mobile broadband profile is the correct way.

For your reference, these are the settings:
APN: airtelgprs.com
Dial: *99#
Everything else: blank, Type: Any.
At least initially, enable "Connect Automatically"

If it still does not work, please provide information about the device you are using for connectivity: 
a) Mobile phone: What model and method?
or b) USB stick: what model and method?

Some USB stick have a "dual mode": one is a mass storage device that provides drivers for the stick (Windows only, usually) and a second mode for wireless broadband modem. To switch between these manually (usually not necessary) you need to use "usb-modeswitch".

Please post back with details if you need more guidance.

---

### Post by mitultechs on 2012-05-31
> **prshah said:**
> You don't need to use wvdial any longer. Mobile broadband profile is the correct way.

For your reference, these are the settings:
APN: airtelgprs.com
Dial: *99#
Everything else: blank, Type: Any.
At least initially, enable "Connect Automatically"

If it still does not work, please provide information about the device you are using for connectivity: 
a) Mobile phone: What model and method?
or b) USB stick: what model and method?

Some USB stick have a "dual mode": one is a mass storage device that provides drivers for the stick (Windows only, usually) and a second mode for wireless broadband modem. To switch between these manually (usually not necessary) you need to use "usb-modeswitch".

Please post back with details if you need more guidance.


Hey,

I have created the mobile profile into ubuntu but I can't able to connect it. 

I am using Nokia C3-00 and connecting with using the Data Cable. 

Looking Forward.

---

### Post by prshah on 2012-05-31
> **mitultechs said:**
> I am using Nokia C3-00 and connecting with using the Data Cable.

Is your c3-00 phone's inbuilt modem being recognized? You can check this way: Disconnect your phone, open Dash-Terminal and give the commands ```

lsusb > ~/o_usb
lsmod > ~/o_mods
tail -f /var/log/syslog
```

Now, with the terminal open, connect your phone to the computer. Wait a few seconds (10-15) and some new output (lines) will appear in the terminal. Please copy and paste those lines here for analysis.

You can now terminate the tail command (Press Ctrl+C when focus is in the Terminal) and also run the following commands and post back outputs, please (DO NOT REMOVE PHONE)```
lsusb > ~/n_usb
lsmod > ~/n_mods
diff o_usb n_usb
diff o_mods n_mods
```

All of this is just for information gathering.

---

