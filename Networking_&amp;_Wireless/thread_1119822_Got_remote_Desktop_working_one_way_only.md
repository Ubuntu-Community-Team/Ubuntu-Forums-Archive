---
title: "Got remote Desktop working one way only"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2009-04-08
Hi All

Well yesterday I discovered the joys of SSH and have setup a place on my eeepc and on my main PC where I can drag n drop files between the two. Much better than using samba it seems :)

Any way I got carried away and looked into the remote desktop. I had it up and running in 2 minutes flat. However I can only do it one way.

I can use my eeepc with 8.10 OS to view and manipulate my PC with 8.04 OS.
I cannot get it to go the other way though IE. Use the PC to view the eeepc.

I can use terminal to ping the eeepc from the PC no problems at all. But It wont open up in the gui. any attempt opens vinagre and I get the;

```
Connection to host "x.x.x.x:5900" was closed.
```

Both computers are on a wireless network ssh works fine samba shares worked fine to. What may I be missing here?

regards

Fenris

---

### Post by Fenris_rising on 2009-04-09
Additional info. On my eeepc in the Remote Desktop Viewer under the 'hosts nearby list the following is listed;

```
**me** remote desktop on **PC**
```

Which is correct (me and PC are sudonyms :) but are correct.

on my PC in the Remote Desktop Viewer is says;

```
exactly the same as on the eeepc
```

So this must be wrong because it means the PC is looking at itself only.
The find function only finds the PC but I can still ping the eeepc using its hostname and IP using terminal.

Any ideas guys?

regards

Fenris

---

### Post by Fenris_rising on 2009-04-09
Further to the above posts I have activated Remote Desktop on a third PC. The PC's can see each other and I can control one from the other in both directions. Again the eeepc can see them both and can be used to remote view but cannot be seen from either of the PC's.

Help ;)

Regards

Fenris

---

### Post by Fenris_rising on 2010-02-17
Hi All

Long time since I posted this but I have stumbled across the reason, at least it appears that way, why I had a one way remote desktop.

In the menu> internet> remote desktop viewer. Which is the software you use to view the remote desktop.

System> Preferences> remote desktop. This is the bit I missed. You use this to set the permissions of the machine to except, with or without password, connections from other machines.

Why some setups seem ready to work and some not though is a bit odd. But at least I know why now =D.

It's great for scaring the kids when the PC in the front room suddenly blasts music out late at night =D

regards

Fenris

---

