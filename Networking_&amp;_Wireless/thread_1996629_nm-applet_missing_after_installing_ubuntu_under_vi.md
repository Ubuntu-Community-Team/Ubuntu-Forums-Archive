---
title: "nm-applet missing after installing ubuntu under virtualboc"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by Kompost on 2012-06-04
After installing Ubuntu under VirtualBox the nm-applet is missing.

I already tried to restart the applet but nothing has happened. Any suggestions? 

```
jonas@jonas-laptop:~$ kill nm-applet 
bash: kill: nm-applet: arguments must be process or job IDs 
jonas@jonas-laptop:~$ kill 2649 
jonas@jonas-laptop:~$ sudo nm-applet 


** (nm-applet:2740): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files 
** Message: applet now removed from the notification area 

** (nm-applet:2740): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files 
** Message: using fallback from indicator to GtkStatusIcon 

(nm-applet:2740): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed 
** Message: Starting applet secret agent because GNOME Shell disappeared 

** (nm-applet:2740): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files 
```

---

### Post by Kompost on 2012-06-05
No idea anyone?

---

### Post by Kompost on 2012-06-06
So do I really need to reinstall Ubuntu in order get my nm-applet back? :(

---

### Post by danielhayes on 2012-06-06
I am having the same problem.

My system crashed (12.04 64bit Ubuntu) and after a reboot my nm-applet is missing and I can no longer get online.

any help is much appreciated.

---

### Post by danielhayes on 2012-06-06
Just noticing slight difference in the error mesage from the Original poster.

--> Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

Many Thanks

---

### Post by Kompost on 2012-06-06
Please, doesn't anybody has an idead? My computer is just worth nothing without working internet ... :(

---

### Post by Kompost on 2012-06-10
I found a solution. Edit /etc/NetworkManager/NetworkManager.conf to 

[main] plugins=ifupdown,keyfile dns=dnsmasq

[ifupdown] managed=false

---

