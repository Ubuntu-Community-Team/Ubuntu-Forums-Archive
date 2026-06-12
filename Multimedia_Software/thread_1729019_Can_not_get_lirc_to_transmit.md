---
title: "Can not get lirc to transmit"
date: 2011-04-14
forum: Multimedia Software
---

### Post by rickg100 on 2011-04-14
I have an Ubuntu 10.04 install with Myth TV working (been stable for ~1 year). 2 tuner cards (hauppauge 350 and 1600), no lirc (using a wireless keyboard to control it)

I'm now trying to set up lirc and an IR blaster so I can hook up my digital cable box, rather than just my analog cable. I bought a serial ir blaster from [www.irblaster.info](www.irblaster.info). I installed lirc and lirc-module-src and after a few hiccups I thought I had things working.

I can start lirc from the command line and it starts with no errors:
```
sudo lircd -n
```
in another terminal I use irsend to send a command
```
sudo irsend  SEND_ONCE SAE8000 power
```
I get no error from the irsend command and lircd reports
```
lircd: lircd(default) ready, using /var/run/lirc/lircd
lircd: accepted new client on /var/run/lirc/lircd
lircd: removed client
```
but nothing is being transmitted.

I have an IR repeater that flashes when any IR is detected and it does not flash when I issue the irsend command (nor does mt STB respond).

The fact I'm not getting any errors from irsend or lircd is making this hard to debug. 

Any ideas?

---

