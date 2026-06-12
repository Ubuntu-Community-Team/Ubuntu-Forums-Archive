---
title: "Internet Connection Problem"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Viktorja on 2009-11-07
[COLOR=Purple][B]Since about 9am this morning I have not been able to connect to the internet from my eeepc.  I am running Easy Peasy Ubuntu for netbooks version 8.10 (Intrepid).

I have ascertained that it is NOT an ISP issue.  When I connect the desktop computer (XP) to the modem it works just fine.  I also tried power cycling everything, to no avail. 

When I hook the eee directly to the modem, it does detect that there is a wired connection, and it tries to connect, but fails.


And since I changed the os when I bought the computer (from Xandros), ASUS isn't allowed to help me at all.

my comp is Asus eeepc 1000 / Intel Atom 1.6GHz

:( 


[/B][/COLOR]

---

### Post by Logan 1229 on 2009-11-07
Here's a few threads that may help you:
[http://ubuntuforums.org/showthread.php?t=1219931](http://ubuntuforums.org/showthread.php?t=1219931)
[http://ubuntuforums.org/showthread.php?t=1197614](http://ubuntuforums.org/showthread.php?t=1197614)
[http://ubuntuforums.org/showthread.php?t=1211738](http://ubuntuforums.org/showthread.php?t=1211738)

I also have a 1005HA & but use Eeebuntu.  Once I got the internet issue solved, no problems whatsoever.

---

### Post by Viktorja on 2009-11-08
I read through the threads you listed for me, thank you for those, btw.  
However, they are all for Jaunty users, and I do not have any way to upgrade my os at this time.  Also, due to the limitations of the desktop computer, there is no way for me to transfer anything that i've downloaded, so I can't download drivers to the desktop and move them to the laptop unfortunately.

The internet worked fine from February up until yesterday morning at 9am.  Is there a setting somewhere inthe computer for detecting and connecting to wired net?  My cousin has managed to some how disable the internet on her computer, and I am wondering if that might be the problem on mine.

---

### Post by Viktorja on 2009-11-08
[COLOR=Purple][B]I posted this under general help, but thought it fit here as well, so I am reposting in hopes that someone will have an idea as to what I can do to fix this.

Since about 9am yesterday morning I have not been able to connect to the internet from my eeepc. I am running Easy Peasy Ubuntu for netbooks version 8.10 (Intrepid).

I have ascertained that it is NOT an ISP issue. When I connect the desktop computer (XP) to the modem it works just fine. I also tried power cycling everything, to no avail. 

When I hook the eee directly to the modem, it does detect that there is a wired connection, and it tries to connect, but fails.

And since I changed the os when I bought the computer (from Xandros), ASUS isn't allowed to help me at all.

my comp is Asus eeepc 1000 / Intel Atom 1.6GHz

Additonally due to the limitations on the desktop computer, I am not able to download and transfer drivers or os upgrades to the laptop.  

Even if someone can just tell me where to look on the eee to find out WHY it stopped working for no apparent reason, that might give me a next logical step.  Unfortunately my router doesn't log, and I do not know how to read the system logs on the comp.

Thank you in advance for any help you can give me.


[/B][/COLOR]

---

### Post by cariboo on 2009-11-08
Please don't double post on the same subject, I have merged your two threads. I'm not to excited about your choice of font colors either.

---

### Post by cariboo on 2009-11-08
What did you change that stopped your network connection? Was it an update, a configuration file change? Open a terminal and type:

```
sudo lshw -C network > network.txt
```

The above command creates a text file called network.txt which you can copy to a thumbdrive and transfer it to your computer with a working network connection. The command will list all the information about your network connection.

---

### Post by Viktorja on 2009-11-09
Here is the copy/paste of the network.txt file. 
Also in answer to your question, I did nothing to change any settings on my computer.  I was asleep, and the connection was working fine at 3am.
When i woke up at 11am, i discovered that at 9am it had stopped working.

I have done no recent updates or configurations.  I set my eee up in March when I got it, and haven't touched any settings or configurations since, as I do not know what I am doing in Linux.
--

*-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:a4:5c:44
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:00:0e:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:35:81:b6:3a:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Iowan on 2009-11-09
Post results of **ifconfig -a** (in similar fashion to the way you posted results of **lshw -C network**).

---

### Post by cariboo on 2009-11-09
Go to /etc/NetworkManager/nm-system-settings.conf and check to see if the device is mamaged, there should be a line in the file saying something like managed=true or false, if it says false, change it to true and reboot.

---

### Post by Viktorja on 2009-11-09
okay here is the copy/paste of the command you gave me:

eth0      Link encap:Ethernet  HWaddr 00:22:15:a4:5c:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3460 (3.4 KB)  TX bytes:3460 (3.4 KB)

pan0      Link encap:Ethernet  HWaddr e2:35:81:b6:3a:be  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr 00:22:43:00:0e:4a  
          inet6 addr: fe80::222:43ff:fe00:e4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:113503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17651907 (17.6 MB)  TX bytes:2693483 (2.6 MB)
          Interrupt:19

---

### Post by Viktorja on 2009-11-09
Criboo907 - I found the file you advised me to go to...it DOES say "false", however I had to open it with the text editor, and when i attempted to save the .conf file it says I do not have permission.
Is there a line command in a terminal that I can use or a method to get "permission"?  I tried to open it using the sudo command but it's saying command not found.  
I am not that experienced with line commands, though, so I am probably using the wrong terms.

I am the only person who owns or uses this computer so I should have the permissions for this...I would think...

Thanks again for the help.

---

### Post by cariboo on 2009-11-09
As with all files and directories, if they aren't in your home directory, you need to be root to access them. Press Alt-F2 and type:

```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

The above command will open the file in a text editor, running as root. Make the changes to the file, then save it and close, then reboot

---

### Post by Viktorja on 2009-11-09
I followed your instructions and rebooted, but unfortunately it still will not connect.
I ran sudo lshw -C network > network.txt again.  The 3rd section at the bottom still saying disabled.  I checked the .conf file and the change saved properly.

Here is the .conf file: 
[main]
plugins=ifupdown,key

file

[ifupdown]
managed=true

-- -- --
and this is the output of the lshw command:

*-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:a4:5c:44
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:00:0e:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:35:81:b6:3a:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


-- -- --

*sigh* I am open to other ideas.
Please let me know if this is a lost cause and I will just sit through a formatting and re install the os, as a last resort.

Thanks for all of your help; it is very much appreciated.

---

### Post by cariboo on 2009-11-09
According to your listing, you should have a network connection, pan0 being disabled is normal.

---

### Post by Viktorja on 2009-11-09
hrm...that does not inspire hope. i tried two different cables, and the modem is definitely working...i have the desktop machine, an XP hooked up and online without a hitch at the moment.

Any ideas as to what I could do next?

---

### Post by Iowan on 2009-11-09
Is wired connection configured via Network Manager, or via */etc/network/interfaces*? Static (manual) or DHCP?

---

### Post by Viktorja on 2009-11-09
To be honest, I have no idea?  Prior to this issue, I simply plugged the cord into the modem, plugged the other end into the laptop and it connected automagically.  I have never had to mess with the network or anything on it.

If you tell me how to find out, though, I will look...

---

### Post by Iowan on 2009-11-09
Post */etc/network/interfaces*. For a Network Manager-ized connection, the file may contain only two lines configuring "lo" (loopback device). I never used Intrepid, but seems like it was a li'l touchy (maybe it's been updated since then...)

---

### Post by Viktorja on 2009-11-09
it says:

auto lo
iface lo inet loopback

---

### Post by Iowan on 2009-11-09
That'd be 'bout normal for NM-managed interface.  You can try (from that terminal you're getting familiar with): ```
sudo dhclient eth0
``` I suspect it'll complain, but *might* yield more information.
Might also want to check the interface configuration in NM - I doubt it's changed, but something apparently has...

(lest I forget - NM is Network Manager)

---

### Post by Viktorja on 2009-11-09
Here is the output:

Listening on LPF/eth0/00:22:15:a4:5c:44
Sending on LPF/eth0/00:22:15:a4:5c:44
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---
*sigh*

---

### Post by cariboo on 2009-11-09
There is one thing I have run into, I don't know if that is still a problem. Is your wireless working? At one point, network manager wouldn't let both connections work at the same time. When you left click on the Network Manager Icon do you see any wireless networks?

---

### Post by Viktorja on 2009-11-10
That sort of thing was never a problem for me, but yes the wireless works just fine; I've taken the eee to wi fi spots and had no trouble at all connecting.

Also, my router is in need of reconfiguration so that is why I am unable to connect at home wirelessly at the moment.  The router isn't hooked up at this time, so I don't feel that it is the cause of the wired not working.

It's times like this I wish I lived closer to the city where people have wireless routers without passwords on them lol.  I'm not a fan of having to borrow computers. lol.

---

### Post by cariboo on 2009-11-10
Even if you don't have a wireless connection, if the device is active, you may not get a wired connection

I would suggest you blacklist the wireless driver, just to see if what I said is the problem. Press Alt-F2 and type:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

and add:

```
blacklist rt2860
```

to the bottom of the file. Save it and close it, then reboot to see if you have a wired connection.

---

### Post by Viktorja on 2009-11-10
Still no dice.
I also tried power cycling the modem in addition to that.
Nothing. :-(

---

### Post by cariboo on 2009-11-10
I hate to say it, but I've run out of things to suggest.

---

### Post by Iowan on 2009-11-10
A few more things... Although the ultimate goal will be a DHCP connection, perhaps we can see if ANY connection will work. [This]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") How-To deals with setting up static IP in Intrepid. First, we'll need to decide which IP address to try. Do you have access to whatever machine is supposed to be providing DHCP addresses (modem?)? The machine you're using might give a clue what range is in use - what is it's IP address?

---

### Post by Viktorja on 2009-11-10
Thank you so much for your help; I really really appreciate it!
I'm just going to wipe the drive and reinstall my easy peasy os.
If that doesnt fix it, then maybe it's a hardware issue and covered by warranty.  ::crosses fingers::
Thank you again for the help.

---

### Post by Iowan on 2009-11-10
Good luck! I'll hope to see this thread marked [SOLVED] next time around.

---

