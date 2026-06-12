---
title: "X11 over SSH works in Intrepid... not in Jaunty"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by smillerlsu on 2009-05-02
All,

I am running 3 Ubuntu boxes at home, and am trying to get my work VPN set up on the two that are runnning jaunty. I have a computer that still has intrepid SOLELY because I can only get the SSH X11 forwarding properly on that machine. 

I have PuTTY on Intrepid and 1 Jaunty. I have OpenSSH on all three. VPN connection works the same (VPNC, also Cisco on Intrepid)... but X11 forwarding only works on Intrepid (but does so with both VPN modules). I have verified this with both PuTTY and OpenSSH, and forwarding (i.e., xclock, xterm, etc.) will only succeed on the Intrepid machine.

ANY ideas, anyone? 

Thanks!

---

### Post by smillerlsu on 2009-05-04
Can anyone please offer any ideas? I am using the following command to SSH:

ssh -X [server] -l [username]

and it works in Intrepid. I have tried -Y and that doesn't help, VPN is configured the same, and neither OpenSSH nor PuTTY will forward my X apps after I setenv DISPLAY on the server. I'm at a loss here, and haven't found any other info in the forums (I have looked).

Any help would be REALLY appreciated!

Thanks!

---

### Post by xantus on 2009-06-29
*bump*

---

### Post by dmizer on 2009-06-30
Please post your /etc/ssh/sshd_config contents from the non-functional Jaunty machine. Last time I needed it, ssh -X worked fine for me in Jaunty, so I'm not too sure what the problem could be.

---

### Post by cavalier911 on 2009-06-30
[LEFT][LEFT]Same problem, discovered that sudo firefox would forward correctly. 
On a new user account all programs forwarded correctly without sudo.
[/LEFT]
 The ownership of folder .dbus and it's children in the broken account that existed prior to the upgrade was root while it was owned by the account owner and group in the new working account. 
[/LEFT]
After "sudo chown -R  account owner:account group ~/dbus" on the broken account it was fixed.

---

