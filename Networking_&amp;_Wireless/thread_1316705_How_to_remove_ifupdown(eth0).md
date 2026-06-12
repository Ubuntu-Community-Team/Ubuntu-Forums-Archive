---
title: "How to remove ifupdown(eth0)??"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by prashantbhardwaj89 on 2009-11-06
I have recently upgraded my system to Ubuntu 9.10 from 9.04 ...
I hv a dsl broadband connection which is working fine in 9.04 when created with network manager...
Now in 9.10 I'm getting a ifupdown(eth0) wired connection which in non-editable.. n also I'm not able to create any connection.. Help me Plzz !!!

---

### Post by prashantbhardwaj89 on 2009-11-06
Output lshw -C network

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:76:5e:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.09 latency=0 multicast=yes
       resources: irq:30 memory:f69f0000-f69fffff

---

### Post by SawyerLX on 2009-11-06
Seems to have a bug, I have same problem.  Fresh install edited Network Manager then tryed to connect to the new dsl and did Not connect, then restarted and ifupdown (eth0) replaced auto (eth0) and removed my dsl connection.  Then went to use pppoeconf under console.
 I thought it was the beta RC i was using.,yet  *am currently on the Final 9.10. ugly and needs to be patched!*

---

### Post by shahan on 2009-11-07
> **prashantbhardwaj89 said:**
> I have recently upgraded my system to Ubuntu 9.10 from 9.04 ...
I hv a dsl broadband connection which is working fine in 9.04 when created with network manager...
Now in 9.10 I'm getting a ifupdown(eth0) wired connection which in non-editable.. n also I'm not able to create any connection.. Help me Plzz !!!

