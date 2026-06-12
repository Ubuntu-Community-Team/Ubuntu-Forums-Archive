---
title: "Driver not loading in kernel?  Kubuntu 13.10"
date: 2014-04-11
forum: Multimedia Software
---

### Post by kooldino on 2014-04-11
After much tinkering, I've finally found a driver that works properly with my GeForce 7300LE - the Nvidia_304 driver.

However, when I boot the machine, it will load up in just a terminal screen.

If I try to start x, it gives me several error..

```
NVIDIA: could not open the device file /dev/nvidiaact1 (no such device or address).
```


However, it will load the desktop in full res if I do the following...

```
$ sudo modprobe nvidia_304
$ startx 
```

So it appears to not be loading the driver into the kernel until I run modprobe, correct?  If so, how can I automatically load it?

---

### Post by kooldino on 2014-04-11
Ok, so I went into /etc/modules and I added a new line:

```
nvidia_304
```

^that's the name of my driver module.  Now it auto loads into the GUI and all seems well.  Hooray.

---

