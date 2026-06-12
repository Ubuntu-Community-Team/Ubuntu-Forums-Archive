---
title: "Plextor ConvertX (go7007) doesn't work after system update"
date: 2007-11-06
forum: Mythbuntu
---

### Post by tedder on 2007-11-06
I upgraded from the 20.2 beta to stable. Things seem okay, except my ConvertX has disappeared.

Here's the relevant line from lsusb:
Bus 002 Device 003: ID 093b:a104 Plextor Corp.

I double-checked my loader script, which is executing the following:
fxload -t fx2 -D /proc/bus/usb/002/003 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

When I run that by hand with -vv, I get a return value of zero, and the following output:
```
microcontroller type: fx2
single stage:  load on-chip memory
open RAM hexfile image /lib/firmware/ezusb/hpi_PX-TV402U.hex
stop CPU
write on-chip, addr 0x0b49 len   28 (0x001c)
write on-chip, addr 0x0a6b len  222 (0x00de)
write on-chip, addr 0x0414 len  669 (0x029d)
write on-chip, addr 0x12c4 len   10 (0x000a)
write on-chip, addr 0x0cfe len    2 (0x0002)
write on-chip, addr 0x0cf6 len    8 (0x0008)
write on-chip, addr 0x1290 len   18 (0x0012)
write on-chip, addr 0x12b4 len    8 (0x0008)
write on-chip, addr 0x12a2 len   18 (0x0012)
write on-chip, addr 0x12d2 len    6 (0x0006)
write on-chip, addr 0x0080 len  916 (0x0394)
write on-chip, addr 0x1220 len   24 (0x0018)
write on-chip, addr 0x1250 len   44 (0x002c)
write on-chip, addr 0x10b7 len   54 (0x0036)
write on-chip, addr 0x1238 len   24 (0x0018)
write on-chip, addr 0x0fd2 len  104 (0x0068)
write on-chip, addr 0x12d8 len   35 (0x0023)
write on-chip, addr 0x11ca len   30 (0x001e)
write on-chip, addr 0x127c len   20 (0x0014)
write on-chip, addr 0x0bf6 len   10 (0x000a)
write on-chip, addr 0x0b65 len    2 (0x0002)
write on-chip, addr 0x0db8 len  163 (0x00a3)
write on-chip, addr 0x06b1 len  666 (0x029a)
write on-chip, addr 0x0033 len    3 (0x0003)
write on-chip, addr 0x12ce len    4 (0x0004)
write on-chip, addr 0x0b67 len  142 (0x008e)
write on-chip, addr 0x0ee7 len  118 (0x0076)
write on-chip, addr 0x0c00 len  190 (0x00be)
write on-chip, addr 0x0043 len    3 (0x0003)
write on-chip, addr 0x0053 len    3 (0x0003)
write on-chip, addr 0x0d00 len  184 (0x00b8)
write on-chip, addr 0x114e len   44 (0x002c)
write on-chip, addr 0x11a5 len   20 (0x0014)
write on-chip, addr 0x111f len   47 (0x002f)
write on-chip, addr 0x12bc len    8 (0x0008)
write on-chip, addr 0x0cbe len   56 (0x0038)
write on-chip, addr 0x10ed len   50 (0x0032)
write on-chip, addr 0x1080 len   55 (0x0037)
write on-chip, addr 0x004b len    3 (0x0003)
write on-chip, addr 0x094b len  288 (0x0120)
write on-chip, addr 0x117a len   43 (0x002b)
write on-chip, addr 0x11e8 len   56 (0x0038)
write on-chip, addr 0x103a len   70 (0x0046)
write on-chip, addr 0x11b9 len   17 (0x0011)
write on-chip, addr 0x0000 len    3 (0x0003)
write on-chip, addr 0x0e5b len   12 (0x000c)
write on-chip, addr 0x0f5d len  117 (0x0075)
write on-chip, addr 0x0e67 len  128 (0x0080)
EOF on hexfile
write on-chip, addr 0x0bf5 len    1 (0x0001)
... WROTE: 4746 bytes, 49 segments, avg 96
reset CPU

# echo $?
0

```

Ideas? The kernel is newer, and I rebuilt the wis-go7007-linux-0.9.8-patched drivers to match it.

gorecord complains as you'd expect- "Driver loaded but no GO7007".

---

