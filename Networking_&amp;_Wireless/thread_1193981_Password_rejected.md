---
title: "Password rejected"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by MadMax2 on 2009-06-22
When Itry to connect to wireless it tries then I get a dialogue box>

Authentification Required by wireless network
Password or encryption Keys are required to access the wireless network xxx
Wireless Security WPA & WPA2 Personal

Show password:
key s3%t67hjui*9(kljhf (example)

 then after trying unsuccessfully to connect it comes back

Showing password
889d3765h8965265

What's going on?

---

### Post by lisati on 2009-06-22
Two things come to mind:
[LIST=1]
[*]The password is case sensitive
[*]WEP and WPA don't actullay use the password you put in, but a hex passphrase
[/LIST]
This might seem obvious, but you need to make sure that you're actually entering the exact same passphrase that was used to set up encrtption on the network, and that you're choosing the correct format to enter it with. Another possibility is that there's some kind of MAC address filtering on the router that's blocking your access.

---

### Post by MadMax2 on 2009-06-22
> WEP and WPA don't actullay use the password you put in, but a hex passphrase

 Thanks I thought someone had managed to hack into my system

 I see a lot of people here have had a similar problem here:

[http://ubuntuforums.org/showthread.php?t=963379&highlight=password+rejected](http://ubuntuforums.org/showthread.php?t=963379&highlight=password+rejected)

---

