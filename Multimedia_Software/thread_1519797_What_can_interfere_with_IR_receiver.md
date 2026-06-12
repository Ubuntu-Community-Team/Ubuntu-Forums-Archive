---
title: "What can interfere with IR receiver?"
date: 2010-06-28
forum: Multimedia Software
---

### Post by Kdar on 2010-06-28
I am not really sure where to post this, but anyways..

I bought a Remote (with IR receiver) recently - RRC-127, which is similar to GP-IR02BK with same receiver.

Few days ago, I got it working on my laptop. The way I did it is: I removed previously install LIRC by make uninstall and removing from apt-get. Next I install CVS version by make & make install, and than reinstalled version from apt-get "sudo apt-get install lirc". This somehow worked (maybe CVS version had some extra files which wasn't included in Ubuntu's repository).
On Laptop it works just fine, I even installed XBMC to see if it will work there, and it did.

However, when I started to do the same things on my HTPC (the installation of LIRC). I did everything 100% same like what I did on laptop. Next, on HTPC, I connected receiver into USB port and run irw in terminal. I tried pressing few things on my remote...irw didn't return anything.. and also... receiver's light after that would not turn off, always stay on, unless I unplug the receiver.

In contrast, on Laptop that light would show up only when something pressed. (even when LIRC wasn't installed, so I am pretty such its not LIRC problem).

What do you think is wrong with it?

Why do I have this LED light problem on my HTPC (and Desktop too) but not on Laptop?
(They all use same Linux)

I also tried moving away Receiver far from LCD TV, but it didn't really help. Maybe there is something else that makes it function like this.

---

### Post by wyliecoyoteuk on 2010-06-28
Have you tried booting with the Receiver in the USB port?

---

### Post by Kdar on 2010-06-28
I rebooted few times with receiver plugged in, and it did the same thing.
One press on remote lights up LED light on receiver and it would never shut off, unless I unplug it.

---

### Post by undecim on 2010-06-28
Have you looked at dmesg to see if there's anything useful there?

Otherwise, the only thin I can think of would be another IR remote or maybe a running microwave, since microwaves and IR waves are similar wavelength.

---

### Post by cariboo on 2010-06-28
This isn't a cafe thread, moved to multimedia & video

---

### Post by Kdar on 2010-06-29
> **cariboo907 said:**
> This isn't a cafe thread, moved to multimedia & video

sorry for that

> Have you looked at dmesg to see if there's anything useful there?

Otherwise, the only thin I can think of would be another IR remote or maybe a running microwave, since microwaves and IR waves are similar wavelength.

Here what I got from dmesg

```
[22490.424020] usb 4-1: new full speed USB device using uhci_hcd and address 5
[22490.619619] usb 4-1: configuration #1 chosen from 1 choice
[22551.562620] lo: Disabled Privacy Extensions
[22563.208539] usb 4-1: USB disconnect, address 5
[22578.804019] usb 4-1: new full speed USB device using uhci_hcd and address 6
[22579.004128] usb 4-1: configuration #1 chosen from 1 choice
```

Does it mean anything? I disconnected and connected it again there.
What is meaning of uhci_hcd?

I tried using modprobe
```
[armen@armen-desktop uhci_hcd]$ modprobe -r uhci_hcd
FATAL: Module uhci_hcd not found.

```

---

