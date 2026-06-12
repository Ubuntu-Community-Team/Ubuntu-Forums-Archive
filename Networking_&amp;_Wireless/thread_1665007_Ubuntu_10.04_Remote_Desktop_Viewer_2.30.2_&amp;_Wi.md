---
title: "Ubuntu 10.04 Remote Desktop Viewer 2.30.2 &amp; Windows XP TightVNC 2.02"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by GNU-Cody on 2011-01-11
Issue: Ubuntu 10.04 LTS Remote Desktop Viewer 2.30.2 will not connect to Windows XP Professional with TightVNC server 2.02 installed. Remote Desktop Viewer screen goes black then you receive "Connection Closed" error message. 

Testing: Connection was tested with several different settings on both the Ubuntu 10.04 Remote Desktop Viewer machine as well as the Windows XP pro TightVNC machine. Each test resulted in the same error. (NOTE: TightVNC connection was made without issue from another TightVNC viewer in a Windows XP environment to the Windows XP pro TightVNC server.)

Solution: None. I was only able to workaround the problem by installing TightVNC 1.3.10 on the Windows XP pro host. After this was done there were no issues connecting from either the Ubuntu or Windows environments. Since I suspect this to be a TightVNC 2.02 issue rather than an Ubuntu Remote Desktop Viewer problem I have not posted this with launchpad as a bug.

I did search this forum but was unable to find this specific problem. Still I offer my apologies if this specific issue was already addressed in another thread.

---

### Post by yorua007 on 2011-04-16
Well, I came across this problem too. And my solution is to use tsclient to connect the TightVNC2.02 server on Windows xp Pro. It works fine. So I wonder where this problem lies indeed.

---

### Post by InnerBushman on 2011-08-24
I confirm that tsclient connects without issues while Gnome Remote Desktop Viewer does not.
U10.04LTS, Gnome RDV 2.30.2, TightVNC Server 2.0.3
Let me know when reason/solution is found.

Bushman

---

