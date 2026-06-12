---
title: "SSH Connection Timed Out (Random WLAN and ETH)"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by rearviewmirror on 2009-11-21
I'm running Ubuntu 9.10, over my LAN connection (WLAN or ETH) I can only connect to my box via SSH randomly.  Sometimes it'll connect, and sometimes it won't.  It seems at the times when I can't connect it won't allow any no matter how many times I try.  If I reboot I can connect again, or if I wait for a while I can connect again.  Restarting the sshd does nothing, I turned off the firewall in FireStarter.  

Again, my attempts are LAN only (WLAN or ETH) so there shouldn't be any issues with blocking or firewalls.  Why would it not allow me to connect via SSH any and every time?

---

### Post by rearviewmirror on 2009-11-21
If I leave a continuous ping running the SSH session never times out and I can also start new SSH sessions.  If I let the session time out (idle), I cannot resume it or launch new sessions for quite some time.  The period of time in which is not known, it appears to be random.  Restarting the SSHD doesn't help, rebooting the box does allow new SSH connections.  I can't figure out why it's failing to respond (timing out) like this.

---

### Post by Lars Noodén on 2009-11-22
As a temporary work-around try looking at setting **ServerAliveInterval** and **ServerAliveCountMax** in [ssh_config](http://manpages.ubuntu.com/manpages/karmic/en/man5/ssh_config.5.html).  

You can make it automatic when connecting to that particular server by using the Host directive in ssh_config to make the settings apply only to that host.  

Or setting **ClientAliveInterval** and **ClientAliveCountMax** in [sshd_config](http://manpages.ubuntu.com/manpages/karmic/en/man5/sshd_config.5.html) on the server.



As far as diagnosis goes, if you can replicate the problem every time, try running sshd at debug1, debug2 or debug3 to get more info than you need, but maybe a clue as to what's shutting you out.

For what it's worth, what are the options you are using on the ssh client to connect to the server?

---

