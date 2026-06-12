---
title: "Changing DNS server on Ubuntu"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by nightlock on 2010-11-03
I recently changed my OS to Ubuntu, running before on windows 7 before (dumb I know). On windows 7, I knew how to edit the DNS server settings for one of the networks I use frequently, and could therefore bypass its pesky firewall. In windows I would go into the IPv4 settings (under change adapter settings in control panel) and change the DNS server from the default (which the computer obtained on its own) 10.0.0.4, to 10.0.0.3, thus enabling me to bypass the firewall. How can I do this on Linux?

---

### Post by SeijiSensei on 2010-11-03
Your default nameserver is the first one listed in /etc/resolv.conf.  By default, the DHCP client will rewrite this file each time it queries the server.  However you can fiddle with the settings in /etc/dhcp3/dhclient.conf to tell it to ignore the DHCP server's DNS information or, indeed, not rewrite resolv.conf at all.

You'll need to edit resolv.conf as root using sudo.

---

### Post by chili555 on 2010-11-03
Please do:```
sudo gedit /etc/resolv.conf
```Change the line(s) nameserver 10.whatever to nameserver 10.new. Substitute your settings, of course.

You can make it unchangeable with:```
sudo chmod -w /etc/resolv.conf
```That means, approximately, change the mode, or permissions, to remove 'writable.' 

Of course, you can simply change it back and forth by editting the file as needed; if it's writable!

Be careful when you're not behind the firewall. Don't start a fire!

---

### Post by nightlock on 2010-11-04
Thanks Chili555, your method worked. As for the other one, I didn't find what I was looking for, that's the only real way I know how to explain it.

---

### Post by SamHiatt on 2011-03-01
Thanks to both Chili and Sensei for your answers.  Just what I needed.  :)

---

### Post by dmizer on 2011-03-01
Instead of editing conf files, you can use the default network-manager to set your DNS servers.

Just edit your connection, click on the IPv4 tab and change the "method" to "Automatic (DHCP) addresses only". Then you can manually fill in your DNS servers.

---

### Post by Givzadamn on 2011-04-12
> **dmizer said:**
> Instead of editing conf files, you can use the default network-manager to set your DNS servers.

Just edit your connection, click on the IPv4 tab and change the "method" to "Automatic (DHCP) addresses only". Then you can manually fill in your DNS servers.

Thankyou. 

Just what I was looking for.

---

