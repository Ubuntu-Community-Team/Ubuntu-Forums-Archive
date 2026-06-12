---
title: "Trying to automount Windows Shares"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by KentonS on 2009-01-02
Hello.

I'm running Ubuntu 7.10 on a laptop. I have a wireless connection to my home network which comprises a router and some PCs running various flavors of Windows. I am able to do a manual cifs mount of shares on those PCs. I'm now trying to automate the mounting of those shares using automount.

Following instructions found [here]("http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs") I installed and configured automount. When I tried the suggested command (ls -als /cifs/*<server name>*/*<share name>*), it failed, giving the message "ls: /cifs/*<server name>*/*<share name>*: No such file or directory". The following entries had been made in /sys/log/syslog:[list][*]automount[15389]: lookup(program): lookup for *<server name>* failed[*]automount[15389]: failed to mount /cifs/*<server name>*[/list]I should probably mention at this point that I have installed winbind, but I've done nothing to configure it. Nor have I been able to find anything telling me whether and how I should configure it.

What am I missing? What else should I have done?

As always, thanks in advance for any assistance anyone is able and willing to provide.

---

### Post by KentonS on 2009-09-15
Hey, thanks very much for the overwhelming response to my question. This Community Support idea really rocks! (Not!)

---

### Post by Iowan on 2009-09-15
Unfortunately, you have some really interesting problems that are above some of us.  I have never used Automount or AutoFS, so I can't really offer much advice.
Have you verified that the */cifs/<server name>* directory exists?

---

### Post by uylug on 2009-09-15
> **KentonS said:**
> Hey, thanks very much for the overwhelming response to my question. This Community Support idea really rocks! (Not!)
 
That is not the way you're gonna get help.

It seems like it is not being able to resolve the host name? Are you trying to mount the shares by using the Windows computer name? Ubuntu will be unable to resolve the address for that host.

If you're attempting to connect to the server **by host name** see if you can ping it:

```
ping yourwindowscomputer
```

---

