---
title: "Win XP won't connect to my Samba"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Superdude_123 on 2009-03-22
I managed to setup my samba server, and with my mac, I can connect. The problem I am having is, my windows xp system isn't connecting. I've turned off the firewall, and still nothing.

What should I try to do?

---

### Post by Iowan on 2009-03-23
Can XP see the server? Dunno if Winbind and nsswitch.conf edit might be a solution... but this'll serve as a bump anyway.

---

### Post by Benkrishman on 2009-03-23
I've been having a similar problem today.  I've been running 8.10 for a few months on my media server desktop and have been accessing it's shares on a windows xp desktop just fine.  However today everything stopped working.  I believe it has to due with recent updates installed(everything broke after I restarted for updates to take effect, I believe there was a kernel update as well in there) and since that point I've been unable to access the shares from my windows box, but could access them fine from other computers running ubuntu.

It was very strange, as I have 3 different folders shared, and had each one mapped as a drive on my xp desktop, however when things started acting weird 2 of the shares would work, and then none.  I've tried messing with the settings in the samba gui, and removing the shares and setting them up again but now the ubuntu desktop isn't showing up in my network places at all like it was earlier(at which point I'd get a permission denied error when I tried to access it).

I tried booting up into the previous kernel but that didn't seem to solve any problems.  

Any help would be greatly appreciated.

---

### Post by Benkrishman on 2009-03-23
Somehow I was able to get everything working again.  I gave my pc a static ip(removed network-manager) and then set up my shares again.  Got on my xp cd and went to Start > Run... and ran \\192.168.0.00 (with the static ip of my ubuntu desktop in place of zeros) and was prompted for a username and password, I used the ones I setup for the windows username in the samba config, and it showed the shared folders.  After that I mapped each to a drive letter and now it's back to working perfectly.  I don't know what the problem was initially but I'm just glad I got it working again.

---

