---
title: "Windows 98 ask for password to print"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by Francis4344 on 2013-02-16
I have Ubuntu 12.04 networked with Win98, no problem. I can browse my home directory from windows. 

I can see the shared printer (HP3055) but I cannot install it on windows (by installing, I mean use it as a shared netword printer). 

Windows keeps asking me for a password even though on the ubuntu side, the printer is set to accept all jobs, no password, no questions asked, cash is king.

In the smb.conf, I made the printer browsable, printable, free love, you name it. Still ask for a password.

I have tried adding this solution to the smb.conf file
lanman auth = Yes
client lanman auth = Yes
client plaintext auth = Yes
client ntlmv2 auth = no
from [http://www.troubleshooters.com/linux/win9x_samba.htm]("http://www.troubleshooters.com/linux/win9x_samba.htm")


Before you ask, the printer is on the Ubuntu machine because it uses the USB port, something win98 does not support very well.


I could use a bit of help...

Thanks!

---

### Post by Francis4344 on 2013-02-16
Well, I must have forgotten to reboot windows 98 for the 14th time in a row.

Anyhow, I manage to install the printer and all.

Still does not work ( It crashes the printer spool) but now this should be mostly a window problem, not a network problem.

---

