---
title: "mobile broadband via bluetooth in Jaunty?"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by HankB on 2009-04-27
Is this possible?

I have managed to pair my phone (LG VX8350 using Verizon) with my Eee PC 901 and I have created a mobile broadband connection using nm-applet, but I have no idea how to connect the two.

My phone shows up on the "Bluetopoth Preferences" applet. There are icons at the bottom  of the screen for a plug and four point star. I have no idea what they do or where to look for help. (They have no bubble text nor is there a help button for this applet.)

I've searched the forum and found [http://ubuntuforums.org/showthread.php?t=598890](http://ubuntuforums.org/showthread.php?t=598890). I think it may be out of date WRT Jaunrty, but I tried it anyway. When I get to the part where it asks to run "hcitool scan", I've done so. It reports nothing after about 10 seconds:
```
root@bonsai:~# time hcitool scan 
Scanning ...

real	0m10.251s
user	0m0.004s
sys	0m0.004s

```

bluetooth messages in daemon.log include:
```
Apr 27 11:00:05 bonsai bluetoothd[2719]: Discovery session 0xb9b4a628 with :1.270 activated
Apr 27 11:00:32 bonsai bluetoothd[2719]: Discovery session 0xb9b4a628 with :1.270 activated
Apr 27 11:00:50 bonsai last message repeated 2 times
Apr 27 11:01:20 bonsai bluetoothd[2719]: Discovery session 0xb9b4a628 with :1.273 activated
Apr 27 11:03:31 bonsai bluetoothd[2719]: pin_code_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:xx:xx:xx)
Apr 27 11:03:40 bonsai bluetoothd[2719]: Discovery session 0xb9b43588 with :1.275 activated
Apr 27 11:03:51 bonsai bluetoothd[2719]: link_key_notify (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:xx:xx:xx, type=6)
Apr 27 11:03:55 bonsai bluetoothd[2719]: link_key_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:09:27:34)
Apr 27 11:04:03 bonsai bluetoothd[2719]: pin_code_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:xx:xx:xx)
Apr 27 11:04:06 bonsai bluetoothd[2719]: Agent replied with an error: org.bluez.Error.Rejected, Pairing request rejected
Apr 27 11:04:07 bonsai bluetoothd[2719]: /org/bluez/2719/hci0/dev_00_1F_E3_09_27_34: error updating services: Invalid exchange (52)
Apr 27 11:04:50 bonsai bluetoothd[2719]: Discovery session 0xb9bxxx88 with :1.276 activated
Apr 27 11:04:57 bonsai bluetoothd[2719]: link_key_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:09:27:34)
Apr 27 11:04:57 bonsai bluetoothd[2719]: pin_code_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:09:27:34)
Apr 27 11:05:12 bonsai bluetoothd[2719]: link_key_notify (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:09:27:34, type=6)
Apr 27 11:05:14 bonsai bluetoothd[2719]: Registered interface org.bluez.Serial on path /org/bluez/2719/hci0/dev_00_1F_E3_xx_xx_xx
Apr 27 11:05:14 bonsai bluetoothd[2719]: Registered interface org.bluez.Control on path /org/bluez/2719/hci0/dev_00_1F_E3_xx_xx_xx
Apr 27 11:05:14 bonsai bluetoothd[2719]: probe failed with driver input-headset for device /org/bluez/2719/hci0/dev_00_1F_E3_xx_xx_xx
Apr 27 11:07:11 bonsai bluetoothd[2719]: Discovery session 0xb9b4xxx0 with :1.277 activated
Apr 27 11:07:19 bonsai bluetoothd[2719]: link_key_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:09:27:34)
Apr 27 11:08:10 bonsai bluetoothd[2719]: Discovery session 0xb9b4xxx0 with :1.281 activated
Apr 27 11:33:33 bonsai pand[25228]: Bluetooth PAN daemon version 4.32
Apr 27 11:33:33 bonsai pand[25228]: Inquiring
Apr 27 11:34:21 bonsai bluetoothd[2719]: link_key_request (sba=00:15:AF:F9:8A:F5, dba=00:1F:E3:xx:xx:xx)
Apr 27 11:51:27 bonsai bluetoothd[2719]: Discovery session 0xb9b4xxx0 with :1.291 activated

```


Is the information at [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup) relevant?

Pointers to where to look for further information would be appreciated.

thanks,
hank

---

### Post by Mohamed Samy on 2009-04-28
check this website [http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html](http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html) 
it will help

---

### Post by HankB on 2009-04-28
> **Mohamed Samy said:**
> check this website [http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html](http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html) 
it will help
Thanks for the tip. I have implemented that with some changes. The chat script that seems to work for my phone is:

```
TIMEOUT 35
ECHO ON
ABORT '\nBUSY\r'
ABORT '\nERROR\r'
ABORT '\nNO ANSWER\r'
ABORT '\nNO CARRIER\r'
ABORT '\nNO DIALTONE\r'
ABORT '\nRINGING\r\n\r\nRINGING\r'
'' \rAT
OK ATD*777
```
It seems to work as the phone shows 
```
DATA CALL
*777
RX:
TX:
```
on the front screen. Unfortunately it does not seem to proceed beyond that. From daemon.log I see:
```
Apr 28 11:02:16 bonsai chat[4770]: send (^MAT^M)
Apr 28 11:02:16 bonsai chat[4770]: expect (OK)
Apr 28 11:02:16 bonsai chat[4770]: AT^M^M
Apr 28 11:02:16 bonsai chat[4770]: OK
Apr 28 11:02:16 bonsai chat[4770]:  -- got it 
Apr 28 11:02:16 bonsai chat[4770]: send (ATD*777^M)
Apr 28 11:02:16 bonsai pppd[4766]: Script /usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup finished (pid 4769), status = 0x0
Apr 28 11:02:16 bonsai pppd[4766]: Serial connection established.
Apr 28 11:02:16 bonsai pppd[4766]: using channel 3
Apr 28 11:02:16 bonsai pppd[4766]: Using interface ppp0
Apr 28 11:02:16 bonsai pppd[4766]: Connect: ppp0 <--> /dev/rfcomm0
Apr 28 11:02:17 bonsai pppd[4766]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3fa674ba> <pcomp> <accomp>]
Apr 28 11:02:44 bonsai last message repeated 9 times
Apr 28 11:02:47 bonsai pppd[4766]: LCP: timeout sending Config-Requests 
Apr 28 11:02:47 bonsai pppd[4766]: Connection terminated.
Apr 28 11:02:47 bonsai pppd[4766]: Receive serial link is not 8-bit clean:
Apr 28 11:02:47 bonsai pppd[4766]: Problem: all had bit 7 set to 0
Apr 28 11:02:48 bonsai pppd[4766]: Modem hangup
Apr 28 11:02:48 bonsai pppd[4766]: Exit.

```

So it seems to not be able to establish the PPP connection. I have only just called Verizon to enable this so it may not yet be fully enabled on their end.

---

