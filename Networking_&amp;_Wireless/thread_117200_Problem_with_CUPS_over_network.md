---
title: "Problem with CUPS over network"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-01-14
Hello,
I'm using Breezy on my desktop and on my laptop. On the desktop, I have a Kyocera printer attached to USB, and I can print with it fine. I also want to use this printer over the network from my laptop. On the desktop (where the printer is attached) I have this in my cupsd.conf:

```

ServerName desktop
...
Listen 127.0.0.1:631
Listen 192.168.1.10:631
...
<Location />
#Order Deny,Allow
#Deny From All
#Allow From 127.0.0.1
#Allow From 192.168.1.*
Allow From All
</Location>
[code]

On the laptop, I have this in client.conf:
[code]
ServerName desktop

```

With this setup, I can access all of the CUPS web frontend from both the desktop & the client. But printing does not work. In printers.conf on the desktop, I have this:

```

<DefaultPrinter Kyocera-FS-1010>
Info
Location
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```

From the Gentoo network printing guide - if I understand it right - if I want IPP printing I need this as DeviceURI on the client:
```

DeviceURI http://192.168.1.10:631/ipp/Kyocera-FS-1010

```

But well this does not work. The web frontend on the laptop tells me that "Destination printer does not exist!". Permissions seem to be right, since I can access the web frontend from both computers (I can also go to the admin section remotely) - I just can't print. 

Any help would be greatly appreciated! Is the DeviceURI correct?


Tom

---

