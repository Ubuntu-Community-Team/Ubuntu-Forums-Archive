---
title: "Wireless trouble with asus-56e.  how to disable/edit iwlwifi module?"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by mbsch on 2013-03-07
> **bouchigo said:**
> I did this, but it won't stick (not permanent).

Every time I reboot I have to use these two commands, otherwise I can't connect:

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi bt_coex_active=0

There are no conflicting files in /etc/modprobe.d, I already checked that.

Any suggestions???

Thanks



Hi!  I am a completely new to Linux, I have my ASUS u56-e with the same problems - Wireless networks are appearing but the computer refuses to connect.  I've been working through the solutions in this forum and I'm stuck - here is my situation.

When I type

 sudo modprobe -r iwlwifi 

into the terminal, I get:

FATAL: Module iwlwifi is in use.

So, I tried to disable iwlwifi, and this happens:

alex@alex-U56E:~$ sudo rmmod -f iwlwifi
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'iwlwifi': Resource temporarily unavailable
Error: could not remove module iwlwifi: Resource temporarily unavailable

I tried unchecking the "Enable WiFi" options in the networking menu, but to no avail.

Any ideas for how to get this working for me?

---

### Post by mbsch on 2013-03-07
Hi! I am a completely new to Linux, I have my ASUS u56-e, with a intel wimax-6150+ wireless card with a common problem - Wireless networks are appearing but the computer refuses to connect. I've been working through the solutions in this forum and I'm stuck.  This solution is supposed to work:








sudo modprobe -r iwlwifi


sudo modprobe iwlwifi bt_coex_active=0


gksu gedit /etc/modprobe.d/iwl.conf


options iwlwifi bt_coex_active=0


and to ensure fast internet do the same:


sudo rmmod -f iwlwifi
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf


options iwlwifi 11n_disable=1




but I get stuck:


When I type


sudo modprobe -r iwlwifi 


into the terminal, I get:


FATAL: Module iwlwifi is in use.


So, I tried to disable iwlwifi, and this happens:


alex@alex-U56E:~$ sudo rmmod -f iwlwifi
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'iwlwifi': Resource temporarily unavailable
Error: could not remove module iwlwifi: Resource temporarily unavailable






I tried unchecking the "Enable WiFi" options in the networking menu, but to no avail.


Any ideas for how to get this working for me?


Thanks,
Alex

---

### Post by mörgæs on 2013-03-07
Please don't double-post.
Merged.

---

### Post by mbsch on 2013-03-08
I just stuck with the first one I tried.  Should I try a different one?  I'm using Ubuntu 11.04.

---

### Post by Bucky Ball on 2013-03-08
*Thread moved to **Networking & Wireless***

---

### Post by chili555 on 2013-03-08
> alex@alex-U56E:~$ sudo rmmod -f iwlwifi
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'iwlwifi': Resource temporarily unavailable
Error: could not remove module iwlwifi: Resource temporarily unavailable

You probably want:```
sudo modprobe -r iwlwifi
```> gksu gedit /etc/modprobe.d/iwl.conf




and to ensure fast internet do the same:


sudo rmmod -f iwlwifi
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf


options iwlwifi 11n_disable=1


I'd put it in just one file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi bt_coex_active=[COLOR="#FF0000"]N[/COLOR] 11n_disable=1

```The parameter bt_coex_active is boolean, not an integer. See *modinfo iwlwifi*.

---

