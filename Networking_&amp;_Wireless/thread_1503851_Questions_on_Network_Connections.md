---
title: "Questions on Network Connections"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Chaconne on 2010-06-07
Hello, all,

I have a question regarding the configuration of Network Connection. My wired connection is fine right now and when I check the network connection applet, it display active information of eth0. However, when I click the Configure button, the Network Connection window appears but there's nothing in the Wired panel. Should there be a eth0 in that panel? I remember I had one before, but after I messed with some configuration of VPN, my network became unstable and I remove the Network Manager to try to solve the problem. Since then, there's nothing in my Network Connection window, though I can still connect to my router with eth0. Now even after I reinstalled the Network Manager, I still don't get anything.

Thanks in advance for any insightful comments.

---

### Post by dineshs on 2010-06-07
Maybe NM is not managing your network.With ref to this site
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager) 
For NM to manage your devices the file /etc/network/interfaces should contain only this
```
auto lo
iface lo inet loopback
```
> Should there be a eth0 in that panel
You can add eth0 in NM (Right-click on the NM icon-two opposite arrows on top right- and then click on Edit Connections. 
Select the tab, wired then click add)

---

### Post by Iowan on 2010-06-07
Sometimes it becomes a "Yes, it works, but..." 
The connection  might be working because it's defined in */etc/network/interfaces*. You can tell NM to control that interface via */etc/NetworkManager/nm-system-settings.conf*. It'd probably be a good idea to make backups - not every edit makes things better. ;)

---

### Post by dineshs on 2010-06-08
> **Iowan said:**
> . You can tell NM to control that interface via */etc/NetworkManager/nm-system-settings.conf*.
Set ```
managed=true
``` in */etc/NetworkManager/nm-system-settings.conf*
Am I right?

---

### Post by Iowan on 2010-06-08
> **dineshs said:**
> Am I right? That's the one...
Sometimes it makes things work - sometimes not.:???:

---

### Post by Chaconne on 2010-06-09
Thank you very much dineshs and Iowan.

I modified the two file accordingly - leaving only 2 lines in */etc/network/interfaces* and Managed=true in */etc/NetworkManager/nm-system-settings.conf*. It's working now. There's a item *Wired 1* automatically appeared in the Network Connections.

---

### Post by Iowan on 2010-06-09
Give it a couple of days to make sure it STAYS fixed before you mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

### Post by Chaconne on 2010-06-09
Thank you very much Iowan and you are definitely a foreseer! Now I have the old problem with Network Manager after another boot. I uninstalled Network Manager previously because of this problem. That is the Network Manager overwrites my resolv.conf while not providing a valid nameserver. My computer is not even able to get a valid IP though DHCP is set to auto in the Network Manager. BTW, my router with a tomato firmware provides DHCP functions.

However, I unfortunately have [another more serious issue]("http://ubuntuforums.org/showthread.php?t=1505970") to worry about now.:'( So I rolled back to the old configuration(managed=false) and will debug it later.

---

