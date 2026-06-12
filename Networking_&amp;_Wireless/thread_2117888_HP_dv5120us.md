---
title: "HP dv5120us"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Gene Heskett on 2013-02-19
Greetings all

HP lappy, dv5120us,8139too eth0, 2 different BMC radio's present
I was running 10.04-4 LTS, and the OEM radio is disabled, old bcm4318 didn't even work for XP when it was installed.

But some newer software, needed a newer kernel, so I dl'd 12.04-2 amd64 and tried to install it.  No network during the install, and the blocker popups made that a 4 hour process.  Rebooted, edited all the stuff to give it a static address on my home net, screwed around with it for several hours without even being able to ping the machine by ip address sitting on the next cabinet.

Give up, dl 12.10 desktop, find it now needs a dvd, burn that, and I am now sitting at the install screen where its asking for a network connection.

At this point a ctl+lt+t gets me a terminal, which I've never been able to do before, so I sudo gedit the stuff to make it work statically addressed again, and about 45 minutes later I get enough setup that I was able to to ping yahoo.com, for about 3 pings, then that radio icon up on the top right end of the bar comes alive and tears the connection down & won't restore it .  Wash, rinse, repeat about 5 times now.  That icon doesn't seem to have an identifier so I can make it go away with a sudo killall whatever.

I am getting frustrated enough to go get the latest Mint, the sw I want to run is reported to work with it also and the person who reported that it worked said the networking in the Mint install Just Worked(TM).

But before I do that, what is the name of that obnoxious piece of **** with the radio icon so I can kill it, restore my connection by hand, and continue with the install?

Thanks

Cheers, Gene

---

### Post by chili555 on 2013-02-19
That icon is part of Network Manager. If you want to remove it, which even an old skool guy like me *doesn't* recommend:```
sudo apt-get remove --purge network-manage*
```You can't effectively killall the process since it is designed to re-spawn immediately like some kind of terror movie zombie.

If you do so, then populate /etc/network/interfaces at a minimum with:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Get the system to read the changes:```
sudo ifdown eth0 && sudo ifup eth0
```Did you get an IP address?```
ifconfig
```And can you reach the interwebs?```
ping -c3 www.google.com
```It is not impossible to network with 8139too in any of the versions you mentioned.

I'd love to troubleshoot the internal Broadcom at some point.

---

### Post by Gene Heskett on 2013-02-19
Well, I did kill it, but that made the insaller upchuck and die.  So I fixed it again to where I could ping yahoo.com at 10 sec intervals for several minutes, restarted the installer, which found the network this time and proceeded to do the install.  On the reboot, it was restarted but somehow the wired stuff was labeled 'unmanaged', so I fixed the hosts file for the local stuff, made sure interfaces still had the static settings, did a sudo -i & fixed resolv.conf to give it a nameserver, and I'm off to the races.

At which point, Murphy bit me again, the target fqdn to get the new specialty kernel I need next is now down.

So until I want to use the wireless, I think its ready.  There, my pass phrase is like the first sentence of a mystery novel, so that will take some co-operation from NM.  and its never been co-operative yet, gawd I wish someone who actually speaks English would do the menu's.

I left it running a ping occasionally to the site I need, not a lot else to do till that works.

Network-Manager is a nice concept, too bad it was written by people who don't actually have a clue.  If I was say 50 years newer, I could be tempted to hack on that a bit.

Thanks for reading my rant.

Next Q, why does this thing log me out so quick?  Dumb...

---

### Post by chili555 on 2013-02-19
> Next Q, why does this thing log me out so quick?Which thing? The O/S? The forum? Or...??

Did you know you could install completely without network connectivity and sort it out later?

Glad it's working.

---

### Post by aspireone722 on 2013-02-19
Try a live cd of another distro as long as you back up your personal data and duel boot with Unetbootin or a live cd to test you should give it a shot whats the harm.

---

