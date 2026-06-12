---
title: "LIRC &amp; FTDI receiver - constantly disconnecting"
date: 2015-11-06
forum: Multimedia Software
---

### Post by piotr28 on 2015-11-06
Hi,
I'm trying to get this pair working. I have a simple ftdi receiver connected to my computer. While i start mode2 or irrecord i get
```
 piotr@xxx:~$ sudo mode2 --driver=ftdi -dserial=A9W7VPPT
mode2: Initializing FTDI: serial=A9W7VPPT
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK
mode2: opened FTDI device 'serial=A9W7VPPT' OK

```

it's similar with irrecord:
```

irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK

Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK
irrecord: opened FTDI device 'serial=A9W7VPPT' OK

```

after each call of irrecord i receive a notification in dmesg saying that the device was disconnected, it stops working. This happend both while connected to the computer directly as well as to active usb hub. I also tried adding a large capacitor between +5 and GND of TSOP. Needless to say, nothing changed. 

Has anyone encountered anything similar? Can anyone suggest something?

---

