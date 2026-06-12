---
title: "LIRC with a Homebrew IR Reciever"
date: 2011-02-05
forum: Mythbuntu
---

### Post by mr_luksom on 2011-02-05
Hi,

I'm having issues getting my homebrew receiver to be recognised by mode2.

Software-wise, I have followed the directions here:

[http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install)

The setup I am using is from lirc.org, using the ZD1952 IR Receiver.
```

IC1 = TSOP 1738
+-----------------------+ 3                           R1 (4k7)
|               data -> +--------------------------------+------------o DCD
|                       |                 _______        | 
|      ______________   |                | 78L05 |      | |   D1 (1N4148)
|     /                 |    +-----+-----|OUT  IN|--+   | |
|    (                  | 2  |     | +   |__GND__|  |    |      | /|
|     \______________ + +----+   -----       |      +----+------|< |--o RTS
|                       |        -----       | IC2              | \|
|                       | 1        |         |
|                     - +----------+---------+------------------------o GND
+-----------------------+      C1 (4.7µF)


```

The voltage regulation circuit appears to be working fine (+5V to VCC pin of the IR Transmitter), however I cannot get mode2 to represent anything! I have tried chaning the serial port in the lirc configuration from ttyS1 to ttyS0, but still no luck.

Has anyone else had experience with this IR transmitter (ZD-1952)? Am I missing something obvious?

---

### Post by thatguruguy on 2011-02-05
How are you running mode2?

Do you have a /dev/lirc0?

---

### Post by thatguruguy on 2011-02-05
Also, FWIW, I breadboarded my receiver setup prior to my final build to make sure it worked.  The pinouts on a couple of my parts were different than in the diagrams.  Breadboarding the circuit and using an LED for testing helped me make sure the circuit was right.  (I got the idea from [here]("http://www.engadget.com/2006/05/16/how-to-ir-remote-control-your-computer/").)

---

### Post by mr_luksom on 2011-02-05
I took your advice and had a second look at my homebrew receiver. I don't have a breadboard to try it out on, but after rebuilding from scratch it seems to work a treat now (mode2, irw & myth working fine).

My best guess is that I put the pull-up resistor in the wrong place.

Thanks for the tip!

---

