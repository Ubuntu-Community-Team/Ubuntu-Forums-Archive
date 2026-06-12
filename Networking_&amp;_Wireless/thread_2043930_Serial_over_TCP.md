---
title: "Serial over TCP"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by gpgp on 2012-08-17
So sorry i cant quite figure this out on my own. I work in professional entertainment, and many devices that used to be configured through a serial terminal are now configured through serial terminal provided on a tcp port. This is straight forward in the widows software Hyperterminal, you do a tcp/ip winsock connection to an IP# : port#. I cannot figure out how to do this in ubuntu, i can connect to to the devices though serial directly but not over TCP. I have looked at Cutecom, Moserial and other similar software. I have also tried to telnet and to telnet to a specified port with no results. clearly i am missing something fundamental and would appreciate anyones help or advice.

To be clear my intent is to make a tcp connection to a device on the network and be as if i am at the serial console. An example, i have a projector ip 2.0.0.21 port 3001. if i use hyperterminal i put that address and port using winsock tcp/ip but i want to do it in ubuntu. i don't care if it is all in the terminal or not.

Thank you

GPGP

---

### Post by Kleenux on 2012-08-17
'hyperterminal' for a serial connection requires to setup serial settings (stop bit, crc, data bits, parity...).

But a TCP/IP connection should be more straightforward. The destination networked devices will make the necessary translation and transfer the data bytes it gets to the serial interface according to its requirements.

telnet does a raw exchange of bytes (appart from 0xff), and should work. Don't you have firewall issues? The Windows box being allowed, not the Ubuntu one?

---

