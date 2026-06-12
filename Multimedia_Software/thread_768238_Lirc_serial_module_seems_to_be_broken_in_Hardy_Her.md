---
title: "Lirc_serial module seems to be broken in Hardy Heron"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Noisedsn on 2008-04-26
Today I upgrade my ubuntu 7.10 to 8.04. Everything works fine but not lirc. I use homebrew serial-port IR receiver connected to COM1 but I can't load the lirc_serial module.
When I'm trying to do this manually:
```
sudo modprobe lirc_serial
```
I have the following error:
```
WARNING: Error inserting lirc_dev (/lib/modules/2.6.24-16-generic/updates/dkms/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_serial (/lib/modules/2.6.24-16-generic/updates/dkms/lirc_serial.ko): Invalid module format

```
I have tried either version from repository and compiled from source, but there was the same error...

---

### Post by dentaku65 on 2008-04-26
This happens with i2c too

```
sudo modprobe lirc_i2c
```

```
WARNING: Error inserting lirc_dev (/lib/modules/2.6.24-16-generic/updates/dkms/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_12c (/lib/modules/2.6.24-16-generic/updates/dkms/lirc_i2c.ko): Invalid module format
```

With the last kernel of Hardy:

```
2.6.24-16
```

This is my tv infrared controller (Hauppauge) and I had to switch back to last kernel of Gutsy (on my upgraded machine) to get it work 
:(

---

### Post by dentaku65 on 2008-04-26
Fixed! :)
In my case there was an old package causing wrong configuration modules, I remove:

```
sudo apt-get --purge remove dkms
```

And now it's ok.

---

### Post by Noisedsn on 2008-04-29
dentaku65: Thank you! This solution works fine for me.

---

