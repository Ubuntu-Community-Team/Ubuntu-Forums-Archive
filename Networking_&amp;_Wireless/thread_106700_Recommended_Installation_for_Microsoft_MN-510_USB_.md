---
title: "Recommended Installation for Microsoft MN-510 USB Wireless"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by Hangetsu on 2005-12-21
Hello all!

I'm a newbie to Ubuntu (used SUSE for several months), and I just completed my installation.  However, I don't have internet access yet as my Microsoft Wireless USB NIC was not detected (MN-510).

I've read the existing threads on the forum, and unfortunately that left me a bit confused.  There are threads that recommend using the WINDOWS .inf file, and there are others that recommend using the linux-wlan file.

Is there an overall recommendation as to what should be used?  Also, are there detailed instructions on how to do so?  I did not deal with this aspect in SUSE (my card was detected automatically).

I expect to do this twice, when I install edubuntu on my daughter's PC.

Thanks much for the help, and I'm happy to be here!

---

### Post by Hangetsu on 2005-12-21
Any ideas?  I'm shut down from the internet at home until I get this fixed unfortunately, and I don't want to go back to SUSE (not that it was bad, just that I like the philosophy of the Ubuntu community better).

Thanks!

---

### Post by Lambert on 2005-12-21
I do not use a device using linux-wlan-ng so maybe with time somebody else will jump in here. 

Some find one way or another easier or that's how they go it working so you can try either way.

1. install linux-wlan-ng which is on the cd and then reboot. (If I knew the driver name I'd give you the command to load the module but I don't so all I can recommend is reboot) Then go to system>administration>networking to see if the device is in the list. If so then the driver loaded ok. Try to configure your network. There's a README file in the package with installation instructions if needed.

2. For ndiswrapper there is a link in my signature.

If you go the linux-wlan-ng method, keep notes of what you do to make it work and post back for others.

---

### Post by linuxgrrl on 2005-12-21
I got the MN-510 to work on my parents' machine using linux-wlan-ng.  The prism2_usb module loads automatically when you plug in the device, then you send a couple of commands to load the linux-wlan-ng drivers per the docs, then start the DHCP client.

The connection was a bit flaky at first until I followed someone's suggestion of sending the first linux-wlan-ng setup command twice in a row (I don't remember the whole string, you'll find it in the docs, but it's the one that includes prism2_usb DORESET=1).  That seemed to prevent the connection from shutting down after a few hours.  

I have not been able to get the connection to start properly on boot, despite trying all the suggestions in this forum and others (all involving /etc/hotplug).  Once I figured out what commands worked, I put them in a script that I run manually with sudo after x starts.   If Dad reboots the machine by accident (a weekly thing), he calls me and I tell him how to run it :)

When you are experimenting with the different setup commands to find what works, be sure to unplug the device and re-plug it each time or it won't "take"

I hope this helps you ... it took me several hours of sweat to figure it out!  And if it turns out that ndiswrapper is easier, well, I wish I had been smart enough to ask your question in the first place!
Mary

---

### Post by Hangetsu on 2005-12-21
Thanks for the advice!  Once I get this working, I would *LOVE* to figure out what is different in this regard between SUSE 10 and Ubuntu -- possibly even see if its something that could be considered for a future build.

So far, it looks like I might give the ndiswrapper method a try first -- it seems easier and somewhat less flaky.

---

