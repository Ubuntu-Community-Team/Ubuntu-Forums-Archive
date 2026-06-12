---
title: "Uninstalled Firestarter, lost internet connection"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by laserman on 2011-03-22
:(

I uninstalled Firestarter and lost my internet connection. Icon in the panel shows it is connected to my wireless router. When I try to ping [www.google.com](www.google.com), I get ping: unknown host. 

I re-installed Firestarter and it corrected nothing.

I have found some other information pointing towards the iptables and flushing them but after performing that, it still will not pass traffic to an fro.

Without the connection, it proves difficult to provide direct information but I will work with anyone to provide as much cut and paste as I can between computers.

Thanks, laserman

---

### Post by laserman on 2011-03-23
It appears, and may already be a previously reported bug...

I was able to get connection only after typing in terminal 

sudo ufw enable

Once that was done, I had connection. When I reboot, that option does not carry and appears to have been reported as a bug...still digging.

---

### Post by laserman on 2011-03-23
I followed this thread: [Firestarter prevents internet connection]("http://ubuntuforums.org/showthread.php?t=1657704"). After booting up, I still had to enable UFW. 

I re-installed Firestarter. Clicked on the application, entered the password and followed the generic prompts for loading. Exited the firewall and checked my internet connection, it was present. 

What files are changed when I install Firestarter?

---

