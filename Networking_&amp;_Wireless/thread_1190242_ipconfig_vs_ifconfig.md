---
title: "ipconfig vs ifconfig"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by MissFixIt on 2009-06-17
what is the Ubuntu version of "ipconfig waitall"?

---

### Post by pytheas22 on 2009-06-17
I don't think there's an exact equivalent of ipconfig waitall in Unix, but if you want to execute a script or command before an interface comes up, you can do so by adding a pre-up line to your /etc/network/interfaces file.  By default, that file should look like:
```

auto lo
iface lo inet loopback
```

If you want to run a script before eth0 comes up, you would make the file look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth1 inet **dhcp**
pre-up /path/to/script.sh
```

Be sure that you replace 'dhcp' with 'static' if appropriate in the above example.

Ubuntu also has scripts in /etc/network/if-pre-up.d/ that could probably also be used to run commands, but I'm not positive how they work.  'man ifconfig' would probably explain it, though.

I hope this answers your question; if not, please provide a more specific explanation of what you're trying to do.

---

### Post by MissFixIt on 2009-06-18
The version of Ubuntu I have does not use the persistent-network.rules file.  It still uses /etc/iftab.  I'm assigning a  mac address to a specific device name (other than eth*).  This new name does not show up if I run the /etc/init.d/networking command or depmod -a; only when I reboot.  I'm writing a script for these actions and don't want to reboot.

---

### Post by pytheas22 on 2009-06-18
Which version of Ubuntu are you using?  It must be pretty old.  Is there a reason you're not upgraded to something more recent?

How do you have the new name assigned to the ethernet device?  Did you write a script to do this, or change some file?

---

### Post by MissFixIt on 2009-06-18
I am using Ubuntu release 6.06!  There's no particular reason, I just haven't received a license, yet to do an upgrade.  To change the name, I modified the /etc/iftab file.

---

### Post by pytheas22 on 2009-06-18
You don't need a license to upgrade Ubuntu.  It's free.  If you want, you can upgrade to a more recent release by typing "sudo apt-get dist-upgrade" (back up your important files before upgrading).

Have you rebooted since you made the change to /etc/iftab?  If so, I would think that the name change would be permanent.  If it's not, I'm not sure what's wrong, but I don't have much experience dealing with /etc/iftab.

---

### Post by MissFixIt on 2009-06-18
Thanks for pointing me to an upgrade.  I'll need to modify my script to use the persistent-network.rules file.  Ubuntu is not my cup of "tea"!:)
 
Yes, rebooting makes the name change permanent.

---

