---
title: "Modem hangs within 2 minutes"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by alfotis on 2006-02-13
Hi all,

My internet connection is ISDN 64K and my modem is USB Intracom NetMod.

Everytime I connect with wvdial, connects fine but then, after exactly two minutes, pppd dies with error code either 16 or 15 (one day dies with 15, the other with 16!!!!)

Here is my /etc/wvdial.conf. I don't have any .wvdialrc

```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1
#Init3 =
Area Code =
Phone = 8962407070
Username = my_username
Password =
Ask Password = 1
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 300
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1
```

Here's the wvdial termination...
```
--> Connect time 2.0 minutes.
--> Disconnecting at Sun Feb 12 16:54:33 2006
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
```

and here's /var/log/messages
```
Feb 12 16:54:02 localhost pppd[8710]: appear to have received our own echo-reply!
Feb 12 16:54:33 localhost pppd[8710]: No response to 4 echo-requests
Feb 12 16:54:33 localhost pppd[8710]: Serial link appears to be disconnected.
Feb 12 16:54:33 localhost pppd[8710]: Connect time 2.0 minutes.
Feb 12 16:54:33 localhost pppd[8710]: Sent 63198 bytes, received 567324 bytes.
Feb 12 16:54:33 localhost pppd[8710]: Connection terminated.
Feb 12 16:54:33 localhost pppd[8710]: Exit.
```

I don't understand why it keeps notifying me about serial, while my modem is usb. I also don't understand why my connection works fine for 2 minutes and then hangs!!!

Really annoying. Now I'm stuck with silly Windoze to surf around...

---

### Post by alfotis on 2006-02-13
Anyone plz? Need Help

---

### Post by GTvulse on 2006-02-13
[QUOTE=alfotis]Anyone plz? Need Help[/QUOTE]
Your ISP doesn't use the LCP protocol, yet your connection is setup to send LCP pìngs. Check /etc/ppp/options and make sure that LCP is not enabled there. As well, do you have an active /etc/ppp/peers/provider file, I guess? Check that one as well.

---

### Post by alfotis on 2006-02-14
Great man!

Thanks a lot. Now works Fine...

---

