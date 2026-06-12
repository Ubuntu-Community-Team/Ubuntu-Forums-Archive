---
title: "no internet access after security cleanup"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by nonkreon on 2011-05-17
hi guys;
 i installed many security programs as a switching from windows guy and decided to get rid of them last night. I uninstalled
gufw, clamav(and all based packages), firestarter
using synaptic
[LIST]
[*]before i rebooted the system the internet was well and working. but after i rebooted i had no internet access;
[*]firefox couldn't retrieve, update manager and apt-get couldn't connect.
[*]the computer knows it's connected to the router i see the connection established sign but I can't even connect to the router by typing "192.168.2.1".
[*]the computer can ping itself(127.0.0.1) but can't ping itself in the network (the dhcp address is 192.168.2.3) and replies "operation denied" or something like that.
[*]I rebooted using live-cd and connected with no problems; the my internet connection is fine
[/LIST]any thoughts will be appreciated :)
P.S.: I did a fast check on the forums and couldn't find anything related; i didn't check thoroughly though.

---

### Post by mikewhatever on 2011-05-17
You must have removed some essential networking packages in the process. If you have a 10.10 installation CD, put it into the cdrom tray, then from a terminal window run the following:
```
sudo apt-cdrom add

sudo apt-get update

sudo apt-get install ubuntu-desktop
```

If everything works as expected, that will reinstall the default set of packages and restore the networking functionality.

---

### Post by nonkreon on 2011-05-17
thanks I will try this when I get home tonight :)

---

### Post by nonkreon on 2011-05-17
nope it said ubuntu-desktop is already installed and did nothing :(
then i removed ubuntu-desktop then installed it again and still no internet :(
wait when i "apt-cdrom add" it gives me an error like this;
"skipping nonexisting file .../dists/maverick/restricted/binary-amd64/packages
when i navigate there i find packages.gz; no free packages folder though :(

---

### Post by nonkreon on 2011-05-17
while googling "ping: sendmsg: operation not permitted" i came across something with route -n and iptables. instead of trying to modify the entries moving back and forth to the other computer, i decided to remove iptables and install it offline using the cd.
i removed but couldn't install it.
i guess this brings me to a fresh install.
no possible solution was found to this issue.
i give my regards to forum moderation to do what's necessary with this thread.

---

