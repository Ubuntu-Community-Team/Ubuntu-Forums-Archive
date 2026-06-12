---
title: "Envy Installs ATI but no fireglcontrol"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by switterstx on 2007-03-08
I'll admit right up front this is my first week with this but I've gotten fairly far.  

Used TSeliot's Envy (seems ok) and went through the generic ATI install.  At the end there were two dialog boxes that had yes and no buttons but no text.  First try selected no and that damaged my x11.conf file and I jumped back to text version of envy.  Used text interface, tried to install but was prompted for confirmation of install two or three times but no install.  Removed, tried install again same confirmation bug, tried manual and it seemed to work.  

Rebooted, synaptics wanted to update somethings, all seemed normal.  Reboot again, tried to run fireglcontrol and this is all I get:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I have decent resolution but would like to do a wide desktop if possible and check for other options.  glxgears seems to behave fine, no errors and it seems to be chugging happily away.  

Here's the config:
Ubuntu 6.06.1 AMD64 desktop, ATI FireGL V3300

Any and all help would be greatly appreciated.

---

### Post by switterstx on 2007-03-17
Anyone have any idea what that code means?  Any help would be greatly appreciated.

---

