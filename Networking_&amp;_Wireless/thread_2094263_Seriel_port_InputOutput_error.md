---
title: "Seriel port Input/Output error"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by alex2356 on 2012-12-13
I am using Ubuntu 12.04.01 and need to communicate with a device via a serial port on back of the desktop. Of course, I have no idea if the physical device is ```
/dev/ttyS0
``` or a different port. And of course, I have neither an idea what the correct UART is nor the port. 

```
sudo setserial -g /dev/ttyS?
``` gives the following:
```

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 0
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0

```where I guess I have set the UART's of the first two ports myself. A ```
cat /etc/ttyS...
``` always gives an 'Input/output error'  and 'dmesg' gives the error message   ```
LSR safety check engaged!
```. Does this mean that the port numbers are maybe incorrect? How to find and and how to fix that?


Thanks
  Alex

---

