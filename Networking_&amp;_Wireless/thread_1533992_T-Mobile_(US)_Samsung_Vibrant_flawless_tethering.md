---
title: "T-Mobile (US) Samsung Vibrant flawless tethering"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by benanzo on 2010-07-18
I just thought I'd share that the new Samsung Galaxy S variant on T-Mobile US (the Vibrant) works perfectly for USB tethering in Ubuntu 10.04.  I just plugged in the USB cable and Network Manager automatically detected the new "Mobile Broadband" connection.

Not sure if it matters, but I chose "T-Mobile G1" as the plan and it connected immediately.  No more ConnectBot + adb + ssh tunnels to get simple USB tethering!  Kudos all-around.

EDIT: It appears PPP tethering is only active when "USB Debugging" is enabled on the phone, which leads me to believe this is an "unintentional" feature ... but I hope it was intended!  Either way, it _just works_.

Thanks,

Ben

---

### Post by Zer0Nin3r on 2010-08-04
I was able to get the Vibrant to tether with my desktop, but not with my Toshiba U-405d laptop.  For the desktop I just place the phone in Samsung Kies connection mode on the phone and plug it into the desktop and setup a mobile broadband connection using the T-Mobile G1 presets and it works flawlessly!

I thought the laptop would work the same, but having some problems.  I notice I get this message in my sys logs:

```
Aug  4 10:53:50 193 kernel: [  958.920084] usb 1-1: new high speed USB device using ehci_hcd and address 4
Aug  4 10:53:50 193 kernel: [  959.071828] usb 1-1: configuration #4 chosen from 1 choice
Aug  4 10:53:50 193 kernel: [  959.074313] cdc_acm 1-1:4.0: This device cannot do calls on its own. It is not a modem.
Aug  4 10:53:50 193 kernel: [  959.074819] cdc_acm 1-1:4.0: ttyACM0: USB ACM device
```

I'm wondering if I have some packages installed on the desktop that I don't have installed on the laptop.

**Update**

Alright so I went back to the desktop to see what messages were being captured and now I cannot get the tethering to work as before.  So I'm thinking there must have been an app or crash that gave me access to the tethering ability under the Samsung Kies mode when connected to Ubuntu.  I also wonder if there was an update that went out over night that just happened.  Unfortunately I didn't check the firmware or baseband before turning in for the night.

Before (working):

