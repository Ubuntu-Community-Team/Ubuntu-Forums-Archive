---
title: "samba problems between 2 ubuntu comps"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by poikiloid on 2009-07-14
using an ethernet crossover cable, i want to get files off a jaunty32 (32bit) laptop to a jaunty64 (64 bit) laptop.

I have created manual wired static connections on each with the following settings.

jaunty32:
ip: 192.168.0.1
netmask: 255.255.255.0
ateway: 192.168.0.0

jaunty64:
ip: 192.168.0.3
netmask: 255.255.255.0
ateway: 192.168.0.0

Samba is installed, crossover cable is connected.

By right clicking for "Sharing Options" in Nautilus, I enabled sharing on the desired folder on jaunty32. On the jaunty64, using Nautilus>Go>Location, I typed smb://192.168.0.1
This allowed me to see the share name of the folder I had shared. But when i double-click it, I am asked to enter password.

So I put
Username: (the username of the jaunty32 comp that has the folder)
Domain: WORKGROUP
Password: the password for the username of the jaunty32 user account.

It doesn't work. The password disappears, leaving the login screen for me to try again.

i have tried pinging eachother, and it is 100% successful...

i have Firestarter on jaunty32. i have set it to "Stop Firewall" but it doesn't help. same problem. so i reenabled firewall, then i added samba to inbound policy allowed list, specifying "192.168.0.0/24" as the allowed ip range. still doesn't help.

let me know if and how i should post any more info.

---

### Post by poikiloid on 2009-07-14
i have now used samba server configuration on jaunty32 to "allow access to everyone" to connect to the folder. when i did this, i was able to browse the folder's contents. 

however, when i try to copy files out of it, i cannot. it says i do not have permission. but the username that i use on both accounts is the SAME.

now, i don't really like setting it to allow everyone, as this is a big security risk from internet attacks, right?

so, why is it working when set to allow everyone?, how can i get it working while still requiring password?, and how can i solve the problem with file permissions? i really hope this is possible via gui, as i know very little about terminal, config files, networking, etc.

thanks for help.

---

### Post by poikiloid on 2009-07-14
Ok, so using the Samba Server Configuration program, i went to prefences>samba users. under the username that was there, i had to update the password that was there--i dont' know where it got that one, but it was too short.

then, i added write abilities for the folder, and set it to only allow selected user(s), and chose that username.

finally, it is working...

---

### Post by poikiloid on 2009-07-15
So, it now lets me select an item, a folder, or even multiple folders, and drag to my other comp. But when I show hidden, and do a control-a, then drag, it starts "preparing" to copy indefintely. I stopped it after 3 hours, at which point the file operations dialog had counted up over 600,000 files (and counting) of over 400GB, which is astonishing, as the source hard drive is only 30 GB total (and has 8GB free space). the destination is 300GB.

The folder I have shared is my home folder, and i'm trying to copy everything in it to the other comp. If I go to properties on the home folder, it says there are only 12,174 items at 18GB. Why is this happening? I finally told it to stop. Instead, I have simply copied them to an external hard drive via usb. But I'd like to know why it wouldn't work.

---

