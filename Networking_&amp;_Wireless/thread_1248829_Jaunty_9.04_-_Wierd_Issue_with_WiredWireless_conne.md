---
title: "Jaunty 9.04 - Wierd Issue with Wired/Wireless connection"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by JUNiA on 2009-08-24
Hey people,

I'm here because everything I have tried on these forums doesn't work unless I missed something.

When hooked up via Ethernet to my home network.. everything works (internet, ubuntu shares, xp shares etc)

BUT

When hooked up to home network via wireless, only internet access works and I can't connect to XP Shares...

but I had it working once when I left my ubuntu laptop in wireless mode for like a day and didn't touch it and then it worked... but now its not working again since reboot.  Any ideas? THis is REALLY annoying and has been for weeks, frankly making me go crazy.

UPDATE:  Ok.. well I have have continued messing with this .. and I think I have figured it out ..I have a newer gateway laptop.  So when I switch to wireless (manual switch already set to on position) and disconnect the ethernet cable like I was saying, I can only connect to internet but lose connectivity to my XP shares on my XP machine on the home network.  But if I disconnect the ethernet cable and turn the wireless switch off and on by physically turning it back on since its at the side of my laptop, and then perform the following commands;

sudo dhclient wlan0

then I enter this command

sudo /etc/init.d/winbind restart

then I enter this command

sudo /etc/init.d/samba restart

and voila I can connect back to my shares.. could someone tell me why when I perform these commands I can reconnect to my shares, but when I disconnect the ethernet cable and having wireless already switched on and try to access my shares I can't, and only connect to internet?

---

### Post by shanix on 2009-08-24
What's the error message that you are getting when you try to access the windows share?

---

### Post by Iowan on 2009-08-24
Wonder if wireless routing sends everything to internet (which won't find the rest of your network)...

---

