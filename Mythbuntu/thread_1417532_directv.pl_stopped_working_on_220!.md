---
title: "directv.pl stopped working on 2/20!"
date: 2010-02-27
forum: Mythbuntu
---

### Post by IceCap on 2010-02-27
I just found out that my directv.pl (controlling a D11-800) stopped working on Saturday (between 7 and 11pm) based on the MythTV log.
  When I try using it manually from the command line, it exists with "Error excessive retries" so clearly it isn't communicating at all.  This has been working for over a year now so I'm a bit perplexed.  What I think might have happened:

[LIST]
[*]If I remember correctly I ran update manager on Saturday and upgraded several packages.  I'm wondering if I have some permission issues, but I'm not sure how to check for that.
[*]The space in my media center is a little small so the serial cable on my Myth box gets a little bit squished.  Maybe my cable is bad (simple to check out by getting a new cable).
[*]I have been running with 9600 baudrate.  I tried 115200 since few years ago lot of the D1x boxes ran this but it didn't work.  Anyway, the firmware on the box hasn't been changed (according to the box).  I tried restarding the box as well and it didn't change anything.
[/LIST]

  Does anyone have any other ideas of what might have changed or how I can verify that I don't have any permission issues?

  It's a Mythbuntu 9.10, running with PVR-350.

  Thanks

  IC

---

### Post by IceCap on 2010-02-27
Looking at lshw output I get this:

*-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ef00(size=32)

  Is this normal or did I somehow loose the driver for the serial port?

  Thanks

  IceCap

---

### Post by IceCap on 2010-03-01
So I booted into the live CD, ran "./directv.pl on" from a USB drive and it worked so there is nothing wrong with the hardware.

  Where can I look up which updates were installed last which seem to have broken the serial port usage (or at least the directv.pl script use of the serial port)? 

  Anyone have any insight what might have gone wrong?  While the script isn't working I can't watch live TV and I can't record from the TV either.

  Thanks

  IceCap

---

### Post by mrand on 2010-03-01
[http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial](http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial) seems to say that if you're getting that error message, you might be talking out the wrong port.  Perhaps an update (one update related log is /var/log/dpkg.log) caused this, or else it is a low probability event that that was a day you happened to reboot your computer and it happened to hit the low probability event for device name assignment?

Just stabbing around in the dark,

[INDENT]Marc[/INDENT]

---

### Post by IceCap on 2010-03-03
> **mrand said:**
> [http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial](http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_%28STB%29_via_USB_or_Serial) seems to say that if you're getting that error message, you might be talking out the wrong port.  Perhaps an update (one update related log is /var/log/dpkg.log) caused this, or else it is a low probability event that that was a day you happened to reboot your computer and it happened to hit the low probability event for device name assignment?
[INDENT]Marc[/INDENT]

  The port is correct (I'm pretty sure).  The script defaults to /dev/ttyS0 (COM1) which hasn't changed.  I tried /dev/ttyS1 for the hell of it, but it came with another error (port not defined or something like that) since there is only one serial port on the motherboard.
  I'll check the log to see what was updated but even if I can figure that out, I'm not sure if that can help me (I don't know what to do with that information).
  If the port is not on ttyS0 (and it is not on ttyS1) where could it possibly be?

  Thanks

  IceCap

---

### Post by IceCap on 2010-03-04
I looked at the dpkg.log and the upgrade was actually several days earlier.  I checked and the login account (not mythtv) is in the 'dialout' group.  The /dev/ttyS0 appears to be setup in identical way as when I boot from the Mythbuntu 9.10 CD (when directv.pl works).  I.e.

```
$: sudo setserial -a -v /dev/ttyS0

/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

$: dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.204810] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.205305] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

  Note that the directv.pl script sets and uses baud rate of 9600.

  So I'm at a loss.  Like I mentioned in the first post (12h off), the box recorded and commercial flagged at 8AM and then failed at 11AM.  Both were APCI wakeups and to the best of my knowledge no one touched it.
  Does anyone know what the directv.pl script uses control the serial port?  Maybe I need to re-install a package.

  Thanks

  IceCap

---

### Post by IceCap on 2010-03-05
I changed the access for /dev/ttyS0 with "chmod 777 /dev/ttyS0" (was crw_rw____) and then reinstalled the "setserial" package and one of these (or both) fixed the issue. 

  Thanks

 IC

---

