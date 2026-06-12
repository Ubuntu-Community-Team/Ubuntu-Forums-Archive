---
title: "What's using my bandwidth?"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by infinitejones on 2009-11-11
For about the last three hours, the system monitor and netspeed applets in my panel have both been reporting pretty much maxed-out bandwidth going in and out of my laptop (via wlan0). I have no idea what it could be - I do have regularly scheduled backups to a remote NAS, but some quick calculations with the speed and duration rule those out, purely because they don't back up enough data to take that long at that speed.

I installed nethogs and did sudo nethogs wlan0, and this is what it tells me:

PID: 0
User: root
Program: Unknown TCP
DEV: blank

and then sent and received speeds, not constant but pretty much the fastest my wlan card will go.

It's reporting other things correctly, eg. I'm running Firefox and waiting for a youtube video to download, and it reports the PID, User, Program and Device correctly for that. 

I'm 99.9% sure it's not some kind of wireless hijack - I've got WPA2 on the router with a secure password. The router isn't reporting any unknown clients on the DHCP client table.

Does anyone have any idea what this could be, and/or does anyone know a way that I could find out?

---

### Post by dvlchd3 on 2009-11-11
```

sudo netstat -ta

```

Shows all active connections to your computer.

---

### Post by yugo4k on 2010-03-18
Ok, I have the same problem, and **netstat** didn't help at all. Does anyone know what process could that be? **ps aux** doesn't show any PID 0...

---

### Post by jrssystemsnet on 2010-03-18
Well, this is wireless, which means it's promiscuous - you're getting every single packet on the network, whether it's supposed to come to your MAC address or not.

The "PID 0" entry on nethogs basically refers to any traffic it can't tie to a specific PID, not to an actual PID 0.  You might want to try using **iftop** instead, if all your traffic is ending up on the unknown category from nethogs.

```
you@box:~$ sudo apt-get install iftop
you@box:~$ sudo iftop -i wlan0
```

Now you'll want to type **p3** (caps counts!) to enable display of source and destination ports, and sort by the third column (bandwidth usage).  This will give you an idea of where the majority of the traffic is going.  Don't see the traffic that nethogs showed you?  Then quit iftop, and this time try

```
you@box:~$ sudo iftop -p -i wlan0
```

which will start iftop in promiscuous mode, so that you also see traffic which was not targeted to your MAC address (which might be pretty significant, for a wireless environment).  Feed it the same **p3** keypresses to display port numbers and sort by bandwidth usage, and see what your top culprits are.

Report back here when you've got some more data, and we'll see if we can figure it out.

---

### Post by yugo4k on 2011-05-26
Sorry it took so long for me to see your reply... I no longer work where the problem occurred, but it seems the problem had to do with NFS (they had no wireless devices of any sort).

I heard that when some of the network pcs were rebooted, the nfs-manager or whatever kept trying to reconnect the shared partitions, thus occupying the network.

But thanks for your help! I just learned a bit more about traffic and PIDs... :D

---

### Post by novinick on 2011-05-27
it comes down to privacy leaks , which can not be stopped
(outbound connections)
only 3d party applications trys to protect from this , i think,on all os

---

### Post by Cs0hu on 2012-03-13
i detected something similar but i'm a total noob when it comes to this so i just did some observing with nethogs
with me it's definitely to do with torrents, the difference is visible immediately when running vuze or not
the theory i read that it has to do with delayed delivery because of congestion seems to make sense, when you run vuze and play around with the max number of global connections, set them to three or so a pattern becomes visible in netthogs output
maybe these torrents/connections are detected as separate processes?
like i said i'm far from an expert so pls dont burn me for my lack of technicality. I just thought i'd share what i observed and hope maybe it helps someone.
If an experienced user happens by here, i have also noticed that when my vpn is up i have about 15 to sometimes 30 percent more traffic over wlan0 than over ppp0 and no clue what this is ? Anyone could point me in the right direction there that would be greatly appreciated

---

