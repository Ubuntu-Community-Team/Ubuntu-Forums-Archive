---
title: "openvpn using network manager"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Swiftjay on 2011-04-28
I've seen this issue and it never seems to get resolved maybe this time I can find a fix.

I'm currently using ubuntu 11.04 although i've had this issue since 10.04 and 10.10

When using openvpn in windows it works perfectly fine but when using openvpn on ubuntu that's a completely different story I import my .ovpn file from clearos it loads the keys just fine but when it tries to connect it say's "no valid vpn secrets"   

On clearos it gives you 3 certs and a .ovpn file the file sets it to use password with tls certs but it still comes up with this error, i've been quite stumped and it would be nice to possibly shed some light on this so I can finally get ubuntu to work with openvpn if possible.  If anyone is willing to advise where i'm going wrong that has dealt with cleros certs before much would be appreciated, thanks.

---

### Post by johnny_walker on 2011-04-29
I am also experiencing this issue in Ubuntu 11.04 while using WiTopia. If anyone finds a solution, let me know!

---

### Post by johnny_walker on 2011-04-29
So I found this thread [http://ubuntuforums.org/showthread.php?t=991144&page=2](http://ubuntuforums.org/showthread.php?t=991144&page=2) and found that all you should need to do is
```
sudo r[FONT=Courier New]estart network-manager[/FONT]
```After I installed openvpn and network-manager-openvpn, I did not do a full restart of network-manager, I had only disabled networking through the GUI interface. After restarting network-manager via terminal, I stopped receiving the "VPN secrets" error. If that does not work for you, the other posters in the thread suggested a hard reboot.

---

### Post by Swiftjay on 2011-04-29
...holy crap just like that? I've had problems with this for ages, I guess 11.04 is quite easy to resolve then.  Thank you so much for this I really appreciate this just gives me more of a reason to use ubuntu now hahahaha.

I'm gonna put this in our client docs cause this is extremely useful closing thread.

---

