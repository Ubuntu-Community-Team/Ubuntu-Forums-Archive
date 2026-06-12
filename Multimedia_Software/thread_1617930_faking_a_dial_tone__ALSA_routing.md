---
title: "faking a dial tone / ALSA routing"
date: 2010-11-10
forum: Multimedia Software
---

### Post by nicholse on 2010-11-10
I want to fake a dial tone to trick the fax program into initiating the handshake so that I can route the modem out to the line in so any VoIP software will send the fax.

I dont have a copper phone line, I want to trick the modem into talking over VoIP.

How do I fake a dial tone?
How do I route modem/speaker to line in?

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
# wvdial
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
--> Sending: ATDT5551212
--> Waiting for carrier.
ATDT5551212
NO DIALTONE
--> No dial tone.
--> Disconnecting at Tue Nov  9 21:10:23 2010

---

