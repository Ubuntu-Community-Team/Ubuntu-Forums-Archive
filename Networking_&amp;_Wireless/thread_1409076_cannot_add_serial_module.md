---
title: "cannot add serial module"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by meniscus.mike on 2010-02-17
Hi
I am trying to connect to a serial device on USB port using the pyserial code.
Have added pyserial successfully and have configured my default serial device to dev/ttyUSB0 in minicom
Am trying to use the pyserial code by typing import serial into my Python Shell ...but always comes back with ImportError: No module named serial
 
So although I have successfully installed pyserial it does not appear the the serial module is available
 
I am a Python and Ubuntu novice and have spent several days trying to resolve so any assistance is much appreciated.

---

### Post by GeorgeVita on 2010-02-17
Hi **meniscus.mike**, welcome to this forum!

Take a look at: [http://ubuntuforums.org/showthread.php?t=1235241](http://ubuntuforums.org/showthread.php?t=1235241)
and [http://ubuntuforums.org/showthread.php?t=829416](http://ubuntuforums.org/showthread.php?t=829416)

>>> python serial application (paragraph #4): [http://ubuntuforums.org/showthread.php?t=1083710](http://ubuntuforums.org/showthread.php?t=1083710)

In general search ubuntuforums for: python serial ttyUSB0

Mind that minicom LOCKS a communication port when running and this specific port canNOT be used by other application at the same time.

I think that you have to test your ideas via python environment and possibly place a wire (jumper) between pins 2 & 3 (DB9 connector). In this way you will get back all transmitted characters (h/w echo, loopback). When you succeed TX & RX characters you can try with your peripheral.

Regards,
George

---