```
Aug  4 01:32:40 192 kernel: [ 3460.089555] usb 1-6: USB disconnect, address 5
Aug  4 01:32:44 192 kernel: [ 3463.910048] usb 1-6: new high speed USB device using ehci_hcd and address 6
**[COLOR="Red"]Aug  4 01:32:44 192 kernel: [ 3464.052262] usb 1-6: configuration #2 chosen from 1 choice[/COLOR]**
Aug  4 01:32:44 192 kernel: [ 3464.056761] scsi11 : SCSI emulation for USB Mass Storage devices
Aug  4 01:32:44 192 kernel: [ 3464.057224] usb-storage: device found at 6
Aug  4 01:32:44 192 kernel: [ 3464.057228] usb-storage: waiting for device to settle before scanning
Aug  4 01:32:49 192 kernel: [ 3469.053311] usb-storage: device scan complete
Aug  4 01:32:49 192 kernel: [ 3469.055308] scsi 11:0:0:0: Direct-Access     SAMSUNG  SGH-T959 Card    0000 PQ: 0 ANSI: 2
Aug  4 01:32:49 192 kernel: [ 3469.055831] scsi 11:0:0:1: Direct-Access     SAMSUNG  SGH-T959         0000 PQ: 0 ANSI: 2
Aug  4 01:32:49 192 kernel: [ 3469.057334] sd 11:0:0:0: Attached scsi generic sg2 type 0
Aug  4 01:32:49 192 kernel: [ 3469.063929] sd 11:0:0:0: [sdb] Attached SCSI removable disk
Aug  4 01:32:49 192 kernel: [ 3469.069013] sd 11:0:0:1: Attached scsi generic sg3 type 0
Aug  4 01:32:49 192 kernel: [ 3469.077786] sd 11:0:0:1: [sdc] Attached SCSI removable disk
Aug  4 01:33:05 192 kernel: [ 3484.315527] usb 1-6: USB disconnect, address 6
Aug  4 01:33:15 192 kernel: [ 3494.570085] usb 1-6: new high speed USB device using ehci_hcd and address 7
Aug  4 01:33:15 192 kernel: [ 3494.723347] usb 1-6: configuration #2 chosen from 1 choice
Aug  4 01:33:15 192 kernel: [ 3494.724803] scsi12 : SCSI emulation for USB Mass Storage devices
Aug  4 01:33:15 192 kernel: [ 3494.725143] usb-storage: device found at 7
Aug  4 01:33:15 192 kernel: [ 3494.725147] usb-storage: waiting for device to settle before scanning
Aug  4 01:33:20 192 kernel: [ 3499.723220] usb-storage: device scan complete
Aug  4 01:33:20 192 kernel: [ 3499.725306] scsi 12:0:0:0: Direct-Access     SAMSUNG  SGH-T959 Card    0000 PQ: 0 ANSI: 2
Aug  4 01:33:20 192 kernel: [ 3499.725777] scsi 12:0:0:1: Direct-Access     SAMSUNG  SGH-T959         0000 PQ: 0 ANSI: 2
Aug  4 01:33:20 192 kernel: [ 3499.726734] sd 12:0:0:0: Attached scsi generic sg2 type 0
Aug  4 01:33:20 192 kernel: [ 3499.735526] sd 12:0:0:1: Attached scsi generic sg3 type 0
Aug  4 01:33:20 192 kernel: [ 3499.740670] sd 12:0:0:0: [sdb] Attached SCSI removable disk
Aug  4 01:33:20 192 kernel: [ 3499.744415] sd 12:0:0:1: [sdc] Attached SCSI removable disk
Aug  4 01:33:21 192 kernel: [ 3501.080416] usb 1-6: USB disconnect, address 7
Aug  4 01:33:29 192 kernel: [ 3508.530079] usb 1-6: new high speed USB device using ehci_hcd and address 8
Aug  4 01:33:29 192 kernel: [ 3508.682225] usb 1-6: configuration #2 chosen from 1 choice
Aug  4 01:33:29 192 kernel: [ 3508.683039] scsi13 : SCSI emulation for USB Mass Storage devices
Aug  4 01:33:29 192 kernel: [ 3508.683373] usb-storage: device found at 8
Aug  4 01:33:29 192 kernel: [ 3508.683377] usb-storage: waiting for device to settle before scanning
Aug  4 01:33:34 192 kernel: [ 3513.683220] usb-storage: device scan complete
Aug  4 01:33:34 192 kernel: [ 3513.685307] scsi 13:0:0:0: Direct-Access     SAMSUNG  SGH-T959 Card    0000 PQ: 0 ANSI: 2
Aug  4 01:33:34 192 kernel: [ 3513.685780] scsi 13:0:0:1: Direct-Access     SAMSUNG  SGH-T959         0000 PQ: 0 ANSI: 2
Aug  4 01:33:34 192 kernel: [ 3513.686667] sd 13:0:0:0: Attached scsi generic sg2 type 0
Aug  4 01:33:34 192 kernel: [ 3513.686961] sd 13:0:0:1: Attached scsi generic sg3 type 0
Aug  4 01:33:34 192 kernel: [ 3513.703123] sd 13:0:0:0: [sdb] Attached SCSI removable disk
Aug  4 01:33:34 192 kernel: [ 3513.710702] sd 13:0:0:1: [sdc] Attached SCSI removable disk
Aug  4 01:33:47 192 kernel: [ 3526.332500] usb 1-6: USB disconnect, address 8
Aug  4 01:38:34 192 kernel: [ 3813.800093] usb 1-6: new high speed USB device using ehci_hcd and address 9
Aug  4 01:38:34 192 kernel: [ 3813.952103] usb 1-6: configuration #4 chosen from 1 choice
Aug  4 01:38:35 192 kernel: [ 3814.714709] cdc_acm 1-6:4.0: This device cannot do calls on its own. It is not a modem.
Aug  4 01:38:35 192 kernel: [ 3814.715038] cdc_acm 1-6:4.0: ttyACM0: USB ACM device
Aug  4 01:38:35 192 kernel: [ 3814.716474] usbcore: registered new interface driver cdc_acm
Aug  4 01:38:35 192 kernel: [ 3814.716481] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  4 01:38:35 192 modem-manager: (ttyACM0) opening serial device...
Aug  4 01:38:35 192 modem-manager: (ttyACM0): probe requested by plugin 'Generic'
Aug  4 01:38:36 192 modem-manager: (ttyACM0) closing serial device...
Aug  4 01:38:36 192 modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:0a.1/usb1/1-6 claimed port ttyACM0
Aug  4 01:38:36 192 modem-manager: Added modem /sys/devices/pci0000:00/0000:00:0a.1/usb1/1-6
Aug  4 01:38:36 192 modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:0a.1/usb1/1-6 as /org/freedesktop/ModemManager/Modems/0
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): new GSM device (driver: 'cdc_acm')
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): now managed
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): device state change: 1 -> 2 (reason 2)
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): deactivating device (reason: 2).
Aug  4 01:38:36 192 NetworkManager: <info>  (ttyACM0): device state change: 2 -> 3 (reason 0)
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) starting connection 'T-Mobile T-Mobile G1 1'
Aug  4 01:38:49 192 NetworkManager: <info>  (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug  4 01:38:49 192 modem-manager: (ttyACM0) opening serial device...
Aug  4 01:38:49 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Aug  4 01:38:49 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Aug  4 01:38:49 192 modem-manager: Registration state changed: 5
Aug  4 01:38:49 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Aug  4 01:38:49 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Aug  4 01:38:49 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) scheduled...
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) starting...
Aug  4 01:38:49 192 NetworkManager: <info>  (ttyACM0): device state change: 4 -> 5 (reason 0)
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) successful.
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 2 of 5 (Device Configure) complete.
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) started...
Aug  4 01:38:49 192 NetworkManager: <info>  (ttyACM0): device state change: 5 -> 7 (reason 0)
Aug  4 01:38:49 192 NetworkManager: <info>  Starting pppd connection
Aug  4 01:38:49 192 NetworkManager: <debug> [1280911129.709384] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyACM0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Aug  4 01:38:49 192 NetworkManager: <debug> [1280911129.749247] nm_ppp_manager_start(): ppp started with pid 3536
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) complete.
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP6 Configure Get) started...
Aug  4 01:38:49 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug  4 01:38:50 192 pppd[3536]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Aug  4 01:38:50 192 pppd[3536]: pppd 2.4.5 started by root, uid 0
Aug  4 01:38:50 192 pppd[3536]: Using interface ppp0
Aug  4 01:38:50 192 pppd[3536]: Connect: ppp0 <--> /dev/ttyACM0
Aug  4 01:38:50 192 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug  4 01:38:50 192 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug  4 01:38:50 192 pppd[3536]: CHAP authentication succeeded: Welcome!
Aug  4 01:38:50 192 pppd[3536]: CHAP authentication succeeded
Aug  4 01:38:50 192 kernel: [ 3829.710828] PPP BSD Compression module registered
Aug  4 01:38:50 192 kernel: [ 3829.758543] PPP Deflate Compression module registered
Aug  4 01:38:54 192 pppd[3536]: Cannot determine ethernet address for proxy ARP
Aug  4 01:38:54 192 pppd[3536]: local  IP address 26.114.44.XX
Aug  4 01:38:54 192 pppd[3536]: remote IP address 26.114.44.XX
Aug  4 01:38:54 192 NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Aug  4 01:38:54 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  4 01:38:54 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  4 01:38:54 192 NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  4 01:38:54 192 NetworkManager: <info>  Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  4 01:38:54 192 NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) started...
Aug  4 01:38:55 192 NetworkManager: <info>  Policy set 'Auto XXXXX' (wlan0) as default for routing and DNS.
Aug  4 01:38:55 192 NetworkManager: <info>  (ttyACM0): device state change: 7 -> 8 (reason 0)
Aug  4 01:38:55 192 NetworkManager: <info>  Activation (ttyACM0) successful, device activated.
Aug  4 01:38:55 192 NetworkManager: <info>  Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  4 01:39:05 192 ntpdate[3607]: adjust time server 91.189.94.XX offset 0.214080 sec
Aug  4 01:39:34 192 NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 39)
Aug  4 01:39:34 192 NetworkManager: <info>  (wlan0): deactivating device (reason: 39).
Aug  4 01:39:34 192 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2603
Aug  4 01:39:34 192 NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Aug  4 01:39:34 192 NetworkManager: <info>  Policy set 'T-Mobile T-Mobile G1 1' (ppp0) as default for routing and DNS.
Aug  4 01:39:34 192 avahi-daemon[867]: Withdrawing address record for 192.168.1.XX on wlan0.
Aug  4 01:39:34 192 avahi-daemon[867]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.XX.
Aug  4 01:39:34 192 avahi-daemon[867]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug  4 01:39:34 192 kernel: [ 3874.121343] wlan0: deauthenticating from b0:e7:54:67:91:XX by local choice (reason=3)
Aug  4 01:39:35 192 wpa_supplicant[1177]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  4 01:41:18 192 NetworkManager: <info>  (ttyACM0): device state change: 8 -> 3 (reason 39)
Aug  4 01:41:18 192 NetworkManager: <info>  (ttyACM0): deactivating device (reason: 39).
Aug  4 01:41:18 192 NetworkManager: <WARN>  check_one_route(): (ppp0) error -34 returned from rtnl_route_del(): Sucess#012
Aug  4 01:41:18 192 pppd[3536]: Terminating on signal 15
Aug  4 01:41:18 192 pppd[3536]: Connect time 2.4 minutes.
Aug  4 01:41:18 192 pppd[3536]: Sent 527176 bytes, received 427457 bytes.
Aug  4 01:41:18 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Aug  4 01:41:18 192 pppd[3536]: Connection terminated.
Aug  4 01:41:18 192 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug  4 01:41:19 192 pppd[3536]: Exit.
Aug  4 01:41:19 192 modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
Aug  4 01:41:19 192 modem-manager: Got failure code 3: No carrier
Aug  4 01:41:21 192 NetworkManager: <debug> [1280911281.001331] ensure_killed(): waiting for ppp pid 3536 to exit
Aug  4 01:41:21 192 NetworkManager: <debug> [1280911281.001481] ensure_killed(): ppp pid 3536 cleaned up
```

