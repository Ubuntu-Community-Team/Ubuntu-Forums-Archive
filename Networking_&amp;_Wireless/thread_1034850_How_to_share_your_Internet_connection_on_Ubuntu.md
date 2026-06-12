---
title: "How to share your Internet connection on Ubuntu"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-01-09
One problem with Network Manager at present, is not being able to share your internet connection, as eth0 (or eth1, etc) can't be used _at the same time_ as your actual connection.  :(

There is an article [How to share your Internet connection on Ubuntu]("http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/")

Has anyone tried this method ??

Oygle

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by ajmorris on 2009-01-10
hi there,
that guide is actually for sharing your internet between more than one machine, i.e. Internet Connection Sharing.

There are methods in ubuntu to do what you want, (and NetworkManager *should* be able to handle it... it used to be able to) however, since it can't on your machine, theoretically, you should also be able to keep using NetworkManager for one interface, say wireless, then manually up your ethernet with ```
sudo ifconfig eth0 up
```

If this doesn't work, don't dispair, this is deffinitely possible to do, just a matter of going about it the right way (at this stage not sure what gnome tools will do it, im doing what you want on my PC, but purely through CLI -- i also know that the default NetworkManager in KDE4 handles this extremely well...)

AJ

---

### Post by oygle on 2009-01-11
> **ajmorris said:**
> that guide is actually for sharing your internet between more than one machine, i.e. Internet Connection Sharing.


That's what I need to be able to do though, just that I can't even use eth0 at present, at the same time as ppp0, and I thought that guide was a 'how to' to have them both running concurrently :confused:

> **ajmorris said:**
> 
There are methods in ubuntu to do what you want, (and NetworkManager *should* be able to handle it... it used to be able to) however, since it can't on your machine, theoretically, you should also be able to keep using NetworkManager for one interface, say wireless, then manually up your ethernet with ```
sudo ifconfig eth0 up
```

Okay thanks, will try that. The 'wireless' I have isn't stricly wireless, but a USB dongle, which Ubuntu calls ppp0 as it is a 'dailup' connection. It's using the Optus network, and I would love to be able to use the same connection for other computers, hence the need for eth0.

But, I will try what you have described. (As long as I do a full backup prior to all this, and somehow make incrementals whenever anything at all is changed. This is because I have seen so many posts where people have got Intrepid and NM 0.7 going, then they reboot, and it is cactus again).

So, I'm thinking, what files are getting changed on a reboot ?

> **ajmorris said:**
> 
If this doesn't work, don't dispair, this is deffinitely possible to do, just a matter of going about it the right way (at this stage not sure what gnome tools will do it, im doing what you want on my PC, but purely through CLI -- i also know that the default NetworkManager in KDE4 handles this extremely well...)


I use KDE4 (and 3 as well I think ?), but CLI on Ubuntu, well I'm not that proficient with command line.

The frustrating thing is that on another Ubuntu box (Hardy), I was able to run ppp0 (dialup) and also share that connection with other computers. So, it does seem the Intrepid/NM 0.7 has a few bugs.

Thanks,

Oygle

---

### Post by oygle on 2009-01-15
> **ajmorris said:**
> 
There are methods in ubuntu to do what you want, (and NetworkManager *should* be able to handle it... it used to be able to) however, since it can't on your machine, theoretically, you should also be able to keep using NetworkManager for one interface, say wireless, then manually up your ethernet with ```
sudo ifconfig eth0 up
```



I finally enabled the LAN card again, tried to install drivers for it, then have found out Ubuntu does 'see' the eth0. I did the command as you have instructed above, and the lights came on in the hub/switch.

I go into network tools and there is now an eth0 there as well.  :D

To my amazement, I also still have internet, ... BUT will I have it on a reboot ?

Stay tuned.  :)

Thanks,

Oygle

---

### Post by oygle on 2009-01-15
Have still got the internet connection (ppp0) and the eth0 is up, but haven't rebooted yet.

Thought I would try to get the client computer to try and use the internet connection. It has eth0 up, but it cannot ping to the other computer, so no ICS as yet.

Have firestarter going on both computers, but no errors, in terms of either computer showing events from the other computer.

How to I trouble shoot this please ? I would like to be able to get the client computer to use ICS.

I may have either dnsmasq installed on one or both computers, and I used to have ipmasq installed on one. No doubt that could be causing some conflicts.

Oygle

---

### Post by superprash2003 on 2009-01-15
firestarter maybe blocking something..you could share internet connection this way [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. also you could try with static ips..

---

### Post by oygle on 2009-01-15
> **superprash2003 said:**
> firestarter maybe blocking something

Thanks, I did notice this morning, have a internet connection up, but no http or pop3, and Firestarter was not recording anything in the events. Go to syslog, and sure enogh, probs with port 80 and port 110 being blocked, so had to add a policy in Firestarter for both of those. Somehow, I think when I cleared all policies from Firestarter a few days ago, it actually got corrupted, as outbound blocks should get seen in events.

Also, when I tried a network restart today, it complained about an empty value in the interface file

> $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:8: option with empty value
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:8: option with empty value
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 



iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0

$ ls -al /etc/network/interfaces
-rw-r--r-- 1 root root 168 2008-12-26 16:12 /etc/network/interfaces
$ 

Nothing has changed in that file for 3 weeks, however now, for some reason, a restart doesn't like the gateway line with an empty value, I will remove that.

I'm loathe to adjust anything at all in NM, because it is giving me ppp0 and have been able to get eth0 at least 'up', outside of NM (NM shows it as unmanaged).

> **superprash2003 said:**
> 
..you could share internet connection this way [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. also you could try with static ips..

Thanks, will check out tha thread, and the static IP thing is probably the way to go, just need to work out how to do it all at CLI, instead of using NM.

Oygle

---

### Post by t0mc4t on 2009-01-16
Hello,

It seems that I have similar issue with yours.. The difference is only I'm using ath0 (WiFi) not eth0. Any solution in regards of this issue?
Btw, my topic is [http://ubuntuforums.org/showthread.php?t=1036673](http://ubuntuforums.org/showthread.php?t=1036673)
Thanks...


> **oygle said:**
> That's what I need to be able to do though, just that I can't even use eth0 at present, at the same time as ppp0, and I thought that guide was a 'how to' to have them both running concurrently :confused:


---

### Post by oygle on 2009-01-16
> **t0mc4t said:**
>  Any solution in regards of this issue?


I'm taking it VERY slowly. At present I have a working 3G connection (ppp0) and don't want to loose that. Network manger cannot handle 2 connections concurrently, and my eth0 is showing under NM now as 'unmanaged', so I'm going to leave it that way, and try and get around the problem, by not touching NM.

Here is what happens now.

1. On boot, the lan/eth0 is recognised and a driver loaded, but no lights on the hub/switch, this is because NM says it is unmamanged no doubt.

2.  I do this

```
sudo ifconfig eth0 up

