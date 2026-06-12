---
title: "can't change wireless password"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by MadMax2 on 2010-04-23
I've got a permissions problem: whenever I try to set the wpa key wireless password in  network manager it reverts to the original.
 I Checked users > groups and found I didn't have the authority to connect to the internet.
 I changed that but still I haven't got control.
Can you point me in the right direction.
Version is Jaunty
Thanks

---

### Post by rosanbio on 2010-04-23
deleting and recreating the network will solve most of the issues.

---

### Post by MadMax2 on 2010-04-23
> **rosanbio said:**
> deleting and recreating the network will solve most of the issues.

I've tried that. I also tried deleting default keyring in gnome2 (I'm tempted to delete login keyring as am getting mad(der). The original WEP key can't be deleted.

---

### Post by jaco223 on 2010-04-24
> **MadMax2 said:**
> I've tried that. I also tried deleting default keyring in gnome2 (I'm tempted to delete login keyring as am getting mad(der). The original WEP key can't be deleted.

Did you change the wep/wpa password in your router setup?
You need a hardwire connection to login to your router admin
through a browser usually 192.168.1.1 and set the wep/wpa key
there.

Don't know if this helps or not.

Jaco

---

### Post by MadMax2 on 2010-04-24
Yes I have changed the password in the router.
Do you know how I check who I am as in am I who I think I am (admin)and can change a password?

---

### Post by MadMax2 on 2010-04-24
I changed the router to broadcast SSID and was able to connect. The password shown is not the same as that in the router. :confused:

Could be that the long key I'm seeing is what WPA encryption(?) does?..So nothing wrong there. Why does it only connect to a *visible* SSID?

---

### Post by MadMax2 on 2010-04-24
One problem (perhaps) is that I have a router that is made in China and doesn't have such robust explanation as (say) a D-Link.

---

