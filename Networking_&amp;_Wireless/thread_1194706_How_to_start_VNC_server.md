---
title: "How to start VNC server?"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by borophyll on 2009-06-22
Hi,

I am try to get VNC server to run on my desktop pc, so that I can view the session from my laptop.  They are both on the same local network.  I went to System > Preferences > Remote Desktop and ticked all of the options except for "Ask for your confirmation".  I then tried to log into my desktop via the laptop using the command 'vcnviewer x.x.x.x:0' where x.x.x.x is the IP address of the desktop machine.  It doesn't connect (connection refused).

Is there anything else that I have to do here?  When I list the processes on my desktop machine there doesn't seen to be any vnc servers running.  I'm using Ubuntu Jaunty on the desktop, and Ubuntu Intrepid on the laptop.

Thanks, B.

---

### Post by borophyll on 2009-06-23
bump

---

### Post by prshah on 2009-06-23
> **borophyll said:**
> tried to log into my desktop via the laptop using the command 'vcnviewer x.x.x.x:0'

Is there anything else that I have to do here?  

When I list the processes on my desktop machine there doesn't seen to be any vnc servers running.  

Ubuntu does not use vnc-server, but rather vinagre (vino-server); you can check if it running on the host machine with the following command in the terminal (Applications-Accessories-Terminal) ```
Tue Jun 23 11:00:43 ~:$ ps -e | grep vino
 9095 ?        00:00:57 vino-server
```

However, you can use vnc-viewer and others since vinagre is 100% vnc compatible.

You also may need to open up the relevant ports in the host's firewall. Usually it will be 5900+display number (0 in your example).

A quick way to check if the firewall is the problem; first, down the firewall```
sudo ufw disable
```, then try to connect; if it works, then you need to open the relevant port; in either case, as soon as possible, re-enable the firewall with ```
sudo ufw enable
```

To add the relevant port to your firewall exceptions, use the command```
sudo ufw allow 5900
```

You can check if the exception is added successfully with either of the below commands```

sudo ufw status
# or
sudo ufw status | grep 5900
```

If you still have problems, post back with details.

---

### Post by borophyll on 2009-06-23
Hi prshah,

vino-server is not running, which is probably the problem.  Is the Remote Desktop applet supposed to automatically start this, or do I have to do something else?

---

### Post by borophyll on 2009-06-23
Can anyone tell me how to start this vino-server?

---

### Post by borophyll on 2009-06-23
bump again

---

### Post by prshah on 2009-06-23
> **borophyll said:**
> 
vino-server is not running, which is probably the problem.  Is the Remote Desktop applet supposed to automatically start this, or do I have to do something else?

The "Remote Desktop" (vino-perferences) is supposed to start this up automatically if you have the option (Allow other users to view your desktop) checked.

I suggest you run vino-preferences from the terminal and then enable the option and post back any output to check for errors.

---

