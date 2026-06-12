---
title: "unable to read/write serial port /dev/ttyS0"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by tanu1985 on 2011-11-07
Hi

I have connected a windows PC and a Debian one with null modem cable(serial port).I am trying to establish communication between two systems.
I am using hyperterminal on windows and cutecom on Debian.
Now,i am able to send data from windows pc to debian one
but not able to send data from Debian PC to windows one.
not sure why?I checked /dev/ttyS0 on debian,everything seems to be fine...but still its not working....any suggestions??

---

### Post by Cheesehead on 2012-06-03
You should need cutecom (or any terminal program) only on the client.

Also, make sure you're really using a null-modem cable instead of a data cable. 


Let's assume the Debian machine is the server, and the PC is the client (terminal).

**On both machines**, make sure nothing else is tying up the port. Spurious and leftover processes cause interference.

1) Use [FONT="Courier New"]ps -e | grep ttyS0[/FONT] to look for a running tty already owning the port. If you find one, [FONT="Courier New"]kill[/FONT] it.
2) Use [FONT="Courier New"]ps -e | grep cutecom[/FONT] to ensure NO cutecom or other terminal programs are operating on the port. They interefere. If you find one, [FONT="Courier New"]kill[/FONT] it.

3) **On the server**, set up the port using [FONT="Courier New"]sudo getty -L ttyS0 115200 vt100[/FONT]. This command will not respawn the port after a disconnect, so you might need to do it a few times.

4) **On the client**, launch the terminal program and try to connect. Baud is 115200, Term emulation is VT100, 8n1 (of course). On a Debian client, I happen to use the 'screen' application for other purposes, but it's also a good serial VT100 terminal.

Common Pitfalls:
    Make sure you didn't start multiple terminal program sessions (they interfere)
    Make sure neither machine is running both getty and termianl on the same port (they interfere)
    Make sure both sides are using the same speed (115200 in this example). Getty does not usually auto-negotiate speeds!
    Try varying which service starts first. After each attempt, kill both the terminal and getty services (but only the getty running on that port!)

---

