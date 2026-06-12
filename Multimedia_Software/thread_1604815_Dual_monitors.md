---
title: "Dual monitors"
date: 2010-10-24
forum: Multimedia Software
---

### Post by devilliers123 on 2010-10-24
I have been using Dual monitors with ATI RV100.
I upgraded from 10.04 to 10.10 and then lost dual monitors.
Only one showed up.
I reinstalled 10.4 but never got the dual monitors back other than mirrored.
Each time I uncheck the mirror and accept that setting the video output comes back scrambled.

I have had messages;

1. '(to the effect of) uanable toprobe SMB bus' and this was accompanied by a flash of green screen during boot. I cured that by editing the /etc/default/grub file by adding an entry in the second option to the effcet of...'GRUB_LINUX_RESOURCES=lax' then updated grub. That cured the error message and the green screen.
Since that was cured there is a flashed message on the screen in a black frame (just the same as network manager sends upon connection) upon boot that says to the effect 'unable to save configuration settings 1, 0 (file) contains only white space'

2.  'file deprecated (vga=791)' 'use gfxpayload=1024X768X16,1024X768'

3. 'Segregated File Failure'.

I am unable to correct this problem with Dual Monitors which seems to be needed to be done through the xorg.conf file.
At the time I edited that file to try to resolve the issues the boot hung and as a result from a default boot from live disc I now have only xorg.config.failsafe  file.

Anyone know how to add the file content needed to reinstate what was once a very good dual monitor working setup?

I am very frustrated and afraid of further digging into a hole...

Thanks

---

