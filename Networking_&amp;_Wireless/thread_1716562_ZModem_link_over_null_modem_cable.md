---
title: "ZModem link over null modem cable"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by AcIDx0 on 2011-03-28
Hello,

I am writing a simple script which will transmit files over a serial connection. I have simplified the setup to test the solution, so the final configuration will be a bit more complicated.

Current setup:
1. 2 RS232 com ports connected with a null modem in between.
2. Open minicom on both
3. Put in 19200,8,N,1 as parameters
4. Open text travels both ways
5. Files sent over Zmodem transfer well.

Both serial adapters are USB, but I tried it also with real com ports, and same story. For simplicity, I will call one adapter "receiving" and the other "sending" to signify from which side I want to send the files through zmodem.

Then I close minicom on the "sending" site without reseting the port (I have also tried setting everything up with stty)

On sending site:

```
 
sz -vv -b some.file >> /dev/ttyUSB0

```

The minicom on receiving side recognizes that there is a transmission going on and fires up rz. It gets timeouts all the time.
The sending site says: 
Retry 0: Timeout on pathname

I tried googling but no solution helps. Please do not try to suggest to use minicom on both sides, because this is going to be an unattended process in the end.

I would appreciate a step by step on how to transfer a file with zmodem using rz and sz without minicom. 

Thank you!

---

### Post by lloyd_b on 2011-03-28
The problem you're having is because the shell redirection is sending the file out, but has no way of receiving responses from the other system.  Zmodem is a standard packet protocol - system A sends a packet to system B, system B sends an acknowledgement (or a notification of failure) back to A, then A sends the next packet (or resends the failed packet).  As such, rz and sz need to both send and receive via the port.

An experiment to try (not sure if it will work).  On the receiving machine, type the following at a command prompt:```
rz < /dev/ttyUSB0 > /dev/ttyUSB0
```and on the sending machine:```
sz -vv -b some.file > /dev/ttyUSB0 < /dev/ttyUSB0
```

If that doesn't work, you might want to take a look at 'kermit' ("sudo apt-get install ckermit").  It is much better suited to automated tasks than minicom, and I believe it can be configured to use zmodem as well if you absolutely need to use that particular protocol.

Lloyd B.

---

### Post by AcIDx0 on 2011-03-30
Thank you! That worked. I tried doing "<> /dev/ttyUSB0" but that did not work, so I thought that was wrong.

---

