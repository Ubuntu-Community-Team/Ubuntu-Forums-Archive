---
title: "&quot;Not supported card here (PCI id 14e4:4311)!&quot; fix! Check it out."
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Rawrstin on 2011-05-02
Alright, so ever since the new 11.04 version came out, I've had this stupid error dealing with my wireless card saying it wasn't a supported card when it actually was whilst I was trying to install the firmware for it.

The original error code;
```

Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.

```

After a bit of research, I've finally found a fix for this! All you need is three simple lines.
```

sudo apt-get update
sudo apt-get firmware-b43-installer
sudo modprobe b43

```

Now your card should be recognized and working again!
Hopefully it works for everyone.

---

