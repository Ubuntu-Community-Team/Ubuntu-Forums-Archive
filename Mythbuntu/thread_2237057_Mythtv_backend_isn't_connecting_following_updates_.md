---
title: "Mythtv backend isn't connecting following updates: Mythbuntu 12.04, fixes/0.25 branch"
date: 2014-07-30
forum: Mythbuntu
---

### Post by neutron68 on 2014-07-30
I ran the update manager last night (for the first time in 4 months) and it pulled about 350MB of updates down, including a kernel update.

Mythbuntu Version: 12.04
MythTV Branch : fixes/0.25(v0.25.3-49-gb5adf03)
Linux Mythbuntu 3.5.0-54-generic #81~precise1-Ubuntu SMP Tue Jul 15 04:02:22 UTC 2014

After reboot, Mythtv frontend displays a message "Cound not connect to the master backend server. Is it running? Is the IP address set for it in mythtv-setup correct?", over and over.  
Mythtv *was* able to connect to the backend before the update, an hour earlier.

I need help troubleshooting this.  

What log files should I look in for clues?

---

### Post by neutron68 on 2014-07-30
I got it solved.  The cause wasn't the updates.  It was the power supply of the Hauppauge HDPVR box!

It turns out that the HDPVR wasn't getting recognized by the system any more.  This is from the syslog whenever the HDPVR was powered up:
> Jul 30 18:10:34 Mythbuntu kernel: [ 4553.832068] usb 2-5: new full-speed USB device number 14 using ohci_hcd
Jul 30 18:10:34 Mythbuntu kernel: [ 4554.016046] usb 2-5: device descriptor read/64, error -62
Jul 30 18:10:35 Mythbuntu kernel: [ 4554.304043] usb 2-5: device descriptor read/64, error -62
Jul 30 18:10:35 Mythbuntu kernel: [ 4554.584041] usb 2-5: new full-speed USB device number 15 using ohci_hcd
Jul 30 18:10:35 Mythbuntu kernel: [ 4554.768048] usb 2-5: device descriptor read/64, error -62
Jul 30 18:10:35 Mythbuntu kernel: [ 4555.056066] usb 2-5: device descriptor read/64, error -62
Jul 30 18:10:36 Mythbuntu kernel: [ 4555.336052] usb 2-5: new full-speed USB device number 16 using ohci_hcd
Jul 30 18:10:36 Mythbuntu kernel: [ 4555.744060] usb 2-5: device not accepting address 16, error -62
Jul 30 18:10:36 Mythbuntu kernel: [ 4555.920046] usb 2-5: new full-speed USB device number 17 using ohci_hcd
Jul 30 18:10:37 Mythbuntu kernel: [ 4556.328050] usb 2-5: device not accepting address 17, error -62
Jul 30 18:10:37 Mythbuntu kernel: [ 4556.328085] hub 2-0:1.0: unable to enumerate USB device on port 5
(another symptom was that no /dev/video0 was present).
With no /dev/video0 present, the Mythbuntu Backend Setup software wasn't able to close out gracefully and thus the backend wasn't starting (even after a reboot!).  
It's like the backend got locked by the Mythbuntu Backend Setup software??

After I replaced the power supply to the HDPVR, the HDPVR was recognized again (as seen from the syslog)
> Jul 30 18:19:22 Mythbuntu kernel: [ 5081.539932] usb 2-5: New USB device found, idVendor=2040, idProduct=4903
Jul 30 18:19:22 Mythbuntu kernel: [ 5081.539944] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 30 18:19:22 Mythbuntu kernel: [ 5081.539952] usb 2-5: Product: Hauppauge HD PVR
Jul 30 18:19:22 Mythbuntu kernel: [ 5081.539958] usb 2-5: Manufacturer: AMBA
Jul 30 18:19:22 Mythbuntu kernel: [ 5081.539963] usb 2-5: SerialNumber: 00A7500E
and the Mythbuntu Backend Setup software was happy and closed out gracefully, and started the backend for me.  After that, the backend worked again and all the recorded programs in the database showed up again!

That was a weird mystery.  I never expected a USB device could keep the backend from connecting!

---

### Post by neutron68 on 2014-08-08
I looked at the output of the failed 5V HDPVR supply under a load.
The rating on the supply says 3 Amps.  

I put an 8 Ohm resistive load on it, which should have been a mere 0.625 Amps at 5V.
It didn't stand up...no wonder the HDPVR didn't work right!

When I measured it with a Voltmeter, that mess averaged out to about 2.7V

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20140806_174649_zpsdaf33910.jpg[/IMG]

---

