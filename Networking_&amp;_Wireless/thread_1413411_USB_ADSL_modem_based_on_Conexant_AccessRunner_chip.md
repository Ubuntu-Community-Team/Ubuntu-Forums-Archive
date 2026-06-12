---
title: "USB ADSL modem based on Conexant AccessRunner chipset"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by aryanwicked on 2010-02-22
Hi guys!

:KS **I DID search throughout the forum and ubuntu community web site and googled it before I started writing this!  **

**I switched to ubuntu[9.10]recently so I'm still noob in it. *

I have a USB ADSL MODEM which has no Ethernet port based on DAMN
Conexant AccessRunner chipset. 

This is the exact text which is written on the chipset.
```

conexant
accessRunner
CX82320-13
43001161
0439 KOREA
ARM

```

First Of all I know it s better to buy a brand new ADSL ROUTER with good reputation in Linux but as a computer GEEK I really want to get this modem running on ubuntu :)

1) I downloaded a little tool for obtaining firmware binary from Modem setup CD called "cxacru-fw.c" 
in those tutorials I've read there is a file called **"CnxEtU.sys" ** which has to be extracted with "cxacru-fw"
BUT I dont have such a file on my Modem Setup CD! all I have are listed below
```

CnxTrLan.sys        25.3 KB
CnxTrUsb.sys        51.6 KB
cnxe2fw.bin         2.59 MB  [maybe this is my firmware modem:confused:]
...

```
I get weird error when I try to do like this
```

cxacru-fw CnxTrLan.sys cxacru-fw.bin
or
cxacru-fw CnxTrUsb.sys cxacru-fw.bin
or
cxacru-fw cnxe2fw.bin cxacru-fw.bin

```

2)I copied **cnxe2fw.bin** which was already on my Modem Setup CD directly to /lib/firmware after I plugged my modem in the LED light didn't start blinking at all! :( SO STUCK HERE :(

I also got a **"cxacru-fw.bin"** by searching it on google and tried that one, but still the same!:(

does anybody have experience with this god damn device? :(

---

