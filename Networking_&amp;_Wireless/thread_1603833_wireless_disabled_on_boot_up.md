---
title: "wireless disabled on boot up"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by RediJedi on 2010-10-23
Kind of a weird intermittent problem.  When I boot up my wireless is disabled according to the network manager.  I have to disable my wireless using the switch on my laptop (dell latitude e6400), reboot, login and then enable the wireless using the switch on the laptop in order to get the wireless enabled again.  If I then reboot or shutdown, the next time I start up the wireless will be disabled unless I boot up with it disabled via the hardware switch and then enable it using the hardware switch.
I've tried editing the /var/lib/NetworkManager/NetworkManager.state, deleting it altogether but that doesn't seem to affect anything.
I'm not sure what happens to trigger this, since it originally happened a few months ago, disappeared for a few months and then started happening again a few days ago.
Anyone else experience/resolve this?

---

### Post by blazerw on 2010-11-26
I had the same problem. Many posts about fixing /var/lib/NetworkManager/NetworkManager.state did not fix it. Still, there remains no fix. However, I did find a workaround. NetworkManager installs with a command line tool that can control it. I simply created a script file that gets run when I log in that enables wifi.

Here are the details:
Create a file, /etc/profile.d/enable_wifi.sh
Put this in it:
```
nmcli nm wifi on
```

Now, I'm not 100% sure that a profile.d script is the most appropriate place to put this, but it worked.

---

