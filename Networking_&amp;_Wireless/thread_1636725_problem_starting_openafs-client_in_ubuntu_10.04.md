---
title: "problem starting openafs-client in ubuntu 10.04"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by ilangobi on 2010-12-03
Hi guys,

I'm having problems running openafs-client on my  desktop. I installed it using "sudo apt-get install openafs-client", and  when I try "sudo service openafs-client start" it just shows:

Starting AFS services:.

and  waits indefinitely. The strange thing is, I was able to install and run  openafs-client following exactly the same steps above on my macbook  with exactly the same ubuntu version (64-bit 10.04), same linux kernel  (2.6.32-25-generic). 

It doesn't seem to be a connection problem  either: I used the same wired connection for either one, and when I  unplug it from the macbook and try to run openafs-client, it gives an  error message of "No existing IP interfaces...". When I unplug from the  desktop system, there's no such error message, it only shows the same  "Starting AFS services:.". And when using my macbook I can get full  AFS functionality with my college server.

Also, I have tried  installing openafs-client in other ways that involved building some  modules, such as ([http://ubuntuforums.org/showthread.php?t=1279096](http://ubuntuforums.org/showthread.php?t=1279096)) and  ([http://bobcares.com/blog/?p=501](http://bobcares.com/blog/?p=501))   Before each new attempt I would  completely remove any traces of open-afs using complete removal in  synaptic and manual deletion of openafs files in the terminal.

Finally, 
sudo service openafs-client force-start ("Starting AFS services:.")
sudo service openafs-client force-reload ("Stopping AFS services:afsd: Shutting down all afs processes and afs state")
sudo service openafs-client stop ("Stopping AFS services:afsd: Shutting down all afs processes and afs state")

all  stall at the given message shown in brackets. The inability to stop  openafs has also caused my ubuntu to be unable to restart or shutdown,  stalling at that message. 

Is there any way for me to see a more detailed  log of errors when I try to startup openafs-client? Any help is appreciated. Thanks!

-Edmund

---

