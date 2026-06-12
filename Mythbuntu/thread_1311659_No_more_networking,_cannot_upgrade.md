---
title: "No more networking, cannot upgrade"
date: 2009-11-02
forum: Mythbuntu
---

### Post by dibuntux on 2009-11-02
Help! Suddenly networking is dead. I had to change the IP back to localhost from a fixed IP on my subnet, just to let the frontend find the master.


XFCE desktop is not running as task, but instead 2 copy of the frontend are in execution. If I exit from the frontend (both), I'm  in an empty desktop, with no options and no Network manager icon. I can start apps, using the menu key, but cannot configure network manager.

Tried to repair it from the safe menu, but is not working. If choose to be dropped in a root & network shell, networking is ok. 

So, I cannot even upgrade to 9.10, since no net.

Any idea on how save what was a perfectly running machine just a few hours ago?

Hint: the only thing I was doing, is a backup with Simple Backup on a share in /home using ssh.

I've run out of ideas...TIA!

---

### Post by SiHa on 2009-11-02
if you 'ssh -X' into the box, you can run, from a terminal:```
sudo nm-connection-editor
```.

---

### Post by dibuntux on 2009-11-03
Thanks for your help! 
No, I can't ssh, the PC has no networking. But I can sudo nm-connection-editor from the local console.
The Auto eth0 connection is not activated, nor can I activate it or activate another one. 
It is a policy kit mess. The error I get from the local terminal is the following:
(nm-connection-editor:5675) Glib critical g_ hash table foreach: assertion hash table null
Warning nm-connection-editor polkit-action.c.211polkit-action.setaction ID polkit-action.validate id ... much stuff like that, too long to copy.
I tried to grant Network manager perm from the Authorization app to the su but no luck.

So, I just tried to do a backup using ssh on a new directory in my home directory, AND ALL this mess came along?

What can I do? TIA

---

### Post by SiHa on 2009-11-03
Note to self: No Network = No ssh. 

sorry, it was late.

Forget I mentioned it.

---

### Post by dibuntux on 2009-11-03
Found out it is a nasty bug with keyrings and policykit - cannot get out of it easily...
I manually modified /etc/network/interfaces and set auto eth0 from false to true - I regained networking, now I'm upgrading to 9.10

Hope to have a working machine again soon...

---

### Post by dibuntux on 2009-11-03
I've done the upgrade; well... the system is now 9.10, but myth is STILL 0.21 - I tried to repair broken packages, and managed to get back MCC - I also tried the procedure described in mythbuntu home page:
1) Install the Mythbuntu Repos package and select MythTV 0.22
2) Run "sudo apt-get update && sudo apt-get upgrade"
3) Start MythTV Frontend, you will be prompted to upgrade the database schema. 

but point 3 does not prompt anything, and no matter what, I'm still with 0.21

What do I have to do to upgrade to .22?
PS: I've had VDPAU mod in use...
TIA

---

