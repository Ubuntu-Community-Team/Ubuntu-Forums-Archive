---
title: "USB printer shared in Samba, visible on WinXP but cannot be connected to"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by teel on 2012-06-12
Hi,
I've shared a USB cups-supported printer (Brother HL-2030) via Samba on Ubuntu 12.04 LTS, the printer is visible in Windows XP network neighbourhood but when I try to connect to it (followed by driver choose dialog at Windows computer) I get the Windows notice that either the name is incorrectly given or the printer is unavailable.

I'm pretty sure this isn't Windows XP issue, nor the firewall settings as I successfully run file sharing at this setup.
The printer name is simply "hl2030" so no special characters are present. I  set the read only = false in smb.conf, still no luck.

I've read a couple of articles on how to setup samba printer share, they are no different to what I do.
Anyone can help?

---

### Post by ratcheer on 2012-06-12
Just a guess, it is probably a firewall problem on the Linux side. To test, stop the firewall service (probably ufw). If you can then connect from Windows, fix the firewall issue, don't just leave it off.

Tim

---

### Post by teel on 2012-06-12
> **ratcheer said:**
> Just a guess, it is probably a firewall problem on the Linux side. To test, stop the firewall service (probably ufw). If you can then connect from Windows, fix the firewall issue, don't just leave it off.

Tim

Thanks, I tried disabling firewall on Ubuntu, still no luck :(

---

### Post by Morbius1 on 2012-06-12
It be a bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

Don't connect to the printer through Samba. Go to CUPS directly: [http://ubuntuforums.org/showpost.php?p=11915502&postcount=18](http://ubuntuforums.org/showpost.php?p=11915502&postcount=18)

---

### Post by teel on 2012-06-12
> **Morbius1 said:**
> It be a bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

Don't connect to the printer through Samba. Go to CUPS directly: [http://ubuntuforums.org/showpost.php?p=11915502&postcount=18](http://ubuntuforums.org/showpost.php?p=11915502&postcount=18)

Thank you, this is exactly the issue I'm facing.

---

