---
title: "incompatitbility"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by t_virus on 2009-04-03
hello all,
i installed madwifi-hal for my atheros 5007eg and it works fine. last night i installed the driver rt2870 for my USB wireless pen and it worked to. i had both working. when i rebooted the atheros stoped working and only the usb wireless pen (smcwusbs-n) was working.
so, i installed madwifi-hal again but now the usb wireless stoped working and only the atheros works.

any help about this?

thanks

---

### Post by t_virus on 2009-04-03
IT&#346; SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
FOR EVERYONE!!!!!!!!!!!!

The deal is this:

instal madwifi-hal -> install rt2870 -> reboot (only rt2870 will work) -> reinstall madwifi-hal (dont make clean) -> atheros is working -> with the computer on insert rt2870 USB DEVICE ->
[COLOR="Red"]
AND DONT FORGET TO REMOVE THE USB RT2870 BEFORE SHUTTING DOWN[/COLOR]

[COLOR="Red"]PUT IN WITH YOUR PC ON AND REMOVE IT WITH YOUR PC ON[/COLOR]

---

