---
title: "unable to connect to wireless network"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by rhb on 2009-03-27
I installed the Jaunty beta in a spare partition.  It runs ok, but does not connect to the network.  I probably need to try command-line operations to discover the problem.  I am using an old SMC adapter on a usb port.

I use WEP security.  I clicked on the network icon, used the first key setting (wep 40/128 or something like that), and entered the hex digits of the key.  When I clicked "connect", the icon spun for a while with no result.  I tried the manual command I use with the old system:

 sudo ifconfig -v wlan0 up [down first if needed]

The command completed immediately and printed nothing.  I suspect the startup scripts are different now.

Can anyone advise me how to observe the messages exchanged with the router?  I also need to look at DMESG output.  Can I find that on the other partition after I reboot my regular system?

Thanks for any advice you can give.

[edited]:

I got some log messages related to wlan0.  Here they are:

dmesg:

[   11.777416] at76_usb: Atmel at76c50x USB Wireless LAN Driver 0.14beta1 loading
[   11.777448] usb 2-2: firmware: requesting atmel_at76c503-rfmd-acc.bin
[   12.047629] at76_usb: firmware version 8.101.5 #84 (fcs_len 4)
[   12.048634] at76_usb: device's MAC 00:04:e2:4b:00:47, regulatory domain FCC (U.S) (id 16)
[   12.049613] at76_usb: registered wlan0
[   12.049644] usbcore: registered new interface driver at76_usb


messages:

Mar 27 13:49:29 ubuntutest kernel: [   24.951106] r8169: eth0: link down
Mar 27 13:49:29 ubuntutest kernel: [   24.951263] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 27 13:49:30 ubuntutest kernel: [   26.891358] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 13:49:30 ubuntutest kernel: [   26.894353] at76_usb: wlan0: ignored AuthFrame in state 3


messages.0:

Mar 27 12:02:22 ubuntutest kernel: [   11.020108] udev: starting version 140
Mar 27 12:02:22 ubuntutest kernel: [   11.433951] at76_usb: Atmel at76c50x USB Wireless LAN Driver 0.14beta1 loading
Mar 27 12:02:22 ubuntutest kernel: [   11.433983] usb 2-2: firmware: requesting atmel_at76c503-rfmd-acc.bin
Mar 27 12:02:22 ubuntutest kernel: [   11.576452] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Mar 27 12:02:22 ubuntutest kernel: [   11.792068] at76_usb: firmware version 8.101.5 #84 (fcs_len 4)
Mar 27 12:02:22 ubuntutest kernel: [   11.793072] at76_usb: device's MAC 00:04:e2:4b:00:47, regulatory domain FCC (U.S) (id 16)
Mar 27 12:02:22 ubuntutest kernel: [   11.794115] at76_usb: registered wlan0
Mar 27 12:02:22 ubuntutest kernel: [   11.794149] usbcore: registered new interface driver at76_usb


Mar 27 12:02:32 ubuntutest kernel: [   25.961963] r8169: eth0: link down
Mar 27 12:02:32 ubuntutest kernel: [   25.962192] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 27 12:02:36 ubuntutest kernel: [   30.632200] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:02:36 ubuntutest kernel: [   30.637192] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:02:36 ubuntutest kernel: [   30.642192] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:02:36 ubuntutest kernel: [   30.646193] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:02:53 ubuntutest kernel: [   47.067433] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:02:53 ubuntutest kernel: [   47.080428] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:03:28 ubuntutest kernel: [   82.037803] at76_usb: wlan0 join_bss ssid 00:18:39:b5:57:8a timed out
Mar 27 12:04:03 ubuntutest kernel: [  117.509143] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:04:03 ubuntutest kernel: [  117.512145] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:04:03 ubuntutest kernel: [  117.521144] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:04:03 ubuntutest kernel: [  117.564142] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:04:03 ubuntutest kernel: [  117.565139] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:04:53 ubuntutest kernel: [  167.082836] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:04:53 ubuntutest kernel: [  167.083828] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:04:53 ubuntutest kernel: [  167.090835] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:06:55 ubuntutest kernel: [  289.066140] at76_usb: wlan0 join_bss ssid 00:18:39:b5:57:8a timed out
Mar 27 12:06:57 ubuntutest kernel: [  291.746018] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:06:57 ubuntutest kernel: [  291.747023] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:07:35 ubuntutest kernel: [  329.021277] at76_usb: wlan0 join_bss ssid 00:18:39:b5:57:8a timed out
Mar 27 12:07:37 ubuntutest kernel: [  331.083187] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:07:37 ubuntutest kernel: [  331.101184] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:07:37 ubuntutest kernel: [  331.102185] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:07:37 ubuntutest kernel: [  331.107185] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:07:37 ubuntutest kernel: [  331.108189] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:07:37 ubuntutest kernel: [  331.110182] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:07:37 ubuntutest kernel: [  331.114181] at76_usb: wlan0: AssocResp in state 7 ignored
Mar 27 12:07:48 ubuntutest kernel: [  342.500029] at76_usb: wlan0: lost beacon bssid 00:18:39:b5:57:8a
Mar 27 12:08:10 ubuntutest syslogd 1.5.0#5ubuntu3: restart.
Mar 27 12:08:56 ubuntutest kernel: [  410.431485] at76_usb: wlan0: ignored AuthFrame in state 3
Mar 27 12:09:54 ubuntutest kernel: [  468.311789] at76_usb: wlan0: ignored AuthFrame in state 3

---

