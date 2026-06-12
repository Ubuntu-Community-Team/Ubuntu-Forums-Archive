---
title: "Ttyd"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by jcv on 2006-06-12
Hello from Belgium,

I need to connect a serial printer to my linux but the device is not next to the server.
I'm trying to use a LS100 box from SENA.
It's a serial to ethernet converter box using a TELNET connection.
To speak to the printer box, I 'm invited to use TTYD and declare a device /dev/pty??.

# ttyd -d /dev/ptyp0 192.168.1.50 6001 -b 9600 -p 8NC0
# echo "Hello" > /dev/ttyp0

The printer writes well "Hello" but there are 9 chars before.
   FF FB 80 FF FB 81 FF FB 82

I looked with Ethereal and I saw that ttyd (I think) sent 2 packets :
    the first with only FF FB 80
    the second with FF FB 81 FF FB 82 followed by the Hello string.

If I do directly a telnet connection, like :
# telnet 192.168.1.50 6001
those chars disappear.
It's typicaly when I use TTYD.
 
Do you know where those chars come from ? 
What can I do to remove them ?
Must I configure the /dev/ttyp0 ? How ?

Thank you for your help.

Jean-Christophe

---

