---
title: "screen goes black (suddenly and randomly)"
date: 2009-01-22
forum: Multimedia Software
---

### Post by remmosf on 2009-01-22
Hey

My computer has suddenly decided to let my screen go black and I will have to press "ctrl" + "alt" + f6" and then "ctrl" + "alt" + f7" to get back to a visible screen.

I do not know whether it is related to the computer or whether it might be a bug in Ubuntu

My computer:

Dell XPS m1530

Ubuntu

Ubuntu 8.10 64 bit

Does anyone have a clue?

Cheers 
Peter

Output from tail /var/log/Xorg.0.log

(**) Broadcom Corp: YAxisMapping: buttons 4 and 5
(**) Broadcom Corp: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Broadcom Corp: Device reopened after 10 attempts.
(II) Logitech USB Receiver: Device reopened after 10 attempts.
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Logitech USB Receiver: Device reopened after 10 attempts.
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Video Bus: Device reopened after 10 attempts.
pew@tyr:~$ tail /var/log/Xorg.0.log
(**) Broadcom Corp: YAxisMapping: buttons 4 and 5
(**) Broadcom Corp: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Broadcom Corp: Device reopened after 10 attempts.
(II) Logitech USB Receiver: Device reopened after 10 attempts.
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Logitech USB Receiver: Device reopened after 10 attempts.

---

### Post by daniel_93 on 2009-03-01
Hello, 
I have the same problem on a Hp pavillion dv6700, it has the Nvidia GeForce 7150M (I'm trying to use it for CUDA) 

Any help would be great!

I don't know is this is of any help!
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Video Bus: Device reopened after 10 attempts.

---

### Post by marcok on 2009-03-25
same problem with a Dell laptop Inspiron E1505

---

### Post by chipfryer on 2009-08-31
This started happening with me last week. Only a reboot will get things back to normal. Ok other than that.

---

### Post by olmecnz on 2009-09-01
I have been experiencing a similar issue on Acer Aspire One (ubuntu 9.04)

Even with the latest XOrg drivers for Intel it seems that (quite randomly) the display will just go black.

Only way to recover is to reboot.

I tried restarting the GDM service but that didn't resolve the issue. Also Dropping out to console and back with Ctrl + F7 didn't fix it for me....

---

### Post by anujpathania on 2009-09-01
Maybe its a bug, you must report it at Launchpad ASAP and in the mean time keep looking for solution. It maybe a hardware specific problem.

---

### Post by anatolica on 2009-09-14
I have the same problem with Ubuntu Jaunty in Acer Aspire one AOA150 with the latest Xorg installed. The screen doesn't go black only but sometimes displays a single colour - no applications, no nohing. The only way to recover is to restart, and this began to happen rather frequent.

---

### Post by mojo dodo on 2009-09-29
my screen goes black randomly too. im using an acer aspire 5570z laptop. i usually press the sleep button, and then wake it up, and everything is ok after that, but for who knows how long...

---

