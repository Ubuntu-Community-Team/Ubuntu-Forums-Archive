---
title: "ssh &quot;Connection reset by peer&quot; problem"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by slockton on 2010-02-09
Hello,

I've been searching with no luck for this problem, which cropped up today after no changes to the system: I can successfully ssh into my ubuntu 64-bit 9.10 machine (via OS X with iTerm), but after about 30 seconds, the connection drops with the message "Connection reset by peer\nConnection to xx.xx.xx.xx closed".

If I then try to immediately ssh back in I get: "Write failed: Broken pipe". If I try to immediately ping the machine instead, I cannot ping it until the ~10th try. Eventually I can log back in again, only to be kicked off after between 5 and 60 seconds.

I called the network people and their are no known issue right now with networking. The networking on the ubuntu machine is otherwise fine, it seems.

In the /var/log/auth.log file, it simple says:
> Feb  9 14:19:20 harriet sshd[4134]: Accepted password for xxx from xx.xx.xx.xx port 55105 ssh2
Feb  9 14:19:20 harriet sshd[4134]: pam_unix(sshd:session): session opened for user xxx by (uid=0)
Feb  9 14:19:28 harriet sshd[4046]: pam_unix(sshd:session): session closed for user xxx

Which isn't of much use.


So, does anyone have any ideas? How can I further troubleshoot this annoying issue? The solution I come across to a similar problem is to add a "ClientAwakeInterval" number to sshdconfig, but this (as expected) doesn't fix my problem.

Thanks,
Steve:confused:

---

### Post by suseendran.rengabashyam on 2010-02-10
Hi,

Try to set the MTU of the network interface to 1400 in both the machines.

In Ubuntu you can do it by

```
sudo ifconfig ethX mtu 1400
```

Change suggested above will not survive a reboot. If the above works, you may like to edit your network configuration to permanently apply the new MTU setting. If you are manually configuring the network interface, you can accomplish this by adding "mtu 1400" line to /etc/network/interfaces under the right section.

For OS X you can refer this link

[http://support.apple.com/kb/HT2532](http://support.apple.com/kb/HT2532)

Let me know if this helps.

---

