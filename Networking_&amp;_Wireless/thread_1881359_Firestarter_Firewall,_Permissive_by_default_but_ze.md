---
title: "Firestarter Firewall, Permissive by default but zero connectivity"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by jozeph78 on 2011-11-15
Hey guys. I'm using Firestarter to manage my firewall. I've had to completely turn it off because I get zero connectivity when it is disabled. In the outbound policy section, I have permissive by default set, which I assume would allow any outbound connection, but it does not. 

My Iptables/UFW knowledge only so deep. I'm not sure if FireStarter is a manager of these services and there is some conflict but I can definitely post output from any of those tools if it would help you in assisting me with this. 

Thanks!

---

### Post by ajgreeny on 2011-11-15
I believe firestarter is no longer being supported or developed, so you would be better off using just ufw, or gufw if you want a GUI.

I suggest you read as much as you can on ufw/gufw, and here are two forum threads as a starter.
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)
[http://ubuntuforums.org/showthread.php?t=1229056](http://ubuntuforums.org/showthread.php?t=1229056)

You may need to purge firestarter and flush your current iptables settings  with
```
sudo iptables -F 
```
before making any further changes with gufw.

---

### Post by jozeph78 on 2011-11-22
Thanks! I recently found that firestarter is old but I didn't see gufw at first. I have removed it and will try learning more about ufw/gufw. Actually, ever since uninstalling firstarter i haven't had issues.

---

### Post by WasMeHere on 2011-11-22
Hi jozeph78,

I suggest that you have a look at the new Wiki about security in Ubuntu
[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
You will find several valuable links to deeper knowledge about security there.

Have fun finding out about Ubuntu :-)
Olle

---

