---
title: "network printer not recognized"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by mamboze on 2011-07-07
Hi,

I have a desktop and a laptop connected by ssh (Places>Connect to Server). This works OK for file sharing but the laptop does not recognize the 2 printers attached to the desktop machine. As I understand (??) it, if the 2 printers are set up as 'shared' in CUPS (as they are on the desktop) then they should be recognized by the other machine on the network. But this is not happening. Is this the right way to network printers? 

Any help much appreciated.

---

### Post by chili555 on 2011-07-07
I think the desktop with the printer attached also has to publish the printer. Open Printing > Server > Settings and check off Publish. See attached.

---

### Post by mamboze on 2011-07-07
Hi,

Printing > Settings > Publish is checked already

---

### Post by mamboze on 2011-07-07
Solved, yah yah yah!! 

On the laptop, Printing > Settings > Show printers shared by other systems  **checked**

Printing > Settings > Connect > CUPS server  **set to 192.168.1.2 (desktop address)**

Chili555, you pointed the way. Thanks :D

---

