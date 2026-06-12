---
title: "ubuntu 9.04 &amp; wpn111."
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by switcha on 2009-05-14
Hi,

I am trying to set my wpn111 up. 
I have read several related forums but
I still cannot get it connected to my
my network.

I have been using this primarily as a reference
guide: 

[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

but when I get to step 10 I receive the following
msg:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netwpn11 : driver installed
device (1385 : 5F01) present

So I know its present.

I have used the iwconfig, ifconfig and lsusb commands
and they all seem to look ok.

My wireless usb adapter picks up the network ok but it just
won't connect. 
I've tried to uninstall and reinstall the driver and ndiswrapper(which is 1.53 btw).
I've tried resetting the machine and switching it on or off.
I think it might have some thing to do with this error.

If anybody can help me out - it would be appreciated.

Cheers.

---

### Post by Peter09 on 2009-05-14
There is quite a bit of this type of problem drifting around in the forums, some people have solved it by installing wicd

```
sudo apt-get install wicd
```

---

### Post by switcha on 2009-05-14
Oh.

I probably should mention that I don't have net access on the ubuntu PC. Hence, why I need the wireless adapter to work.
Is that pkg on the ubuntu disc?

Cheers :)

---

### Post by Peter09 on 2009-05-14
No ......... thinking .....thinking

xxxx Out of Cheese Error xxxxxxx

---

### Post by switcha on 2009-05-14
Lol.

...out of cheese error. Well, that's a new one to me!

;)

---

### Post by switcha on 2009-05-14
Now, the network Im trying to access is inaccessible from the network connection icon in the top right of the screen. Its there, just inaccessible.

---

### Post by Peter09 on 2009-05-14
Thoughts you can download the wicd .deb file here
[http://sourceforge.net/project/platformdownload.php?group_id=194573](http://sourceforge.net/project/platformdownload.php?group_id=194573)
then transfer it to your machine and right click to run the package manager on it

---

### Post by switcha on 2009-05-14
...it comes up with this: Error: Conflicts with the installed package 'network manager'.

---

### Post by switcha on 2009-05-14
hmm. Am thinking about reverting to a previous version 8.04 or something. But I had the same problem with that. No connection.
I am using WPA2/Personal encryption but I'm entering in the proper password.


I'm stumped!

---

### Post by Peter09 on 2009-05-14
```
sudo apt-get remove network-manager
```

---

### Post by switcha on 2009-05-14
Alrighty, did that. System cannot find some needed dependancies.

---

### Post by Peter09 on 2009-05-14
What are they?

---

### Post by switcha on 2009-05-14
I don't know. It didn't say.

I'm re-installing ubuntu 8.04 now.

Hopefully have a little more luck with that.

Though, I don't think its going to completely resolve the issue.

Would a notebook that has wireless access interfere with the netgear usb adaptor?

...hmm.

---

### Post by switcha on 2009-05-17
OK.

So I've installed 9.04.
Had ethernet connection yesterday.
Didn't have wireless.
Figured out the problem was the WPA and WPA2 security
settings b/c I could connect using open connection.

But I uninstalled network-manager and now can't put it
back on. I have all of the dependencies. 

The error I receive is as follows:

Error: Dependency is not satisfiable: libnm-glib-vpn0(>=0.7.0)

When I search using Synaptics I can't find this package anywhere and I can't find anything about it online.

I've tried to install Wicd Network Manager - double click
the icon and it does nothing.

I need to fix this up, seriously! Please!?!!

---

### Post by hobbystas on 2009-05-26
hi there!!
i'm also struggling with the same prob for a couple of months now (maybe more:() but on hardy (8.04). Found out some things, might be some help. So, i use the combination netgear wpn111 dongle and dlink di-524 router. about the dependencies error when installing wicd, i had that too. solved it as follows : did a fresh installation of 8.04.2 . Never got online. First, mount the release cd on the repository and do
code:
sudo apt-get install build-essential

after that, make .deb back up package of network manager using information on this link (just in case ;)):
[http://ubuntuforums.org/showthread.php?t=527488]("http://ubuntuforums.org/showthread.php?t=527488")
(i skipped that part). after that,

code:
sudo apt-get remove network-manager network-manager-gnome

to remove gnome's network manager (i also used the --purge but i guess that would throw your backup away, not sure about that).

in the next step install ndiswrapper and wpn111 drivers as described in the thread you mentioned. You may want to get the latest version of ndiswrapper from sourgeforce (i did, but its strange, it should be version 1.54 but the ndiswrapper -v command reports version 1.52) i also found through the netgear site, drivers version 2.1 for the dongle (check attachement)

and finally, install wicd using downloaded deb package. just double clicking on the icon should do it (it worked for me). and no more dependencies error. so i suppose wicd is expecting a wireless interface to be installed and connected. that is why u should install the drivers first and wicd after.

that is as far i am now. i use wpa personal encryption. i can see the wireless network in the networks list of wicd but the dongle refuses to connect. (at this point i'd like to mention that i used the same equipment in ubuntu 7.10 and it worked flawlessly! what is wrong since 8.04?!?!?!)

i don't know if that is much help, but i thought i share my experience. please, anybody, let us know if there is a solution!!

ps: by the way, googling around, i found this:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1422846.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1422846.html")

---

