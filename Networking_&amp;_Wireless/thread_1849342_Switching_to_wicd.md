---
title: "Switching to wicd"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by Enigmapond on 2011-09-24
Greetz!

I am having problems with the default network manager and it is crashing periodically with no apparent reason. I want to switch to using wicd as in Jaunty, I had an issue and installed it and it was great. Problem now and that when I installed it on Jaunty it uninstalled the default and worked right away. It didn't happen with Lucid and it "failed" to start or uninstall the conflict upon installation. What can I do to get rid of the default and use wicd as the network manager?

Thank you!

---

### Post by nothingspecial on 2011-09-24
You have to remove network-manager yourself.



```
sudo service network-manager stop
sudo apt-get remove network-manager
```

Then start wicd

---

### Post by Enigmapond on 2011-09-24
Thanks for that! I assume just starting it from the terminal will do it? Will it also stay started when I reboot?

---

### Post by nothingspecial on 2011-09-24
I've got to be honest, I can't really remember.

It should be started as a service.

```
sudo service wicd start
```

or ```
sudo service wicd-daemon start
```

or just ```
wicd
```

---

### Post by Enigmapond on 2011-09-24
Thank you again. Well, that worked and I actually saw it added in startup apps however, good thing I didn't purge the default as wicd was unable to see any available networks. What could be the cause of the network-manager to just die on occasion? It's never happened before and I didn't change any configs...

---