```

and the lights come on, but I cannot ping to that computer (it cannot ping to itself) at this stage, even though it is shown in /etc/hosts.

3.  I do this

```
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0
```

and I can ping to it okay.

So, that's a good start. At least I haven't lost my ppp0 (3G) connection, and the eth0 is up and running. There needs to be more conclusive tests and info gained from the eth0 interface, before I try to use the LAN from another computer, to connect to the internet.

Certainly, circumventing NM is the way to go with this, that is, let NM still control the ppp0 connectio, and use CLI to get the eth0 up and running.

I won't have the same hassle on the 'client' computer, I don't think (the computer that will be using the shared connection), as it is not running Intrepid (Hardy). I just need to tell it what the gateway is.

But not sure about the dns side of things on the client, whether it should be the 2 dns IP's that are on the host, or whether it should actually be the host IP ( 192.168.1.100 ).

I did have ipmasq and dnsmasq installed on the host, but Firestarter has  ICS enabled , and besides, when I did have them installed on the host, pings across the lan stopped working, and I also lost the ppp0 connection.

I'm not convinced as yet that I need those 2 packages.

Slowly, slowly is the go, ....... and I'm very slow so it's okay. ;)

Oygle

---

### Post by t0mc4t on 2009-01-16
Hello,

Thank you for the respond..

> **oygle said:**
> Network manger cannot handle 2 connections concurrently, and my eth0 is showing under NM now as 'unmanaged', so I'm going to leave it that way, and try and get around the problem, by not touching NM.


How do I make that become unmanaged?
In NM there are is "System Setting" option. Would you please let me know what is that and should I checked it?

Little bit Out Of Topic, how do I connect to WiFi router with WPA2 encryption via the CLI (I mean the command).

Thanks..

---

### Post by oygle on 2009-01-16
> **t0mc4t said:**
> 
How do I make that become unmanaged?
In NM there are is "System Setting" option. Would you please let me know what is that and should I checked it?


If I knew how to view the NM settings without actually going into NM, then I would be able to tell you. If I go and do the 'edit connections' at this stage, I'm asking for trouble, as I've seen posts where people have gone into 'edit' and actually only viewed (no changes), and then, no internet.

Sorry, don't know about the CLI side of making a connection (the connect to WiFi router with WPA2 encryption via the CLI).

---

### Post by oygle on 2009-01-17
Well, I spoke too soon.  :(

Boot up today, and no internet connection. Then disbaled eth0, as the net connection (mobile boradband) used to only work, when no lan card in BIOS, .. yet still no internet.

Even with the lan disabled in bios, the drivers seemed to be still loaded, and this stopped the internet connection. Finally, in all desperation ..

```
sudo /etc/init.d/NetworkManager restart
```

and have the internet again. Why is the networking side of Ubuntu so "flakey" ?

Oygle

PS  As this is all getting a bit off topic, maybe discussions from here will go back to [http://ubuntuforums.org/showthread.php?t=1022569](http://ubuntuforums.org/showthread.php?t=1022569)

---

