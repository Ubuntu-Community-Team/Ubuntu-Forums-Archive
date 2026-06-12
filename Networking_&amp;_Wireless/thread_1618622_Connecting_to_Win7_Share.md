---
title: "Connecting to Win7 Share"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by gandaroth on 2010-11-10
Thank you for the help, and I apologize if there is already a post with this information.

I have just updated (via clean install) to 10.10. I have been able to in the past, have not tried while using 10.04 and Win7, been able to use 9.xx to connect to an XP share fairly easily. However, now I'm having troubles connecting to my Win7 share.

Info:
Win7 box:
Name: Gandaroth-DT
Workgroup: Balt
User: user

I select Connect to Server and select Windows Share as the share type. Then enter Gandaroth-DT as the server. I have tried many combinations of the optional boxes but nothing seems to help. If I leave them blank, I'm prompted for a user name, domain and password. I enter the user name as "user" and change the domain to Balt, and enter my password. When I click connect, it pauses for a second and brings the same prompt back up. Any ideas on how to fix this? It is very confusing and seems more difficult than it used to be. Thanks again for the help!

---

### Post by gandaroth on 2010-11-11
Sorry to bump this but,

No solutions or suggestions anyone?

Also, another question to ask, connecting to school network with security WPA2 enterprise, connection randomly drops and reconnects. Any idea why? I have a broadcomm card and am using the STA drivers. Should I try the other drives with fwcutter or ndswrapper?

---

### Post by gandaroth on 2010-11-14
For those who may also be having issues, I found that installing Samba and following the directions here:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

to mount the share permanently works well.

---

