---
title: "After exiting Suspend Mode Wireless/Wicd inactive, how to restart?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by KeyboardKowboy on 2009-01-11
Hello All,

I am running Ubuntu 8.10 Desktop and I'm loving it.  Given a few minor to medium issues, resolving them were straight forward.  I was having difficulty getting my wireless card to connect to my router when WPA2 security was enabled.  Installed Wicd and everything has been great.

That being said, I am setting my laptop into suspend mode when I close the lid.  When I return from suspend mode, Wicd picks up on zero devices and my wireless card is completely inactive.  How do I snap my wireless card back into action?

---

### Post by cwall on 2009-01-31
Me too.  Ideas?

---

### Post by freak42 on 2010-02-08
try stopping and restarting wicd on suspend:

alt+f2 
type: 

> gksudo gedit /etc/acpi/suspend.d/54-wicd


and then paste the following into gedit and save:
> #!/bin/sh

# Stop wicd
if [ -x /etc/init.d/wicd ]; then
  /etc/init.d/wicd stop
fi



 and again

> gksudo gedit /etc/acpi/resume.d/79-wicd
paste: 

> #!/bin/sh

# Start wicd
if [ -x /etc/init.d/wicd ]; then
  /etc/init.d/wicd start
fi

taken from : [http://forum.eeeuser.com/viewtopic.php?id=38240](http://forum.eeeuser.com/viewtopic.php?id=38240)

hth

---

### Post by henk148 on 2010-02-08
Install etherwake, and from the command line issue:

# etherwake [MAC address]

e.g.

# etherwake 00:a0:ab:8c:0c:42

This works if your NIC has wake-on-lan

---

