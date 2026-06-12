---
title: "Bluetooth DUN with Sprint..."
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by grndslm on 2009-03-11
I've used Blueman to configure some of the bluetooth setup.  Then I started trying to configure wvdial for the Sprint connection.  Here's my config...

```
[Dialer Defaults]
Stupid Mode = on
Modem = /dev/rfcomm0
ISDN = off
Modem Type = Analog Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Dial Attempts = 1
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Idle Seconds = 0
Auto DNS = on
Ask Password = off
Username = 0
Password = 0
New PPPD = yes
```

Even tho Ask Password is turned off, it still complains about the Username and Password variables being left blank, so I just set them both to 0 and it works...

```
grndslm@MicroBox:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 11 18:12:31 2009
--> Pid of pppd: 8790
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> local  IP address 173.112.x.x
--> pppd: &#65533;&#65533;[06][08]
--> remote IP address 209.97.x.x
--> pppd: &#65533;&#65533;[06][08]
--> primary   DNS address 166.102.165.11
--> pppd: &#65533;&#65533;[06][08]
--> secondary DNS address 166.102.165.13
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
```

... But it only works for 2 and a half minutes.  Then it spits out this junk...

```
--> Connect time 2.5 minutes.
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Disconnecting at Wed Mar 11 18:15:02 2009
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
```

Perhaps my Init string isn't correct??

Another odd thing is that while I'm connected for those 2 and a half minutes, everything seems to work other than firefox.  I can ping, traceroute, and use links2 from the bluetooth DUN conection... but firefox always complains about being in offline mode.  Perhaps Firefox depends on a signal from Network Manager??

I've tried to do this several times before, but I've never gotten this far before.  So any help is definitely greatly appreciated here, guys.  Thanks!!

---

### Post by grndslm on 2009-03-11
BAM!!

I finally got it to work.

I simply edited two variables in /etc/ppp/options both to 0:  lcp-echo-interval & lcp-echo-failure

Now it stays connected.  In both Firefox and Epiphany, I unselected "Work Offline" in the File drop-down menu.

WOOT!!!

---

