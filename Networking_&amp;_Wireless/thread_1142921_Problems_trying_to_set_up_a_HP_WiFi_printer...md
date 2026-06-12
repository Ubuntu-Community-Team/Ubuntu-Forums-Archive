---
title: "Problems trying to set up a HP WiFi printer.."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by cptrohn on 2009-04-29
Hi I have a new HP Officejet J4680 WiFi All-in-One printer I am trying to get set up to work with Jaunty 9.04 (Kubuntu)


The printer WILL work when it is set up via USB perfectly fine, but I am having problems with the WiFi end of things... I just can't get it to work with the WiFi connection at all.


I have tried using the printer set-up function through hplip toolbox, when it goes to the Device Discovery window I select from the connection type the Network/ethernet/wireless network option and then click next...


Then it goes to the Select from Discovered Devices window, which doesn't show my printer at all and doesn't list any devices to be able to connect to....

Is there something I am missing here?  I messed around just a little bit with the CUPS option and it seems through Cups it does recognize the printer on the network..... if I were to set-up with cups would I still have all the features for the printer? (I don't know much about it at all to be honest.)  Is this an HPLIP problem?   It doesn't make sense that it will work just fine with the USB and isn't even detected through the wireless does it?

Anybody gone through something similar that can shed some light on this?  Is it something that I am doing wrong in the setup process that is causing this?

Thanks for reading!

---

### Post by cptrohn on 2009-04-29
LOL


help please?  LOL


This is my first attempt at trying to get a WiFi printer up and running and I'm pulling my hair out now... (and I don't have alot to spare)

---

### Post by wgscott on 2009-04-30
I just did this yesterday, albeit with OS X.

If your printer has a webserver interface, use that instead of any setup software.  Here is what I did to get it to work:

Turn off password protection on your wireless router.

Connect your printer via an ethernet cable to the router (assuming this is permitted) and verify that it is allocated a local IP address.

Websurf to that IP address and use the web-based software to discover the wireless network.  Verify everything works.

Then enter the encryption mode and the passphrase into the printer software and upload it to the printer.

Reprotect the wireless router, unplug the printer from the wired network, and test to see if it works.

It took about 3 hours to distill it to the above. Transiently unprotecting the wireless network was the key to getting it to work (and realizing the distributed setup software was worthless).

---

### Post by dkruidhof on 2009-04-30
After a lot of trying different things, I finally had to borrow a friend's windows laptop to set up my HP wifi printer using a USB connection and the CD it came with. Then my ubuntu computers found the printer on the wifi without an issue just using the simple Printing gui.

---

### Post by cptrohn on 2009-04-30
Thank you guys for the help, I will try these later today, thanks!

---

