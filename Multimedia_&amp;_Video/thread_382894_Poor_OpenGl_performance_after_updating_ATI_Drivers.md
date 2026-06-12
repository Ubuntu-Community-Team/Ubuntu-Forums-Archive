---
title: "Poor OpenGl performance after updating ATI Drivers."
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by BurgesS on 2007-03-12
I updated to the latest video drivers for my ati 9550 using method 2 of this guide :

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Now my OpenGL performance is very slow.

The driver verion is 8.34.8.

```

lspci -n | grep 0300
01:05.0 0300: 1002:4153

```

```

lspci | grep VGA
00:04.4 Non-VGA unclassified device: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
01:05.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

```

Anyone else experience this?

---