After (Not working):

```
Aug  4 12:44:59 192 kernel: [ 1696.200060] usb 1-6: new high speed USB device using ehci_hcd and address 15
Aug  4 12:44:59 192 kernel: [ 1696.352031] usb 1-6: configuration #4 chosen from 1 choice
Aug  4 12:44:59 192 kernel: [ 1696.353691] cdc_acm 1-6:4.0: This device cannot do calls on its own. It is not a modem.
Aug  4 12:44:59 192 kernel: [ 1696.353949] cdc_acm 1-6:4.0: ttyACM0: USB ACM device
```

**Update**

Rooted the phone and still don't have plug & play tethering as before.

**Update**

Ended up setting up the EasyTether and it works with Ubuntu.  One just needs to download the client for their Android phone via Android Market and then install the drivers onto the PC.

Drivers: [http://www.mobile-stream.com/easytether/drivers.html]("http://www.mobile-stream.com/easytether/drivers.html")

How to get it working with Ubuntu:

```
Step 1: Download the drivers at http://www.mobile-stream.com/easytether/drivers.html
Step 1.5: Install said drivers. duh

Step 2: plug your android device into your laptop

Step 3: run easytether and ensure USB is checked.

Step 4: open up terminal and type "easytether enumerate" without the quotes. Then your devices id number will appear.

Step 5: type "sudo easytether connect #########" without quotes. Replace #s with serial num. This will bring up another command.

Step 6: open up another terminal window. THE OTHER ONE HAS TO STAY OPEN. type in "sudo dhclient easytether0" without quotes into the new window. This will configure your phone and signal.

Step 7: Enjoy. When you are done press CTRL+C in the original window to disconnec
```

Walkthrough source: [http://thebarbee.blogspot.com/2010/07/easytether-for-android-ububntu-style.html]("http://thebarbee.blogspot.com/2010/07/easytether-for-android-ububntu-style.html")

---

### Post by wbm on 2010-08-04
Hello, I am looking into the Samsung Vibrant too. Could you guys describe your experience on getting music, videos and photos on and off the phone please. E.g. how does it work with rhythmbox on Ubuntu. How does one move files to and from and so on.
How does it sync with calendars on Ubuntu?
Thanks in advance

---

### Post by Zer0Nin3r on 2010-08-04
> **wbm said:**
> Hello, I am looking into the Samsung Vibrant too. Could you guys describe your experience on getting music, videos and photos on and off the phone please. E.g. how does it work with rhythmbox on Ubuntu. How does one move files to and from and so on.
How does it sync with calendars on Ubuntu?
Thanks in advance

A little bit off topic but here we go:

I like the Vibrant a lot.  I was using a jailbroken iPhone 2g before and just got tired of 1) The slow network speeds (2G/EDGE). 2) The phone lost its snap when it came to launching programs and such.

