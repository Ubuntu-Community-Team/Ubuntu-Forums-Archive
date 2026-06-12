---
title: "Disabling network-manager-gnome"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by Bhaskar_A on 2010-05-19
Hi,
I am trying to script to configure Ubuntu 8/9/10 and like many others I have run into issue with network-manager and network-manager-gnome.
 
I am trying to write to /etc/network/interfaces and get wysiwyg behavior.
 
One peculiar issue amongst others I see is it doesn't seem to obey the documented feature of
```
 
unmanaged-devices=mac:<mac1>;mac:<mac2>;

```
for multiple nics.
 
Question:
 
I want to disable (NOT uninstall) network-manager and network-manager-gnome from starting. 
 
I found one related post which says I can disable network-manager by
```
 
/usr/sbin/update-rc.d -f network-manager remove

```
 
How to do similar thing on network-manager-gnome.
 
I don't own the host and so can't remove packages. I only want to disable the two packages (from startup).
 
Thanks in advance.
 
Regards,
-BhA

---

### Post by wojox on 2010-05-19
You can try:

```
sudo apt-get install rcconf
```

Which is the front end for update-rc.d. It configures what services get started at boot.

---

