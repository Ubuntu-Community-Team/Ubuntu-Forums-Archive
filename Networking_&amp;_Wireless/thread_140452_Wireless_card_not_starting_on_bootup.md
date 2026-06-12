---
title: "Wireless card not starting on bootup"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by racsw on 2006-03-06
Hi,
  I am successfully using a Netgear WG511T on Ubuntu 5.10 BB version on a Dell Inspiron laptop, and I am using it now to write this.
  Problem is, if I reboot, or shut the PC off, it won't come up unless I do one thing.
  If I go to System/Administartion/Networking, I will see the GUI listing all my interfaces.  I will also see that the ath0 interface is up and running, but I know it isn't.
  If I select "Deactivate" ath0, then select "Activate" ath0, it will start and run.  If I don't do this, it won't.
When I do it manually, obviously it's starting a networking script that wasn't started at all, or started improperly on bootup.

What is the command that this GUI is executing manually that it isn't executing on bootup?

Can someone help me fix this?

Otherwise, when it's running, it works beautifully. 

Regards,
Robert

---

### Post by lazychris2000 on 2006-04-26
I'm having the same problem as you.  I was running breezy and it did it and it still does it now that im using dapper.  I wrote this little script that i run before i start X:
```
#!/bin/sh
sudo iwconfig ath0 essid xxxxxx;
sudo iwconfig ath0 ap xx:xx:xx:xx:xx:xx;
sudo iwconfig ath0 key xxxxxxxxxxxxxxxxxxxxxxxxxx;
sudo dhclient ath0
```
of course, you wanna replace the x's with your info.
I havent found out how to start this script on bootup, but if you know how, please let me know.

---

