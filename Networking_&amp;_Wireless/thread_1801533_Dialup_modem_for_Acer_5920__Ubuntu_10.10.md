---
title: "Dialup modem for Acer 5920 / Ubuntu 10.10"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by afz12 on 2011-07-10
I have an Acer 5920 notebook with dual partition XP and Ubuntu 10.10. I would like the Ubuntu partition to use dialup as a secondary option to Wifi / Ethernet. The XP partition runs dialup OK and both partitions have no issues with Wifi or Ethernet. Is there a straightforward way to implement dialup in Ubuntu 10.10?

Thanks in advance

---

### Post by Je Et on 2011-07-10
There is no straightforward way since there are quite a few different modems. Linux goes by '**chipset**', not modem or PC brands. The first thing to do is get and run **scanmodem**. It will give you all the information you need to compile and install the modem for your machine. You will also need the** wvdial **and **dkms** packages, these are on the Ubuntu disc.

---

### Post by jmore9 on 2011-07-10
I used dialup for a while last year.  If you use a serial modem , one that connects via the serial port , it will be easier.

When i setup mine i just hooked up the modem when the machine was off ( hooked up top the serial port ), then turned on the machine.  I did not have to load any drivers at all.

After it was installed i went to a terminal and typed pppconfig and followed the instructions.   I don't remember if you have to use sudo or not.

I always had to change the serial port in the pppconfig to 0 from 1 because it always stuck the modem on 1.

After the pppconfig was done and i saved it , i closed the terminal and opened a new one.   Probley did not need to close and open , huh !

In the new terminal i just typed sudo pon to turn of the modem.  Your number to dial is installed when you use pppconfig from above.  You will here a dial tone and then the modem dialing.  When connection is made you have internet.

Hope that helps i am going from memory here so i may have left something out.

---

### Post by jmore9 on 2011-07-10
Oh yea to turn off just type poff or sudo poff

---

