---
title: "RT2570 woes"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by AndyCooll on 2006-02-04
Ok, I'm another user having endless problems getting my wireless network up and running.

I have a Belkin Wireless G USB Network Adapter which apparently will work with Ralinks RT2570 drivers.

I've been following Lambert's howto here: [HOWTO: Ralink RT2570 usb wireless driver]("http://ubuntuforums.org/showthread.php?t=106846") and
KingBahamut's here: [Rt2x00drivers]("http://doc.gwos.org/index.php/Rt2x00drivers")

It says I'll get errors with modprobe, which duly happens:

```
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/andy/rt2570-1.1.0-b1/Module modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
grep: /etc/modprobe.conf: No such file or directory
append 'alias rausb0 rt2570' to /etc/modprobe.conf
```

However when I then try to move the driver file to the correct directory as suggested, there is no driver (rt2570.ko), nor a "/extra" folder either. In fact there is no rt2570.ko anywhere at all on my box?? Looking at the above code, it's as if nothing has been installed :( 

So I'm a bit stumped as to what to do next :-k

---

### Post by Lambert on 2006-02-05
So make and make install finished with no errors?

run this and see what output you get

```
sudo slocate -u
sudo slocate rt2570
```

I didn't see a new release of the driver so don't believe there are any changes (unless you pulled from cvs)

Can you post the whole output of make and make install here

Also notice the second post in the howto written by me. I don't have a device to test so I had to rely on others. jnorth had good input.

---

### Post by AndyCooll on 2006-02-06
Thanks for your reply. I'm at work at the moment, however I'll follow your instructions and post the results.

And no, I haven't used any CVS driver version, just the standard Beta one that your link points to.

:cool:

---

### Post by AndyCooll on 2006-02-06
I have some good news ... I've been able to connect to my router via my wireless usb network adapter! It really is a breakthrough! It has been the _one_ issue that until this evening I hadn't been able to resolve in my 7-8 months of using Linux. \\:D/ 

A big thank you to the guys who compiled the HOWTO's :D Essentially I followed Lambert's, and this time it all seemed to work until the last "echo" bit. Anyway I cobbled the last bit together using the links on Lamberts thread (which points to threads by reggie and jnorth). And this seemed to do the trick!

Of course ...once you get one thing working you always want something else!!!
And my problem now is that though I am successfully using wireless, my nfs shares didn't successfully mount. Almost as if on boot-up the configuration file mounts are attempted before the wireless network drivers have been loaded?

Anyone got any ideas?

---

### Post by AndyCooll on 2006-02-07
And finally my joy is complete!

Have now managed to get my mounts to load on boot-up. It seems that the problem probably occurred because I hadn't properly de-activated my ethernet connection. Even though I had gone into System->Administration->Networking and de-activated it there, and even removed the cable it was still trying to re-activate on boot-up and as a result conflicting with my wireless connection.

The resolution was to go back into /etc/network/interfaces and disable the eth0 settings there. This prevents the ethernet interface from loading on boot-up

Now boots up like a charm! \\:D/ 

:cool:

---

