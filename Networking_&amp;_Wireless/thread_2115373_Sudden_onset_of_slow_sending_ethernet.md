---
title: "Sudden onset of slow sending ethernet"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by sharkswlasers on 2013-02-12
I'm sorry to trouble this forum, but I'm at wits end. Before this weekend, my ethernet connection on my lenovo y580 ideapad was working just fine with my school's network. I took the computer home for the weekend to work, and now the ethernet connection is slow at best and appears to time out often. (loading pages like reddit causes all sorts of trouble.) It appears that the data is being received just fine, but that the computer waits to send the data, as determined by trying to open webpages while watching system monitor (it will sit at 0b/s sent for ~15sec before finally sending the data so that the new page comes up). maybe most critically i can't ssh into the servers i need access to.

It's not a hardware issue, the computer is dual boot and the windows 8 wired connection is just fine. The wireless card also works just fine, and yes, I'm aware that this laptop uses the Atheros AR8161 which needs the alx driver for the wired connection to work. I installed this a long time ago and it was working just fine.

I've had a similar problem once before with a different laptop on the school's network and at that point in time i called the IT department and complained, and they gave me a static IP. Now that I'm experiencing the same symptoms as before with a new system, I'm really curious if there is a checklist of networking files i should go over before bothering them again. (no guarantee it's the same problem this time, but i'd rather keep the computer on dhcp than static.)

I've been through resolv.conf (or really, /etc/dhcp/dhclient.conf) and it isn't a DNS issue, like i said, the ethernet works, just painfully slowly. Are there other files that could have somehow been changed by connecting to my comcast signal via wifi this weekend? What should i be looking for?

many thanks

---

