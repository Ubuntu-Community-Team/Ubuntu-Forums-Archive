---
title: "LIRC: mode2 works but irw stuttering"
date: 2009-02-25
forum: Multimedia Software
---

### Post by kilian27 on 2009-02-25
Hello all!

I am using LIRC 0.8.3 on Mythbuntu 8.10 with an homebrew serial IR receiver. The mainboard is an Asus M3N78.
In principle, the receiver works: Its LED is flashing when I press a button on the remote. Also, mode2 generates a lot of output lines immediately on every keypress. But with irw, the output is very "stuttering", i.e. it shows a signal only every 10 seconds or for one in 50 keypresses or so.
Google gave me some hint about using hdparm for IDE drives, but my HDD is a SATA drive, only the CD-ROM is IDE (but was not in use during my LIRC experiments). The system was idle.
When I grep for LIRC in /var/log/messages I find some "ignoring spike" lines which appeared in those times when I tried to get something out of irw.

See below for the output of several commands.

Has anyone an idea what could cause the problem?
Thanks in advance!
Kilian


I call this script on startup through a link in /etc/rcS.d/ :
```
$ cat /etc/init.d/homebrew
#! /bin/sh
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
start-stop-daemon --start --quiet --exec /usr/sbin/lircd
```

Also, there is:
```
$ cat /etc/modprobe.d/lirc-serial
alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8
```

Continously pressing keys on the remote for some minutes gives only very few signals received by irw:
```
$ irw
0000000000000090 00 Program_Up Sony_RM-836
0000000000000090 01 Program_Up Sony_RM-836
0000000000000090 02 Program_Up Sony_RM-836
0000000000000090 03 Program_Up Sony_RM-836
0000000000000092 00 Volume_Up Sony_RM-836
0000000000000092 00 Volume_Up Sony_RM-836
00000000000001cf 00 Down Sony_RM-836
```

mode2 reacts immediately:
```
$ sudo /etc/init.d/lirc stop
$ sudo mode2
space 2964651
pulse 2322
space 484
pulse 620
space 562
pulse 813
[..] (about 20-30 "space" and "pulse" lines for each button press)
```

LIRC related things in log:
```
$ grep lirc /var/log/messages
Feb 24 21:55:10 mythbox kernel: [   15.852836] lirc_dev: IR Remote Control driver registered, major 61
Feb 24 21:55:10 mythbox kernel: [   16.352151] lirc_serial: auto-detected active low receiver
Feb 24 21:55:10 mythbox kernel: [   16.352155] lirc_dev: lirc_register_plugin: sample_rate: 0
Feb 24 22:03:37 mythbox kernel: [  525.940872] lirc_serial: ignoring spike: 1 1 49a460a9 49a460a9 d5a7b d4e47
Feb 24 22:03:42 mythbox kernel: [  530.940905] lirc_serial: ignoring spike: 1 1 49a460ae 49a460ae d5a9c d4fcf
Feb 24 22:03:45 mythbox kernel: [  533.940920] lirc_serial: ignoring spike: 0 1 49a460b1 49a460b1 d5aab d4e23
Feb 24 22:03:50 mythbox kernel: [  538.940949] lirc_serial: ignoring spike: 0 1 49a460b6 49a460b6 d5ac8 d4f58
Feb 24 22:03:59 mythbox kernel: [  547.940998] lirc_serial: ignoring spike: 0 1 49a460bf 49a460bf d5af9 d4d8e
Feb 24 22:04:08 mythbox kernel: [  556.941047] lirc_serial: ignoring spike: 0 1 49a460c8 49a460c8 d5b2a d5050
Feb 24 22:04:09 mythbox kernel: [  557.941055] lirc_serial: ignoring spike: 1 1 49a460c9 49a460c9 d5b32 d4e62
Feb 24 22:04:10 mythbox kernel: [  558.941060] lirc_serial: ignoring spike: 1 1 49a460ca 49a460ca d5b38 d4f1b
```

---

### Post by jurgen24 on 2009-06-17
I have a similar problem and the IR is picking up interference from my plasma TV. The mobo is M3N78-EM and I'm also using homebrew serial.

I noticed that the voltage on the Regulator pin is a little lower (6.77V) than on another machine that the receiver was working fine. This could cause a problem for the voltage reg.

If I run, the following and press the same key, I see that the waveform is not stable.
$ sudo xmode2 -d /dev/lirc0 -t 1 -m

I'm thinking 5V into the IR is not stable, hence the intermittent results. I'm planning of picking up a stable 5V off the mobo and trying again. I also noticed that irrecord could only pick up raw codes.

running: Linux myth-htpc 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Regards, Jurgen.

---

### Post by jurgen24 on 2009-06-19
I tried playing around with the voltage (removed RTS and connected to 12V) and with higher and lower pull-up resistor. It had no visible effect on the waveform captured by xmode2. This seems to rule out any instability in the IR chip.

I have now re-run the xmode command on two machines. The upper waveform (see attach) (using -m switch) is the failing machine, the lower one is working. As you can see the waveform is super sharp on the working system.

Are there any low level serial port commands/attributes that could be used to clean up the top waveform? I read somewhere that lirc_serial work off interrupts, are there some issues with interrupts on this mobo (Asus M3N78-EM)?

---

### Post by ktbos on 2011-03-28
I've got the same issue with spikes and I haven't been able to figure it out.  (Also an ASUS motherboard, though that's probably just coincidence.)  jurgen24, did you ever get past your problem and if so, please update the post to let me us how you did it!!

---

### Post by tarasian666 on 2013-04-08
Same problem, also asusMy xmode2[[IMG]http://imageshack.us/a/img593/3231/92614498.th.png[/IMG]](http://imageshack.us/photo/my-images/593/92614498.png/)

---

### Post by tarasian666 on 2013-04-08
xmode2 -m[[IMG]http://img203.imageshack.us/img203/3416/39268008.png[/IMG]](http://imageshack.us/photo/my-images/203/39268008.png/)(different RC)

---

### Post by oldos2er on 2013-04-08
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

