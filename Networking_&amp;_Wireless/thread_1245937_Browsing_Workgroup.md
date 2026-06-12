---
title: "Browsing Workgroup"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by lunchboxtheman on 2009-08-21
Hey all,
    In previous versions (8.04/10) I was able to click on places->network and see all of the computers on my network.  I could then click on them and see any shares they had.  They are all windows boxes.  Nothing has changed except that I've updated to jaunty.

    Now when I go to places->network and click on 'windows network' nothing happens.  I'll get a blank window most of the time, other times it just loads and loads and never stops.

    I'm able to look at a specific share by typing smb://192.168.1.100/share/ for instance but that's not what I want.  I want to be able to *browse* all of the shares on my workgroup.

    I have samba, smbclient, and smbfs installed.  Any suggestions?

Thanks,
Lunchboxtheman

---

### Post by dmizer on 2009-08-21
Please see the 6th link in my sig.

---

### Post by lunchboxtheman on 2009-08-22
Allright, sorry it took me so long to respond.  I tried the 3rd solution in your sig.  I'm at least getting an error message now: "Unable to mount location.  Failed to retrieve share list from server"

Any ideas?


Thanks,
Lunchboxtheman

---

### Post by dmizer on 2009-08-22
> **lunchboxtheman said:**
> Allright, sorry it took me so long to respond.  I tried the 3rd solution in your sig.  I'm at least getting an error message now: "Unable to mount location.  Failed to retrieve share list from server"

Any ideas?


Thanks,
Lunchboxtheman

The "Failed to retrieve share list from server" error is almost always related to a firewall issue either on the Windows or Ubuntu side.

---

### Post by darell_m on 2009-08-22
Sorry but noob here and I cannot see link in your signature. Anyway cannot share and have with jaunty. Have done all the samba and nautilus in tutorial. Have disabled ufw and AVG on windows desktop. No luck. Can see workgroup on windows but says no permission to access. And I get the "unable to mount" error on network windows network. Most important to me is acessing share on windows computer for printer.

Thanks in advance

---

### Post by dmizer on 2009-08-22
> **darell_m said:**
> Sorry but noob here and I cannot see link in your signature. Anyway cannot share and have with jaunty. Have done all the samba and nautilus in tutorial. Have disabled ufw and AVG on windows desktop. No luck. Can see workgroup on windows but says no permission to access. And I get the "unable to mount" error on network windows network. Most important to me is acessing share on windows computer for printer.

Thanks in advance

You don't see -> 6) Fix samba browsing!!!

Here is the link: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

If all you need is printing, then try: system > administration > printing

---

### Post by darell_m on 2009-08-22
> **dmizer said:**
> You don't see -> 6) Fix samba browsing!!!

Here is the link: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

If all you need is printing, then try: system > administration > printing

**Geez Mate - IT All Worked and I am a happy camper - thanks so much  Cheers   **:lolflag:

---

### Post by lunchboxtheman on 2009-08-24
> **dmizer said:**
> The "Failed to retrieve share list from server" error is almost always related to a firewall issue either on the Windows or Ubuntu side.

Nope, firewall is off on both machines.  Like I said this used to work fine, it just broke when I updated to Jaunty.  Any other ideas?

---

### Post by dmizer on 2009-08-24
> **lunchboxtheman said:**
> Nope, firewall is off on both machines.  Like I said this used to work fine, it just broke when I updated to Jaunty.  Any other ideas?

Please post the output of:
```
sudo iptables -L
```

Have you tried all the fixes listed in the 6th link in my sig?

---

