---
title: "Installed dhcp3-server but doesn't seem to exist"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2011-10-18
Hi,

I had originally installed isc-dbcp-server but would like to use dhcp3-server.

So I installed it using Synaptic.  Incidentally I could not uninstall isc-dbcp-server b/c it seems to be required for dhcp3-server.

However, even though Synaptic says it's installed it doesn't appear to be.  

Maybe I just don't understand (it wouldn't be the first time) but "locate dhcp3-server" only found files in /usr/share/doc, /var/cache/apt/archives and /var/lib/dpkg/info.

Also, /etc/init.d/dhcp3-server start returns:  /etc/init.d/dhcp3-server: No such file or directory.

So what's going on?  Do I have a bad install?  What do I do next?

Thanks

---

### Post by jonobr on 2011-10-18
Not sure

But try 

```
sudo apt-get --purge remove dhcp3-server 
```

Trying reinstalling again and see what happens,

Maybe you have some residue?

Again,just a guess

---

### Post by collisionystm on 2011-10-18
try 

sudo find / -name *dhcp3*

---

### Post by jonobr on 2011-10-18
Looking at this [http://ubuntuforums.org/showthread.php?t=1863522](http://ubuntuforums.org/showthread.php?t=1863522) seems you dont want to stop the service, 
so I would recommend against doing a purge if thats the case

---

### Post by papibe on 2011-10-18
Hey AlexBooton, I continued helping you in your other thread. Please read my answer there ([http://ubuntuforums.org/showthread.php?p=11363462#post11363462]("http://ubuntuforums.org/showthread.php?p=11363462#post11363462"))

Regards.

---

### Post by jonobr on 2011-10-18
We are going into a never ending loop here, these things never end up pretty :-)

---

### Post by AlexBooton on 2011-10-19
Thank you guys for all your help.

AB

---

