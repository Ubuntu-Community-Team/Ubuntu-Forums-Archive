---
title: "Dreaded Hotel, wifi, wired, DNS whatever malarky"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by CelestialMechanics on 2013-06-09
Ok, here we go again
I have 13.04 on an HP laptop, and it works brilliantly, it also connects (normally) fine to whatever I need; accept it seems when I'm stuck away from home for three weeks at a time.  Last month I was at a hotel for work and despite connecting to the wifi no browser I could lay my hands on could get past the router.  A couple of mobile hotspots I tried showed the same behaviour, but we shall put these aside for now.  I concluded it was my machine, yet upon returning home everything was fine again, and I tested at a securred cafe wifi I had never used before as a separate test.
So I concluded it was just that hotel (never had the problem before).

Now I'm on another trip, my first stop (Holiday Inn Calais) worked just fine, all seemed good.  Now however I'm at my main hotel (for three weeks), and a router that I myself used last year with ubuntu is displaying the same problem.  I have use of a work windows laptop (which is using Firefox and IE no probs) for two days until it's needed, then I'm stuck again.

This was my previous posting, it fell by the wayside as I took along time to get back to it after returing home
[http://ubuntuforums.org/showthread.php?t=2144697](http://ubuntuforums.org/showthread.php?t=2144697)
This is the same kind of thing
[http://ubuntuforums.org/showthread.php?t=1330428](http://ubuntuforums.org/showthread.php?t=1330428)

I have tried everything in hear that I understand (not certain about the resolvconf stuff, I'm a here so you know I'm more than the average user, but not that well versed in the hard detail of networking)

At this hotel I can now ping 8.8.8.8, which I couldn't at the last, but it doesn't recognise any actual web address, whether through ping or browser.
I have tried to get a look at the router settings (a wanadoo/orange livebox, possibly the worst router I've had the misfortune to encounter) but the hotel has lost their own username and password for the box!
Please help, before I have to give this machine back again!
Best
Robin

---

### Post by jdthood on 2013-06-09
It may help to edit /etc/NetworkManager/NetworkManager.conf and comment out "dns=dnsmasq" and then to restart network-manager or reboot.

---

### Post by CelestialMechanics on 2013-06-10
Just tried that but no change. Hotel have also provided a HomePlug and I've tried an ethernet directly into the router, niether of those wired options work. Am I right in understanding 8.8.8.8 is some external address relating to Google? I can still ping that, but nothing else external. Would this suggest that the problem largely lies with the router? If so (given that windows and Android can both get through) is there anything I can do to my set-up to get around it? Best Robin

---

### Post by CelestialMechanics on 2013-06-11
Ok I'm now typing, on the same pc that failed, but by running puppy linux from a CD.  This is increasingly bizarre, this pc works at home and on many networks normally, but is intractable on others, and now running successfully via another linux flavour.  Can anyone provide insight?
I am at a loss, and I with more work trips coming up I may just have to abandon Ubuntu.

---

### Post by chili555 on 2013-06-11
See post #7 here: [http://ubuntuforums.org/showthread.php?t=2153364](http://ubuntuforums.org/showthread.php?t=2153364)

---

### Post by jdthood on 2013-06-11
What is the output of

ls -l /etc/resolv.conf
cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
nm-tool | grep -i dns

---

### Post by CelestialMechanics on 2013-06-26
Sorry for not coming back sooner, having to jump between Puppy to be online and ubuntu to try things gets a little wearing!  I will try those things and post shortly.
A further development is that a friend of mine has a LiveUSB stick with Ubuntu 12.10 on and this self same laptop can acces at least one of the networks (the only one to hand at the time) that 13.04 can't. So, it would seem 13.04 has somekind of bug, I did upgrade a couple of weeks early, perhaps I have been left with some Beta issue that has not updated.
Best
Robin

---

### Post by CelestialMechanics on 2013-07-02
Thank you guys for the direction, the sudo dhclient -r thing in Chilli's link gave me a resolv.conf that actually looked like what some of the threads had talked about. I had assumed the differences I had seen (not sure what they were in hindsight, but I know there were some) had been due to the threads being about old versions.
ANYWAY, I found I could edit resolv.conf, adding in the gateway of the hotel and worksite gateways to get web up and running.
However the system is not doing this automatically, I have to go and comment out the hotel gateway at work to stop it blocking the work gateway.  Am I perhaps missing some setting that is stopping resolv.conf updating?
Said file looks like this:
domain home
search home
nameserver 192.168.1.1
nameserver 10.0.1.1
Best
Robin

---

### Post by jdthood on 2013-07-02
It appears that /etc/resolv.conf is no longer a symbolic link to ../run/resolvconf/resolv.conf on your machine. It is fine to remove the symbolic link so that you can experiment with different values in a static /etc/resolv.conf but afterwards you should restore the symlink. A quick way to do it is to run "sudo dpkg-reconfigure resolvconf" in a terminal window.

After that you need to configure resolvconf and NetworkManager correctly.

First make sure that in /etc/NetworkManager/NetworkManager.conf the line "dns=dnsmasq" is commented out (has a '#' at the beginning of the line) and that you have restarted network-manager since you commented out that line. The NetworkManager-controlled forwarding nameserver is known not to work well in some circumstances.  [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842)

Second, see if resolving now works everywhere.  If it fails to work somewhere then, while it is malfunctioning, run the following commands in a terminal window and post the log here.

ls -l /etc/resolv.conf
cat /etc/resolv.conf
ls -l /etc/resolvconf/resolv.conf.d
for F in /etc/resolvconf/resolv.conf.d/* ; do echo "=== $F ===" ; cat $F ; done
ls -l /run/resolvconf
ls -l /run/resolvconf/interface
for F in /run/resolvconf/interface/* ; do echo "=== $F ===" ; cat $F ; done
cat /etc/NetworkManager/NetworkManager.conf
nm-tool
dig [www.google.com](www.google.com)
dig @8.8.8.8 [www.google.com](www.google.com)

---

### Post by CelestialMechanics on 2013-07-03
That appears to have worked properly! Thank you so much.
I had not done anything to remove the dynamic link (I didn't know it even existed before now)  Could it be because I had upgraded a week early to 13.04 Beta, and I got left with some developmental settings, even after teh version itself moved on?
Best
Robin

---

### Post by jdthood on 2013-07-03
There's a bug report covering the phenomenon of the disappearing /etc/resolv.conf symbolic link: [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)

Over time the malfunction has been traced back to various distinct causes as summarized most recently here: [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121)

---

### Post by jdthood on 2013-07-03
There's a bug report covering the phenomenon of the disappearing /etc/resolv.conf symbolic link: [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)

Over time the malfunction has been traced back to various distinct causes as summarized most recently here: [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121)

---

