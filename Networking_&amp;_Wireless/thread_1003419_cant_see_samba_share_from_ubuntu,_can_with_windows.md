---
title: "cant see samba share from ubuntu, can with windows?"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by hardyn on 2008-12-06
i know this has been asked before but i cant seem to find a suitable solution.

i have a small file server, storing music etc.  i can be accessed just peachy from vista, but not from my other ubuntu box.

the fact that it can be accessed from windows suggests that i have done something halfway right, but what can i do so ubuntu can see the share?

3 computers:

mythbuntu 8.04, ubuntu 8.10 and vista home

804 and vista work fine
vista 8.10 work fine

810 sees neither vista nor 804

thanks in advance for any help

---

### Post by MockY on 2008-12-06
How are you trying to connect to the server? If you go via Network - Places, then you are out of luck. This has been broken in Ubuntu since Hardy.

Try Places - Connect to server... and select windows share. Enter the required information. I usually put the drive name followed by dollar sign (for example D$), just so that I will have access to the entire drive, whether it is shared or not.

If that still does not work, use nautilus and enter smb://IPNUMBER/share/

---

### Post by hardyn on 2008-12-06
cant find machine name, i did not try ip explicitly but will soon.

what exactly got broken since hardy with the network search tool for nautilus?

---

