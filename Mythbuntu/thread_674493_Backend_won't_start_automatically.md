---
title: "Backend won't start automatically"
date: 2008-01-21
forum: Mythbuntu
---

### Post by not4us on 2008-01-21
After going back and forth between Mythtv, MCE, VMC, GBPVR, Sage and Media Portal I'm glad I'm back to Mythtv.

Yesterday I finished setting up my backend/frontend box using Mythbuntu 7.10 and it's all good except that for some extrange reason the backend won't start automatically at boot and I have to start it manually through "/etc/init.d/myth-backend start".
Could it have been flagged not to autostart when I updated the box through the AutoUpdater??
How can I get it to autostart at boot again?

I'll come back with some other questions and issues at a later time...

---

### Post by Mrbbad on 2008-01-21
I'm sure someone will come along and give you better advise than this, but I think for now a quick and dirty fix would be to:
[B]
sudo nano /etc/rc.local[/B]

and put
[B]
/etc/init.d/mythtv-backend restart[/B]

in there -- yes, restart will start it too -- or should, anyways.

make sure

**exit 0**

is at the end of the file.  Reboot your system and see if it works after that.

Again, we're talking amazingly quick and dirty fix, I'm sure there is an official proper and better way to do this, but if that works for you for now... hey why not.

---

### Post by not4us on 2008-01-21
Thanks for taht.

I know about the rc.local (I have a command n there to stop the screensaver for coming on while on Myth) and will give that a try tonight when I get home.

However, as you said, there has to be a "proper" way to do this since the backned's got a startup script in init.d...

---

### Post by not4us on 2008-01-22
FIXED IT!

After looking at the ogs, I realized that mythtv-backend was starting but couldn't connect to mtsql (this is using a 192.168.x.x IP address that my DHCP server has reserved for my backend).
After changing the bind address in /etc/mysql/my.cnf to that 192.168.x.x I thought it was fixed but mythtv-backend kept giving an error about not connecting to mysql on boot.

It was then that I remembered that Gutsy introduced the "Roaming" option for the network and after going to Network Manager and disabling the Roaming for my NIC and enabling DHCP everything is now working!

Hope this helps somebody else too :)

---

