---
title: "Bluetooth adapter driver: rocketfish RF-MRBTAD"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by [.root/fail] on 2009-04-23
I got a rocketfish Bluetooth Micro Adapter(RF-MRBTAD). I suppose it was stupid to try using WINE to install the drivers since the drivers would go into the WINE folder, if at all. That doesn't work though, the CD given with the installation software won't work, the only functional option is Exit, which doesn't help. I can on the otherhand take whatever files off the CD and put them where ever, I don't know where though, and beyond that, if and how to make them work with Ubuntu. I looked on the net, no luck, I looked here and didn't find anything. I hope I give enough information, because beyond what I give I can't think of anything else to say, otherwise, I hope anyone reading will ask me, even if they can help or not, so that I can post any needed information that others can read.

My specs are: Ubuntu 8.10, Gnome, and my laptop is a Compaq CQ60-211DX. rocketfish Bluetooth Micro Adapter(RF-MRBTAD)

Also, I'm looking into installing XFCE as another desktop environment I can use, so if any thing can work in that, let me know, please.

Being a newb isn't a good thing.

I feel like I may have made a mistake buying this. I hope I won't regret it.

---

### Post by [.root/fail] on 2009-04-26
I upgraded to Ubuntu 9.04, also.

---

### Post by [.root/fail] on 2009-04-26
The bluetooth application to setting up blue tooth devices loads when I plug the adapter in, but I don't think it fully works with the adapter, even though it recognizes a bluetooth adapter has been plugged in. As said, it came with an installation disk, so I guess I need to figure out how to install the drivers. I'm also wondering if it is suppposed to have some own interface program, which I'd need to run with WINE, then. So, I'm still not sure.

---

### Post by [.root/fail] on 2009-04-28
[http://echochamber.me/viewtopic.php?f=20&t=38441&p=1535086#p1535086](http://echochamber.me/viewtopic.php?f=20&t=38441&p=1535086#p1535086)

Is where a good part of my innformation is on all this.

---

### Post by gbogle7623 on 2009-05-01
I am having the same problem with the same adapter.  The bluetooth icon acknowledges a bluetooth device is attached, but i can't set it up. wizard does not list the adapter.  I'm also running Ubuntu 9.04.....Help.  Also when I run hciotool it shows the mac address of the device.

---

### Post by [.root/fail] on 2009-05-05
Recent updates to ubuntu, including bluetooth don't make any difference. The device and mouse synch and work together when being setup in Vista on the same laptop. Without even needing the installation disk.

I've tried all I could and looked around, still no luck.

---

### Post by [.root/fail] on 2009-05-17
Bump because I still am having no luck.

---

### Post by Pug226 on 2009-05-17
I just bought a Rocketfish Bluetooth Micro Adaptor, RF-BCDM4, and it almost works out of the box. Just had to reset the device using ```
sudo hciconfig hci0 reset.
``` Then ```
sudo hcitool dev
``` showed my device. From there, it was a matter of using the Gnome Bluetooth utility and it found my Bluetooth devices: headset and two blackberries. Now I just need to verify the headset works. ;)

Note: When using ```
sudo hcitool dev
``` to search for Bluetooth devices, the blue light on the Rocketfish adaptor blinks. I have it connected to a USB hub that's connected to the computer. I'm running Jaunty 9.04.

---

### Post by [.root/fail] on 2009-05-18
Thanks. That shows the mouse in the menu, now it's just a matter of them pairing. It keeps saying it fails to pair when the connection is attempted.


STILL NOT RESOLVED. The mouse will be recognized but it will not connect.

---

### Post by Pug226 on 2009-05-22
Check /var/log/syslog and dmesg. Do you see any errors?

Here's the output from my /var/log/syslog:
```
May 22 22:48:02 ubuntu-server bluetoothd[3742]: HCI dev 0 down
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Adapter /org/bluez/3742/hci0 has been disabled
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Stopping security manager 0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: HCI dev 0 up
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Starting security manager 0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.Service on path /org/bluez/3742/hci0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/3742/hci0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.NetworkPeer on path /org/bluez/3742/hci0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.NetworkHub on path /org/bluez/3742/hci0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.NetworkRouter on path /org/bluez/3742/hci0
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.Input on path /org/bluez/3742/hci0/dev_00_19_7F_B4_66_1D
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.Headset on path /org/bluez/3742/hci0/dev_00_19_7F_B4_66_1D
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.Serial on path /org/bluez/3742/hci0/dev_00_C0_F7_A4_45_1D
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Registered interface org.bluez.Serial on path /org/bluez/3742/hci0/dev_00_0A_86_1C_72_00
May 22 22:48:02 ubuntu-server bluetoothd[3742]: Adapter /org/bluez/3742/hci0 has been enabled
May 22 22:48:02 ubuntu-server bluetoothd[3742]: return_link_keys (sba=00:02:76:37:88:BC, dba=00:02:34:03:8D:63)

```

---

### Post by brazilla ray on 2009-07-27
> **Pug226 said:**
> I just bought a Rocketfish Bluetooth Micro Adaptor, RF-BCDM4, and it almost works out of the box. Just had to reset the device using ```
sudo hciconfig hci0 reset.
``` Then ```
sudo hcitool dev
``` showed my device. From there, it was a matter of using the Gnome Bluetooth utility and it found my Bluetooth devices: headset and two blackberries. Now I just need to verify the headset works. ;)

Note: When using ```
sudo hcitool dev
``` to search for Bluetooth devices, the blue light on the Rocketfish adaptor blinks. I have it connected to a USB hub that's connected to the computer. I'm running Jaunty 9.04.

I've been beating my head on the desk trying to figure this out - this worked perfectly. Thanks!

---

### Post by TheUnwiseman on 2009-09-17
Wow, I can't believe it was that simple!  I feel so silly.  Thanks a lot!  I was having the same problems with this adapter.

---

### Post by scyang on 2011-01-11
Hi .root/fail, Rug226,

Can either of you shed some light on my problem?  I'm a returning user now running 9.04 and can't get my MS-5000 Notebook BlueTooth mouse to work.  I have had good luck with my Windows notebook PC with a Nano B/T dongle by Interlink SMI-Link which has  software by Toshiba--a Windows executable program.  The hcitool sees the mouse.
Thanks,
-Steve

---

### Post by walthehippie on 2012-08-11
Couldn't get MRBTAD to work on 12.04 till I did this. Also put your device real close to the dongle for initial discovery and patience, it takes longer than you think it should.

---

### Post by wildmanne39 on 2012-08-11
Thanks for sharing. Thread Closed.

---

