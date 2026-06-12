---
title: "netflow on 8.04"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by t1mmy on 2010-06-08
Hey guys, FYI I got netflow generation and collection working on 8.04.  The long version is [here, ]("http://gotorockgarden.blogspot.com/2010/06/netflow-on-ubuntu-804.html")the short version is:

sudo apt-get install fprobe
sudo apt-get install nfdump
sudo fprobe -p -i eth1 -fip localhost:555
sudo cp /etc/init.d/nfdump /etc/init.d/nfdump.default
sudo vi /etc/init.d/nfdump
#change this line to match your arguments
DAEMON_ARGS="-D -p 555 -4 -l /home/lincolnr/incoming/nfcap/"
sudo /etc/init.d/nfdump restart

Rock and roll!  Hope this helps someone, it took me a couple hours to get it happening with the usual detours (screwed up a shell script I was using to troubleshoot, etcetera...).

t1mmy
:guitar:

---

### Post by withjigs on 2011-07-20
your post helped a lot! thanks buddy

---

