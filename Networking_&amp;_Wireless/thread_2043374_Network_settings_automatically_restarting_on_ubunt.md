---
title: "Network settings automatically restarting on ubuntu server 12.04"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by jefranca on 2012-08-16
Pessoal,

I have a problem about network settings on ubuntu server 12.04. In others forum there is the same problem, but I could not resolve.

This is my /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address X.X.120.139
netmask 255.255.255.192
gateway X.X.120.190
dns-nameservers X.X.120.33 X.X.120.34
```Well... when I run "/etc/init.d/networking restart" with these settings, the internet connection goes on. But after some period, my settings change to network dhcp settings.
Sometimes I think there is a dhcp daemon running. Case yes, I can't figure out.

Futhermore I have installed "ubuntu desktop" but I uninstalled Network-manager.

Does someone know what's happen and some ideia to resolve this?
thanks

---

### Post by rukiaEnix on 2012-08-16
You could change the special permissions to the interfaces file so even root won't be able to change the file. May not be the right thing but it would probably work.

Have you checked your log files?

---

### Post by jefranca on 2012-08-16
No, I didn't. You could say what log file I must see and what I must look for.

thanks

---

### Post by papibe on 2012-08-16
Hi jefranca. Welcome to the forums ):P

It sounds like the dhclient process is still running. Check it like this:
```
ps aux | grep dhclient
```
If it is there, you can stop it by running:
```
sudo killall dhclient
```
Let us know how it goes.
Regards.

---

### Post by rukiaEnix on 2012-08-16
Check for the log file /var/log/messages or /var/log/syslog

---

### Post by jefranca on 2012-08-17
Hi guys,

first I think the issue is resolved. The rukiaEnix's tip was good and I can see that dhclient3 was running. Then as papibe said I ran "sudo killall dhclient3" and OK.

Thank you for all \\:D/

---

