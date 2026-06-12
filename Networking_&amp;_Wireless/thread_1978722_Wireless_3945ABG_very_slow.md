---
title: "Wireless 3945ABG very slow?"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by mac-duff on 2012-05-12
Hi there,
I have the sensation that my wifi connection is quite slow because it also doesnt matters to which network I am connected to.
I am running Ubuntu 12.04 and have a Intel Wifi Card:
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1021
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945


I was looking over the internet if there is something about a driver change, but didnt got a good result

I hope someone can assist me a bit?
Thx
Stephan

---

### Post by Sonic Reducer on 2012-05-21
hi, i'm posting here because i have the same problem. wireless used to be pretty decent, but i installed xubuntu 12.04 and now i can barely break 50kb/s on torrents TOTAL

i think the problem is the switch from ipw3945 to iwl3945, which i've never heard good things about. i cant for the life of me figure out how to install (i dont think it's in the repos anymore)

i've also had a lot of problems with encryption on 12.04. ive read some stuff about encryption being handled by hardware vs software, and how one is good and the other bad, but i dont know.

---

### Post by Bartender on 2012-05-21
Take a look at my [post]("http://ubuntuforums.org/showthread.php?t=1901351") from a few months ago.  See if that helps.

I should mention that if the workaround in that thread works, you may have a problem that only comes up with some routers.  With our old Linksys WRT54G I had to use this workaround.  We got a new Netgear router a few weeks ago.  I then removed the workaround and the wireless connectivity is fine.

---

### Post by Sonic Reducer on 2012-05-21
> **Bartender said:**
> Take a look at my [post]("http://ubuntuforums.org/showthread.php?t=1901351") from a few months ago.  See if that helps.

I should mention that if the workaround in that thread works, you may have a problem that only comes up with some routers.  With our old Linksys WRT54G I had to use this workaround.  We got a new Netgear router a few weeks ago.  I then removed the workaround and the wireless connectivity is fine.

i can do better than disabling wireless n, i can have a laptop made before it existed! lol the ipw3945 is wireless a/b/g.

im trying to find any option before i try and install ipw3945 from source.

---

### Post by mac-duff on 2012-05-26
Hi Bartender,
I tried your way and it works. Before when I copied something to my NAS I had 300KB and now 2mbit.

Thanks a lot

---

### Post by Sonic Reducer on 2012-05-27
so i tried it... even though i have a 3945abg...

```
gksu leafpad /etc/modprobe.d/options.conf
```

i didn't have an *options.conf* file already so an empty file was opened. i pasted **options iwl4965 11n_disable=1** into the first line and saved, then rebooted.

it's not as fast as it used to be, but definitely better. 

do you guys have stability issues for a couple minutes after starting? i disconnected and reconnected a couple times. wicd is also not using the static ip i set for connecting to my wifi, but when i dis/reconnect it will use them. that might be wicd's fault not the 3945's though

---

### Post by mconley3 on 2012-08-10
Just thought I would add to this.  I have a Gateway with a  PRO/Wireless 3945ABG [Golan] Network Connection.  I haven't noticed slowness per say, but the connection does "break" when I'm download large files from the internet or lan.  I noticed a problem when I upgraded to 11.04, I was hoping 12.04 would fix the problem but it didn't.  I put break in quotes because network manager still shows I'm connected, but I can't ping the router.  I have to turn off the wifi adapter with a switch and turn it back on again to get the connection to start working.  I'm using an SMC Barricade N Wireless Router.  I have tried various different things, including disabling N, with no success.  I did open a question on launchpad here.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/189625](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/189625)
Seems everyone has a slightly different problem with the driver for this Wifi card.  Maybe it depends on the router.  

Normal browsing of the internet seems to be fine, when I need to do updates, I hard wire to the network.

There is some hope.  I found the following.
[https://bugzilla.redhat.com/show_bug.cgi?id=805285](https://bugzilla.redhat.com/show_bug.cgi?id=805285)
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2359](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2359)
[https://bugzilla.novell.com/show_bug.cgi?id=768567](https://bugzilla.novell.com/show_bug.cgi?id=768567)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1009878](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1009878)

Not really sure how to tell when or if the patch from Intel will get rolled into 12.04/12.10

---

### Post by wildmanne39 on 2012-08-10
*Thread moved to **Networking & Wireless**.*

---

