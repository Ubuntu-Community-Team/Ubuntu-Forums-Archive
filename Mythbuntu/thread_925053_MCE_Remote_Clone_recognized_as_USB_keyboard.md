---
title: "MCE Remote Clone recognized as USB keyboard"
date: 2008-09-20
forum: Mythbuntu
---

### Post by ripdajacker on 2008-09-20
Hello

I have just bought a Media Center Remote clone to use with LIRC, but it is recognized as a HID-compatible keyboard. I am running ubuntu 8.04.

The IR-receiver is a USB one:
```
$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b4:0100 Cypress Semiconductor Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```


More info:
```
$ uname -a
Linux snake-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```


```
$ dmesg|grep -i cyp
[  237.149125] input: Cyp Se WitheHome as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input10
[  237.154380] input,hidraw0: USB HID v1.00 Keyboard [Cyp Se WitheHome] on usb-0000:00:1d.1-1
[  696.836587] input: Cyp Se WitheHome as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input11
[  696.882291] input,hidraw0: USB HID v1.00 Keyboard [Cyp Se WitheHome] on usb-0000:00:1d.1-1

```

The problem is that irw and irrecord don't read the raw input from the receiver, but only the keystrokes the remote emulates.

Is there a way to disable the HID driver for this specific device from loading?

Thanks in advance

---

### Post by tgm4883 on 2008-09-20
Thats kinda how lirc works.  What is the output if you type "irw" then hit remote buttons?

---

### Post by ripdajacker on 2008-09-20
I get numbers and keystrokes, but I cannot customize them. Example if I run irrecord, I get the message that no input is received after 10 seconds.

---

### Post by tgm4883 on 2008-09-20
> **ripdajacker said:**
> I get numbers and keystrokes, but I cannot customize them. Example if I run irrecord, I get the message that no input is received after 10 seconds.

What do you mean by numbers and keystrokes, can you post some of that output here

---

### Post by ripdajacker on 2008-09-20
Here is the irw output by pressing random keys:
```
$ irw
12345679885
^[[6~^[[5~^[[6~^[[5~
^[[6~
^E

^N^A^T^P^P^F^B
```

The issue is not that irw gets input, it's that kopete, firefox, konsole etc also get the number codes and newline's etc.

KMix also gets the volume up and volume down buttons, and I also tried it on an ubuntu without lirc, same thing.

---

### Post by wizgnome on 2008-11-17
I typed this, **ls /dev/input/by-id **to get the decice name and then edited **/etc/lirc/hardware.conf **to add **REMOTE_DRIVER="devinput"** and **REMOTE_DEVICE="/dev/input/by-id/*name from previous step*"**

Then I typed **lshal | grep input.product **to get the device key and edited **/usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi** putting the string from the output from lshal into **<match key="info.product" contains_ncase="*device string from lshal*">**


Then after a reboot and running **irw** I saw the codes from the button presses. Which I could use in **/etc/lirc/lircd.conf **to do the mappings.

However I found that some keys would not work properly as they sent multiple key codes for a single button press and irw would show the same code for all of them - I think it was the last in the sequence. 

The number keys would only display after pressing the Numlock button otherwise they would work as up/down/left/right/enter.

It looked like the remote was emulating the Numeric keypad on a PC and the Media keys (and a mouse).

I can use it just as a keyboard (without lirc) and map the keys from the frontend setup GUI. 

But the big problem is I don't have enough buttons and have to remember if Numlock is on or off. Most of the function keys wont work either as they send mutiple character codes.

Now I am looking for another Remote to purchase - I will give up on this one - unless someone else has a solution.

---

### Post by phamthanhnam on 2008-12-16
Hi
I have this very cheap remote too, made in China. Though the label on it is "Media Center Remote" and the specification in the manual is "Philips IR" but they are fake. This remote is **not** really an MCE remote, but an infrared keyboard i.e. its signal to computer is not raw infrared signal, but translated keystrokes. So there will not be any device node /dev/lirc* created (and you can not use *mode2*, *irw*, *irrecord* to show raw infrared signal either).
However, you can still use it with lirc:
First, define this remote has which "event number"
**cat /proc/bus/input/devices**
Then, reconfigure lirc:
**sudo dpkg-reconfigure lirc**
Choose "Linux Input Layer (/dev/input/eventX)" as "IR Receiver" at the first screen, "None" as "IR Transmitter" at the second screen, et "/dev/input/eventX" at the last screen in which X is the "event number" above.
Or this link if you see that there are 2 "event numbers" (keyboard and mouse) for your remote:

[http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/](http://blog.viridian-project.de/2008/10/02/hid-remotes-and-lirc/)

Read this:
[http://linux.bytesex.org/v4l2/faq.html#lircd](http://linux.bytesex.org/v4l2/faq.html#lircd)

---