Working with the phone as a Mass Storage device is a snap.  I just drag and drop files as needed and create directories for organizing my files.  The phone rescans the file system to detect changes after unmounting the phone.  I haven't used it with Rhythmbox as I use Songbird.

For calendars I have it set up with Google Calendars which takes care of everything I need and syncs across multiple platforms giving me the flexibility that I need.

Hope this helps.

---

### Post by wbm on 2010-08-04
> **Zer0Nin3r said:**
> A little bit off topic but here we go:

I like the Vibrant a lot.  I was using a jailbroken iPhone 2g before and just got tired of 1) The slow network speeds (2G/EDGE). 2) The phone lost its snap when it came to launching programs and such.

Working with the phone as a Mass Storage device is a snap.  I just drag and drop files as needed and create directories for organizing my files.  The phone rescans the file system to detect changes after unmounting the phone.  I haven't used it with Rhythmbox as I use Songbird.

For calendars I have it set up with Google Calendars which takes care of everything I need and syncs across multiple platforms giving me the flexibility that I need.

Hope this helps.

Thanks for the reply.
So can you just plug the phone in via USB and it shows up?

Doesn't it have music/photos/videos folders already?

Assuming Songbird/Rhythmbox are pretty much similar, can you drag from Songbird to the phone or do you have to drag the actual mp3 files from wherever they are on your machine?

Does it support playlists from Songbird/Rhythmbox?

Thanks, btw. I want to replace my ancient cell phone and my iTouch with one device that can do both if it helps.

---

### Post by anise62 on 2010-10-10
I had tethering for a few days but it was far from flawless for my Samsung Vibrant. Now I get a message that says another widget is using the Kies application. When it worked the tether dropped repeatedly. Is there any place I can go in the US to have my questions answered. I was going to drop my awful Home DSL service and replace it with my tethered cell phone. Looks now like I will be returning the phone. Any advice appreciated.

---

### Post by jsoto67 on 2010-10-20
The same thing happened to me that happened to Zer0nin3r. I was able to tether fine via usb one day and the next day it was gone. Now i'm using easytether but I really wish I could go back to have it working out of the box.

---

