---
title: "Neotel &amp; pppconfig"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Dogmatix86 on 2010-04-10
I have a Neotel phone which is connected to my server via USB cable.

In order for me to dial an internet connection on the device, I have to 
```
modprobe usbserial vendor=0x1d09 product=0x4000
```then dial the PPP connection using pppconfig. After I dial the connection (pon neotel) and then disconnect the connection (poff neotel), I cannot get the connection to dial up again without disconnecting and reconnecting the usb cable from the device.

/var/log/messages:

A successful connection (pon neotel):

```
Apr 10 18:01:40 server pppd[6791]: pppd 2.4.5 started by root, uid 0
Apr 10 18:01:41 server chat[6794]: send (ATZ^M)
Apr 10 18:01:41 server chat[6794]: expect (OK)
Apr 10 18:01:41 server chat[6794]: ATZ^M^M
Apr 10 18:01:41 server chat[6794]: OK
Apr 10 18:01:41 server chat[6794]:  -- got it
Apr 10 18:01:41 server chat[6794]: send (ATDT#777^M)
Apr 10 18:01:41 server chat[6794]: expect (CONNECT)
Apr 10 18:01:41 server chat[6794]: ^M
Apr 10 18:01:41 server chat[6794]: ATDT#777^M^M
Apr 10 18:01:41 server chat[6794]: CONNECT
Apr 10 18:01:41 server chat[6794]:  -- got it
Apr 10 18:01:41 server chat[6794]: send (\d)
Apr 10 18:01:42 server pppd[6791]: Serial connection established.
Apr 10 18:01:42 server pppd[6791]: Using interface ppp0
Apr 10 18:01:42 server pppd[6791]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 10 18:01:45 server pppd[6791]: Remote message: Welcome to pdsn.
Apr 10 18:01:45 server pppd[6791]: PAP authentication succeeded
Apr 10 18:01:45 server pppd[6791]: local  IP address x.x.x.x
Apr 10 18:01:45 server pppd[6791]: remote IP address x.x.x.x
```Disconnect (poff neotel):

```

Apr 10 18:43:38 server pppd[6791]: Terminating on signal 15
Apr 10 18:43:38 server pppd[6791]: Connect time 41.9 minutes.
Apr 10 18:43:38 server pppd[6791]: Sent 704815 bytes, received 2877241 bytes.
Apr 10 18:43:44 server pppd[6791]: Connection terminated.
Apr 10 18:43:45 server pppd[6791]: Modem hangup
Apr 10 18:43:45 server pppd[6791]: Exit.

```Trying to connect for a second time (pon neotel):

```

Apr 10 18:51:11 server pppd[7481]: pppd 2.4.5 started by root, uid 0
Apr 10 18:51:12 server chat[7483]: send (ATZ^M)
Apr 10 18:51:13 server chat[7483]: expect (OK)
Apr 10 18:51:16 server chat[7483]: ~^?}#@!}9} } }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)@^_bBv~~^?}#@%}!}!} }9}!}$}%\}"}&} }
Apr 10 18:51:22 server chat[7483]:  } } }#}%B#}%}%}&)@^L};9|~~^?}#@!}!}"} }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)@E4v]~~^?}
Apr 10 18:51:25 server chat[7483]: #@!}!}#} }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)@a}7pU~~^?}#@!}!}$} }9}!}$}%\}"}&} } }
Apr 10 18:51:58 server chat[7483]: alarm
Apr 10 18:51:58 server chat[7483]: send (AT^M)
Apr 10 18:51:58 server chat[7483]: expect (OK)
Apr 10 18:52:01 server chat[7483]: ~^?}#@!}9} } }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)AL}0X})~~^?}#@%}!}!} }9}!}$}%\}"}&}
Apr 10 18:52:07 server chat[7483]:  } } } }#}%B#}%}%}&)A<^QY7~~^?}#@!}!}"} }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)AyDcg~~^?
Apr 10 18:52:11 server chat[7483]: }#@!}!}#} }9}!}$}%\}"}&} } } } }#}%B#}%}%}&)Ajm}5;~~^?}#@%}!}$} }9}!}$}%\}"}&} }
Apr 10 18:52:43 server chat[7483]: alarm
Apr 10 18:52:43 server chat[7483]: Failed
Apr 10 18:52:44 server pppd[7481]: Exit.


```Disconnecting USB cable from device:

```

Apr 10 19:02:24 server kernel: [17239.640052] usb 2-2: USB disconnect, address 4
Apr 10 19:02:24 server kernel: [17239.640334] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Apr 10 19:02:24 server kernel: [17239.640356] usbserial_generic 2-2:1.0: device disconnected
Apr 10 19:02:24 server kernel: [17239.640506] generic ttyUSB1: generic converter now disconnected from ttyUSB1
Apr 10 19:02:24 server kernel: [17239.640523] usbserial_generic 2-2:1.1: device disconnected

```Reconnecting USB cable:

```

Apr 10 19:02:40 server kernel: [17255.792016] usb 2-2: new full speed USB device using uhci_hcd and address 5
Apr 10 19:02:40 server kernel: [17255.951102] usb 2-2: configuration #1 chosen from 1 choice
Apr 10 19:02:40 server kernel: [17255.956653] usbserial_generic 2-2:1.0: generic converter detected
Apr 10 19:02:40 server kernel: [17255.956785] usb 2-2: generic converter now attached to ttyUSB0
Apr 10 19:02:40 server kernel: [17255.960099] usbserial_generic 2-2:1.1: generic converter detected
Apr 10 19:02:40 server kernel: [17255.960228] usb 2-2: generic converter now attached to ttyUSB1

```Ive tried killing all processes relating to chat and pppd. Ive also tried doing modprobe -r which doesn't seem to work with usbserial.
Any ideas?

---