I have the same problem. I use Static IP Broadband connection. this is a bug I think. It should be reported to the UBUNTU Bug report center( I don't know how to do it.)

---

### Post by SawyerLX on 2009-11-08
yeah, connecting via
"sudo pppoeconf"

Funny I told somewone this is probably the best OS i have seen.
Until this problem made me realize I had to text someone the next day to give the above command,
               Otherwise,
                               it is extremely smooth and no other problems.

This is essential bug fix:

  Network applet configures wired ethernet name to grab the ethernet card caller right.
and thatlss be the fix...I;m an idiot, but you get the jist.

maybe version 9.10.?

---

### Post by peepingtom on 2009-11-08
NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

---

### Post by shahan on 2009-11-09
> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

**this is working excellent :D. the problem has been solved. Actually I do the change etc/network/interface file manually due to my [internt connection problem]("http://ubuntuforums.org/showthread.php?t=1211081").**

---

### Post by rtotheototheb on 2009-11-13
Cheers peepingtom, life saver!

---

### Post by Soweto on 2009-11-23
> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

ALAS!!! Problem solved. The reason I messed around with CLI is that at home I used DSL (pppoe) and at work I'm on ethernet. I gets a bit tricky for me to define both. I try defining DSL thru NM 2nite.

Edit: Sorry, I forgot to say thanks. I'm in such a hurry to navigate Karmic... :D

---

### Post by SawyerLX on 2009-11-23
"For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

      "If this doesn't work, post here again.[/quote]


You know I already have it at managed=false, but
I did fresh install, used "pppoeconf" then two updates before I tried to work on NM by changing the file to see if nm-applet would get rid of   ifupdown(eth0)    problem.

i changed managed=true to see what happens.
while waiting for continually/any updates, If NOTHING for Network Manager is fixed I am going to change conf file back and wait for updates.

---

### Post by ManzTiara on 2009-11-24
as per SawyerLX to change managed=true and restarting the network.
Sorry this unsuccessful for me. due to had error message such as :

~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

---

### Post by oremusnix on 2010-01-03
It solved my problem after updating to 9.10, thank you!

---

### Post by produnis on 2010-01-24
> **peepingtom said:**
> 
Check /etc/network/interfaces.
```
gksudo gedit /etc/network/interfaces
```Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```set 
```
 [ifupdown]
managed=false 
```Restart computer or NetworkManager service.


Thank you so much.
This was exactly I was searching for to set  *ifupdown (eth0)  *back to  *Auto eth0*

Works like charme...

---

### Post by ubuinschool on 2010-01-25
THANKS for a great solution. I had, indeed, manually edited the network config. This worked for a while until restart, but then I got stuck with the locked ifupdown. Forum support is awesome!:D

---

### Post by CosminGC on 2010-02-04
> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

Thank you. That helped me too.

---

### Post by djgrant on 2010-02-18
> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

Worksk like a charm, thanks so much. :)

---

### Post by psrivats on 2010-02-28
I have a related problem that I described here when I setup OpenDNS:
[http://ubuntuforums.org/showthread.php?t=1418622](http://ubuntuforums.org/showthread.php?t=1418622)

Here are the contents of my /etc/network/interfaces :

```
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

```

and /etc/NetworkManager/nm-system-settings.conf :

```
[main]
plugins=ifupdown,keyfile

no-auto-default=00:15:58:2f:c0:df,

[ifupdown]
managed=true

```

This is the only combination that will let me connect to the internet on the wired connection.

When I comment out the eth0 lines in /etc/networking/interfaces, set managed=false in the nm-system-settings.conf and restart networking and network-manager as described above, I cannot connect to the internet.

What am I doing wrong? Can someone help me to set this right, please?

---

### Post by psrivats on 2010-03-04
^Anyone?

---

### Post by psrivats on 2010-03-05
OK, I found the fix myself - somehow, the IPV6 settins were set to 'Automatic'. I changed that to 'Ignore', and then commented the eth0 lines in /etc/network/interfaces and selt managed=false in nm-system-settings.conf. After restarting the networking and networkmanager services, everything is back to normal. Hooray.

---

### Post by Tsquad on 2010-03-06
umm, i have the ifupdown and i just went to change managed= to false and it was already at false....what now?

---

### Post by hfxrzw on 2010-03-06
I have the same. Yesterday I had the problem with ifupdown. Restarting today, finding this thread and checking the files ifupdown has gone, the file settings are as the above, so Auto eth0 has returned, however restarting with just the wired connection (its a laptop) doesn't start the network. The green light is on of the ethernet card and the yellow comes on once in a while, but the system doesn't connect. I have not set an IP number, the settings are on DHCP. Other computers on the network have no issue connecting, so DHCP is working.
So I seem to have a card that is detected, but not being used.

Any idea where to look? Thanks, Rene.

Looking further I have noticed that in 'Network Tools' only the loop and the wireless are listed, but not eth0 as interface. Looking in 'Network Connections' I have the eth0 listed, but my wireless adapter eth1 is now listed twice????? Utterly confused here.

---

### Post by cuh on 2010-07-08
I had the same annoyance and the solution works for me, too. Thanks peepingtom!

---

### Post by steph5150 on 2010-10-27
Hi,
I know it's an old thread but I think I found the "bad line to remove" thing... and I think this is a more elegant method.

Try this :

For Ubuntu :
    
     ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
```For Debian users the file to edit is :
    
    ```
 gksudo gedit /etc/NetworkManager/NetworkManager.conf 
```
then remove the 'ifupdown' plugin reference so that the file look like this :
     
```
[main]
plugins=keyfile

[ifupdown]
managed=true 
```Reboot and voilà, now 'ifupdown(eth0)' is gone and you can choose your connection using nm-applet :

_ a left click on the nm-applet icon will let you choose on-the-fly between  the different connections previously configured (manually)

_ a right click on the nm-applet icon and you can configure your connections (or you can use nm-connection-editor as well), again, manually, but with a graphic interface  :-)

hope it helps...(forgive me for my bad english)

---

### Post by steph5150 on 2010-10-27
forgot to say :

As said by **peepingtom[B] :**[/B]

```
gksudo gedit /etc/network/interfaces
```this file should only contain :

```
auto lo
iface lo inet loopback
```And last, I appologize, the solution was (almost) there, the only 2 little things that was missing for me was the keyfile plugin (wep and wap things) and the managed=true (with managed=false Evolution starts offline and it's annoying).

---

### Post by ben2talk on 2011-05-04
> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
```
gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again.

Actually, works well with Natty 11.04 too - but the file name is now (same location **/etc/NetworkManager**)[COLOR="DarkRed"]** NetworkManager.conf**[/COLOR])

Thanks, helped me out - I set this up following a web guide and feel ashamed to say I didn't keep any notes....

I really must start making better use of Tomboy, or at least not be too lazy to keep a text file updated and tucked away somewhere when I do stuff I don't really understand too well.

---

