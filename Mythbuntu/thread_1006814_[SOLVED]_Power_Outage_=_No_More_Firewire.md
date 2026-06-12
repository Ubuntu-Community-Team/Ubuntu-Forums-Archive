---
title: "[SOLVED] Power Outage = No More Firewire"
date: 2008-12-09
forum: Mythbuntu
---

### Post by dmfrey on 2008-12-09
I had a strange occurrence this past weekend.  I had a series of power dips and the a power outage for about an hour.

Now when I turn my mythtv on, the 1394 subsystem gets initialized (according to dmesg), however, the raw1394 module never gets loaded nor does the /dev/raw1394 device.

I have added raw1394 to /etc/modules and on reboot /dev/raw1394 gets created, however, my firewire input is no longer available in mythtv.

Running plugreport shows the following
```

Host Adapter 0
==============

Node 0 GUID 0x001e8c0001516fbd
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

```

I am at a loss for what to do here.  Any suggestions?  It was working prior to this power outage.

Thanks.

---

### Post by volkswagner on 2008-12-10
Does the cable box have two firewire ports?  Sometimes these get swapped.  

You can try to power off your mythbox.   Turn off the cable box, and unplug it from the power source.  Change the firewire cable to the "other" port.  Then plug the cable box back in.  Turn on the cable box and let it fully boot, then reboot your myth box.

---

### Post by dmfrey on 2008-12-10
> **volkswagner said:**
> Does the cable box have two firewire ports?  Sometimes these get swapped.  

You can try to power off your mythbox.   Turn off the cable box, and unplug it from the power source.  Change the firewire cable to the "other" port.  Then plug the cable box back in.  Turn on the cable box and let it fully boot, then reboot your myth box.

volkswagner,
Thanks, I power cycled both the cable box and the mythbuntu box, but I did not try changing the firewire cable port on the cable box.  I will give that a shot tonight when I get back home.

---

### Post by dmfrey on 2008-12-10
I powercycled both the mythbuntu box and the rcn cable box.  I changed the firewire port port on the cable box as well.  No go.

I started thinking that it is probably UDEV that is handling creating this device.  I looked and in the UDEV rules there is a rule file to give access to the firewire device to mythtv.  However, it cannot get a handle on it.

When I do get the device created (modprobe raw1394) and I run plugreport, I get the same output as before.

Any other thoughts?

Thanks.

---

### Post by volkswagner on 2008-12-11
If you try one more time with the port swap on the box without joy, you may want to exchange the box.  Since it was working in the past, I doubt the firewire cable is defective, although it would be good to confirm it.

You should also try to confirm your PC's firewire port works with an alternate device, to rule out the MOBO or add on card.

What is the make and model of the cable box.  You may be able to get into the diagnostic page to see if firewire is enabled on the device.

---

### Post by dmfrey on 2008-12-11
The Firewire port is on my motherboard, not an add-in card.  I had one previously, but now have no slots left to insert it into.

The STB is a Motorola DCT-6200 (not the one with a pvr built in) from RCN in Allentown, PA.  Whether or not the STB Firewire is active or not, i should still get a device created in /dev/raw1394, correct?  From what I can tell, it is almost as if the raw1394 module, and associated modules, are not getting loaded anymore on startup.

---

### Post by dmfrey on 2008-12-15
I am not sure what has happened here, but this has resolved itself.  I didn't do anything to it other than open the case, but now the firewire capture is back.

I am going to test a few times just to be sure :)

---

