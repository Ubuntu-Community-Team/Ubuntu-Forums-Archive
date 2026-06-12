---
title: "Problem with my Mobile Broadband"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by pinoyskull on 2009-07-04
Hi,

I have my Huawei E220 working in Jaunty for about 2 weeks now then suddenly it stopped working, I tailed the log and I found out that it is connecting but at the end of if it will disconnect.

Anybody has experience with this or somebody found a solution to my problem?


Below is the ppp log

```

Jul  5 10:10:13 freedom pppd[4601]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul  5 10:10:13 freedom pppd[4601]: local  IP address 10.50.202.134
Jul  5 10:10:13 freedom pppd[4601]: remote IP address 10.64.64.64
Jul  5 10:10:13 freedom pppd[4601]: primary   DNS address 202.126.40.5
Jul  5 10:10:13 freedom pppd[4601]: secondary DNS address 222.127.143.5
Jul  5 10:10:25 freedom pppd[4601]: Terminating on signal 15
Jul  5 10:10:26 freedom pppd[4601]: Connect time 0.3 minutes.
Jul  5 10:10:26 freedom pppd[4601]: Sent 0 bytes, received 0 bytes.
Jul  5 10:10:26 freedom pppd[4601]: Connection terminated.
Jul  5 10:10:26 freedom pppd[4601]: Exit.
Jul  5 10:10:32 freedom pppd[4663]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jul  5 10:10:32 freedom pppd[4663]: pppd 2.4.5 started by root, uid 0
Jul  5 10:10:32 freedom pppd[4663]: Using interface ppp0
Jul  5 10:10:32 freedom pppd[4663]: Connect: ppp0 <--> /dev/ttyUSB0
Jul  5 10:10:32 freedom pppd[4663]: No CHAP secret found for authenticating us to UMTS_CHAP_SRVR
Jul  5 10:10:32 freedom pppd[4663]: CHAP authentication succeeded
Jul  5 10:10:32 freedom pppd[4663]: CHAP authentication succeeded
Jul  5 10:10:34 freedom pppd[4663]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul  5 10:10:34 freedom pppd[4663]: local  IP address 10.60.137.6
Jul  5 10:10:34 freedom pppd[4663]: remote IP address 10.64.64.64
Jul  5 10:10:34 freedom pppd[4663]: primary   DNS address 202.126.40.5
Jul  5 10:10:34 freedom pppd[4663]: secondary DNS address 222.127.143.5
Jul  5 10:10:48 freedom pppd[4663]: Terminating on signal 15
Jul  5 10:10:48 freedom pppd[4663]: Connect time 0.3 minutes.
Jul  5 10:10:48 freedom pppd[4663]: Sent 0 bytes, received 0 bytes.
Jul  5 10:10:48 freedom pppd[4663]: Connection terminated.
Jul  5 10:10:48 freedom pppd[4663]: Exit.

```and here is the part of the log when I connect Huawei E220, which I can see failed messages on usb storage, is it related?
```

Jul  5 10:09:41 freedom kernel: [  745.004169] usb 1-4: new high speed USB device using ehci_hcd and address 6
Jul  5 10:09:41 freedom kernel: [  745.136991] usb 1-4: configuration #1 chosen from 1 choice
Jul  5 10:09:41 freedom kernel: [  745.137219] hub 1-4:1.0: USB hub found
Jul  5 10:09:41 freedom kernel: [  745.137379] hub 1-4:1.0: 4 ports detected
Jul  5 10:09:49 freedom kernel: [  753.448363] usb 1-4.4: new full speed USB device using ehci_hcd and address 7
Jul  5 10:09:49 freedom kernel: [  753.541963] usb 1-4.4: configuration #1 chosen from 1 choice
Jul  5 10:09:49 freedom kernel: [  753.542987] usb-storage: probe of 1-4.4:1.0 failed with error -1
Jul  5 10:09:49 freedom kernel: [  753.693366] usb 1-4.4: USB disconnect, address 7
Jul  5 10:09:50 freedom kernel: [  753.956228] usb 1-4.4: new full speed USB device using ehci_hcd and address 8
Jul  5 10:09:50 freedom kernel: [  754.050098] usb 1-4.4: configuration #1 chosen from 1 choice
Jul  5 10:09:50 freedom kernel: [  754.050716] usb-storage: probe of 1-4.4:1.0 failed with error -5
Jul  5 10:09:50 freedom kernel: [  754.050763] option 1-4.4:1.0: GSM modem (1-port) converter detected
Jul  5 10:09:50 freedom kernel: [  754.050937] usb 1-4.4: GSM modem (1-port) converter now attached to ttyUSB0
Jul  5 10:09:50 freedom kernel: [  754.053140] usb-storage: probe of 1-4.4:1.1 failed with error -5
Jul  5 10:09:50 freedom kernel: [  754.053189] option 1-4.4:1.1: GSM modem (1-port) converter detected
Jul  5 10:09:50 freedom kernel: [  754.053335] usb 1-4.4: GSM modem (1-port) converter now attached to ttyUSB1
Jul  5 10:09:50 freedom kernel: [  754.054632] usb-storage: probe of 1-4.4:1.2 failed with error -1

```

---

### Post by loell on 2009-07-05
I don't have a modem :D

how about removing auto ppp0? as suggested here. [http://ubuntuforums.org/showthread.php?t=1177021]("http://ubuntuforums.org/showthread.php?t=1177021")

---

### Post by philcamlin on 2009-07-05
it cant find your ip address

its good that its atleast being recognised

try rebooting or reniwing your ip

sudo /etc/init.d/networking restart:popcorn:

---

