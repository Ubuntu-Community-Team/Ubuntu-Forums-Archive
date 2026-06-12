---
title: "Vbox2 Advanced (eMPIA 28xx?)"
date: 2010-12-28
forum: Multimedia Software
---

### Post by dcook32p on 2010-12-28
I purchased an XCM Vbox2 Advanced a few weeks back, and I would like to put up a good effort to get this to work in Ubuntu instead of Windows. I've read several people discussing the em28xx drivers (which I believe this peripheral requires), but everyone says they're built-in to the kernel and the device should auto-detect.

When I plug the device in, dmesg shows:

```
usb 1-5: new high speed USB device using ehci_hcd and address 7
```

I then run lsmod, but the em28xx module isn't showing up in the list. lsusb shows:

```
Bus 001 Device 007: ID eb1a:8165 eMPIA Technology, Inc.
```

I'm still relatively new to Ubuntu and Linux in general, so I really have no idea where to even start with this. Would one of you fine people please help me with this?

---

### Post by dcook32p on 2010-12-29
I have read in a few places that some of the em28xx devices require a "hint" in the form of:

```
sudo modprobe em28xx card=?
```

where the "?" is supposed to be a specific number. One poster said they checked the source code to find out, but I'm afraid I'm not terribly savvy with source code.

When I put in numbers that others say work (so far 2, 35, and 64), modprobe loads the em28xx module (it is listed several times in lsmod's output), but I still don't have a /dev/video0 or similar. In fact, ls /dev returns the same output after loading the module as it does prior to it.

Any suggestions?

---

### Post by switcha on 2011-11-20
I too would like to know if this has any support on ubuntu as I would like to play my wii using it. Right now, though, I am limited because its software is only available using XP. I don't want to run WINE, I would much prefer a ubuntu alternative.

---

### Post by switcha on 2012-03-17
Bump - any updates on this?

---

