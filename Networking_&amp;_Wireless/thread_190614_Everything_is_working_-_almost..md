---
title: "Everything is working - almost."
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by SZF2001 on 2006-06-06
OK, so... Beofre last night, before installing 6.06, I had the latest version of ndiswrapper up, right?

Now I've updated. I try to get back on the internet with ndis but it just won't let me. It can recodnize my card and everything...

This is what happens.

```
coleman@ColemanNetwork:~$ sudo depmod -a
coleman@ColemanNetwork:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
coleman@ColemanNetwork:~$ tail /var/log/messages
Jun  6 10:55:04 localhost gconfd (root-6044): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun  6 10:55:04 localhost gconfd (root-6044): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  6 10:55:04 localhost gconfd (root-6044): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  6 10:55:04 localhost gconfd (root-6044): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  6 10:56:04 localhost gconfd (root-6044): GConf server is not in use, shutting down.
Jun  6 10:56:05 localhost gconfd (root-6044): Exiting
Jun  6 10:57:27 localhost kernel: [4295803.157000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Jun  6 10:57:27 localhost loadndisdriver: loadndisdriver: main(638): version 1.8 doesn't match driver version 1.7
Jun  6 10:58:54 localhost kernel: [4295889.787000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Jun  6 10:58:54 localhost loadndisdriver: loadndisdriver: main(638): version 1.8 doesn't match driver version 1.7

```

So maybe there is a file somewhere or something where I can just change it to recodnize 1.7 or something? Or did a new version of ndiswrapper come with the update?

---

### Post by SZF2001 on 2006-06-06
I hate to bring this topic back up but I've just realized something.

With all the updates and stuff, is the ndis program up to date with Synaptic? Could I possibley just install it from there and it will recodnize USB cards?

---

### Post by nzruss on 2006-06-06
does this help?

[http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101](http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101)

---

### Post by bartlantz on 2006-07-11
you may have to uninstall ndiswrapper and then reinstall it.  I got the same error messages and uninstalling and reinstalling fixed it.

here's the forum that helped:
[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

remove old stuff
==================
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

reinstall
===============
sudo apt-get install build-essential linux-headers-386 linux-headers-686
[download ndiswrapper]
tar xvzf ndiswrapper-1.18.tar.gz
cd ndiswrapper-1.18
make uninstall
make
sudo make install

[cd into the directory that holds your windows wireless card drivers .inf and .sys]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

test that they work
======================
sudo modprobe ndiswrapper
dmesg

---

### Post by ubunturules on 2006-07-11
one simple command:
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by bartlantz on 2006-09-20
actually although I love apt-get, it doesn't work in this case, you must download the newest stable release of ndiswrapper at sourceforge.

I just lost my working wireless driver after an ubuntu update and had to reinstall ndiswrapper from source:
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

so to reiterate:
remove old stuff
==================
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

reinstall
===============
sudo apt-get install build-essential linux-headers-386 linux-headers-686
download source from [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)
tar xvzf ndiswrapper-1.18.tar.gz
cd ndiswrapper-1.18
make uninstall
make
sudo make install

[cd into the directory that holds your windows wireless card drivers .inf and .sys]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

test that they work
======================
sudo modprobe ndiswrapper
dmesg

---

