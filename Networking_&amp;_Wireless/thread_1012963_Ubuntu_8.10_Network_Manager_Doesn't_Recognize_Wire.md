---
title: "Ubuntu 8.10 Network Manager Doesn't Recognize Wired Network Device"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by davism81 on 2008-12-16
I have what seems to be a somewhat unusual problem.  I've been running Ubuntu on my main desktop for about a year now.  Upgraded from 8.04 to 8.10 with no problems and have been running 8.10 since just a few weeks after it was released, with no problems.  However, this morning I installed a bunch of updates that came down the pipe (didn't even really look at them, as I've gotten used to all updates installing without any problems), and after the reboot my wired ethernet connection (an onboard Realtek PCIE x1 LAN 8101E on an ASROCK Conroe 1333 D667 motherboard) stopped showing up in the Network Manager, and the Network Manager applet showed up in the Notification Area, saying that my network connection was unmanaged.  Basically, as far as Network Manager is concerned, I'm not connected to any network and I have no network devices.  Despite this, my wired ethernet connection still works perfectly fine.  It shows up on eth0 when I run ifconfig, I get an IP address with DHCP, and I can connect to the internet (in fact I'm posting this post from the computer that's having the problems).  It just doesn't show up in the Network Manager.  I uninstalled and reinstalled the network-manager and network-manager-gnome packages, but it didn't make any difference.  I searched around a bit for solutions, but most people seem to be having problems with their wireless connections showing up, not with their wired connections.  Here is my ifconfig output:

> eth0      Link encap:Ethernet  HWaddr 00:19:66:53:86:53  
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe53:8653/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5824025 (5.8 MB)  TX bytes:1291773 (1.2 MB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16581 (16.5 KB)  TX bytes:16581 (16.5 KB)

And here is what's in my /etc/network/interaces

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

As of now my "solution" has simply been to uninstall network-manager and network-manager-gnome and live without them.  Since it's a desktop computer, I don't move it around at all and I don't use wireless, so as long as the wired connection is working, not a big deal.  Still, it bothers me slightly that this just suddenly stopped working, and if I can fix it I would like to.  Any advice or help would be appreciated, and please accept my apologies in advance if this is something that has already been covered (although if it has, I'd appreciate a link, as I haven't been able to find anything!).

---

### Post by flyingbrass on 2008-12-16
An update apparently hosed network manager.  My interfaces file is the same as yours, and now there's an x showing on the network manager icon.  Connection information says "no valid active connections found."

As long as you still have a connection, don't worry about it.  I'm a bit disappointed that updates are still breaking things.  I thought everything was being tested before release through the proposed repository.

---

### Post by davism81 on 2008-12-16
> **flyingbrass said:**
> An update apparently hosed network manager.  My interfaces file is the same as yours, and now there's an x showing on the network manager icon.  Connection information says "no valid active connections found."

As long as you still have a connection, don't worry about it.  I'm a bit disappointed that updates are still breaking things.  I thought everything was being tested before release through the proposed repository.

Yeah, that's exactly what happened to me.  Good to know I'm not the only one, anyway.  Hopefully it will be fixed with the next updates, I guess I'll just be living without the Network Manager until then, unless someone has a fix?

---

### Post by Snappo on 2008-12-16
My network manager won't start on my laptop with these updates.

---

### Post by xeddog on 2008-12-16
Add me to the list.  My network icon has a "!" on it instead of an x but other than that I'm hosed.  I have tried manually adding another connection and I am unable to do that either.  I get all the information in the profile and I can save it.  It won't activate, but I can save the profile.  Then when I go back and edit the profile and check the  "system setting" box and try to save it, I get a prompt for root password.  As soon as I enter it, the profile just disappears.  Poof.

Xeddog

---

### Post by cmapesjr on 2008-12-16
Same problem here with my 64 bit box. I still have a connection
but it sure freaked me out a bit. I guess I don't dare update my
other two 32 bit boxes. :confused:

---

### Post by jrobbo on 2008-12-16
Phew! I've been playing around with networking alot over the past few days trying to get bridging going with VirtualBox. After I had installed the latest updates this morning, I also ran into this problem, but naturally thought that I had broken something, have been tearing my hair out all morning trying to figure this out. Sort of releived to find out that it wasn't me! :)

John

---

### Post by Naipes on 2008-12-17
Add me to the list too.

Unfortunately, without an internet connection I cannot get any updates that might fix this problem.  

Guess I'll try the uninstall network manager thing and see if that works.

After a couple of days of searching through these forums it looks to me like there's a whole LOT of people with this problem.

---

### Post by The Cog on 2008-12-17
I think that network-manager is supposed to ignore any interfaces that have configuration entries in the file /etc/network/interfaces. This may be why it is ignoring eth0. The only 2 lines you should have in there are:
> auto lo
iface lo inet loopback
network-manager seems to be very problematic in Intrepid. I recommend installing **wicd** instead. This can be downloaded from [http://wicd.sourceforge.net](http://wicd.sourceforge.net) . I couldn't make their install instructions work, so I downloaded the .deb file from here [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573) and double-clicked the file in nautilus to install it. Works a treat!

---

### Post by jts0803odon on 2008-12-17
Wanted to chime in as well. Updates this morning, little orange triangle appears in my Network Manager panel icon, shows Wired Network device is unmanaged. eth1 is working fine, however, as you can see.

---

### Post by tom-ubuntu on 2008-12-17
Add me to the list aswell; network manager does not see my wired connection aswell. Everything still working fine. Waiting for an update...

---

### Post by BUNAC on 2008-12-17
Aaaaarrrgh! I'm trying to set up Firestarter to share my internet connection through a second NIC and I think the Network Manager update has screwed the pooch!

I can see eth1 and select connections but eth0 is greyed out.
Firestarter gives me the error "Failed to start firewall. The device eth0 is not ready".

Would this be the same issue?
How quickly are these issues usually resolved? 

Cheers
Tom

---

### Post by flyingbrass on 2008-12-17
> **The Cog said:**
> I think that network-manager is supposed to ignore any interfaces that have configuration entries in the file /etc/network/interfaces. This may be why it is ignoring eth0. The only 2 lines you should have in there are:

auto lo
iface lo inet loopback

Paring it down to that solved the issue for me.  Earlier I had a bridge connection set up for KVM and couldn't remember if eth0 was listed there originally or not.  It may have been.  Network manager used to insist on creating a DHCP eth0 connection automatically regardless of settings.

---

### Post by zika on 2008-12-17
> I think that network-manager is supposed to ignore any interfaces that have configuration entries in the file /etc/network/interfaces.it depends of the switch in the file ```
/etc/NetworkManager/nm-system-settings.conf
```that is ```
[ifupdown]
managed={true,false}
```true=let NM rule.
false=let ifup/ifdown rule.

---

### Post by jrobbo on 2008-12-18
Although eth0 doesn't show up in NM for me, i'm still able to use it just fine. I just added these 2 lines to /etc/network/interfaces:

```

auto eth0
iface eth0 inet dhcp

```

and then restarted networking (/etc/init.d/networking restart)

Hope this helps

John

---

### Post by madsmaddad on 2008-12-18
Me too. I installed 8.10 from CD on to a free computer and it picked up the wireless USB stick no problem. So I upgraded my 7.10 to 8.10 over the wireless and now I have no wireless network. I am in a location where I have no wired network, so am dependent on wireless. 

Catch 22. I don't have a wireless network to download fixes over.

---

### Post by oygle on 2008-12-18
> **BUNAC said:**
> Aaaaarrrgh! I'm trying to set up Firestarter to share my internet connection through a second NIC and I think the Network Manager update has screwed the pooch!

I can see eth1 and select connections but eth0 is greyed out.
Firestarter gives me the error "Failed to start firewall. The device eth0 is not ready".


I had a problem with Firestarter, but it _could_ have been network manager that screwed things up, see [this thread]("http://ubuntuforums.org/showthread.php?t=1012800")

---

### Post by rggavubt on 2008-12-19
I've just noticed that I have the same problem on my Lenovo R61i laptop which I usually connect wirelessly.  I took it upstairs to connect directly and it would not connect using the wired Lan connection.  When I look at the available connections the wired "Auto eth0" is greyed out.  When I go to system, preference, network connections the "Auto eth0" line says never.  I upgraded to 8.10 when it came out and just noticed this problem.  I had no problems with 8.04.:confused:

---

### Post by SwooshOU on 2008-12-19
After some updates, my ethernet port is not working either.

---

### Post by baAng on 2008-12-19
hello..i've tried this solution that i got from Ubuntu Documentation. I managed to enable *the wired connection and can surf the net*, but it seems like in the Network Manager the Wired Connection status don't pop up and also in the panel tray there is still X sign at the Network Manager icon.

This are the steps.

1) Open the terminal.

2) Type **sudo ifdown eth1** in the terminal and press **Enter**. 
*Replace eth1 with the name of your network interface if it is different. *

3) Enter the password if prompted.

4) Type **sudo ifup eth1** in the terminal and press **Enter**, again replacing _eth1_ with the name of your network interface.

5) If you have connected successfully, you should see a message similar to the following:

```
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.
```

Now, you should be able to surf the net. I hope it helps.:p

---

### Post by SwooshOU on 2008-12-19
double post

---

### Post by zika on 2008-12-20
this is what worked for me in october when I updated from 8.04 to 8.10 and lost all networking also:

```

sudo nano /etc/network/interfaces

```then make this file look like:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```or, if You need static address:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface static
auto eth0
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask xxx.xxx.xxx.xxx
    gateway xxx.xxx.xxx.xxx
    broadcast xxx.xxx.xxx.xxx
```andcode] sudo nano /etc/resolv.conf[/code] and make it look like:```
nameserver xxx.xxx.xxx.xxx
``` with Your DNS ...

then restart networking (or start, since it's not working) with:

```
sudo /etc/init.d/networking restart
``` or ```
sudo ifdown eth0
sudo ifup eth0
```that way You might see a orange triangle on Network manager or no NM at all but have working connection. You can prevent NM from showing up by disableing it in Preferences->Sessions->uncheck Network Manager.

hope You'll have lasting network connection and forget about NM.

---

### Post by oygle on 2008-12-20
Seems like it is a good idea to have the path /etc included in backups. That way, at least running Kdiff3 or similar on the untarred backup, will reveal what _used_ to work. It appears Networking manger has corrupted some files ?

---

### Post by rggavubt on 2008-12-20
> **baAng said:**
> hello..i've tried this solution that i got from Ubuntu Documentation. I managed to enable *the wired connection and can surf the net*, but it seems like in the Network Manager the Wired Connection status don't pop up and also in the panel tray there is still X sign at the Network Manager icon.

This are the steps.

1) Open the terminal.

2) Type **sudo ifdown eth1** in the terminal and press **Enter**. 
*Replace eth1 with the name of your network interface if it is different. *

3) Enter the password if prompted.

4) Type **sudo ifup eth1** in the terminal and press **Enter**, again replacing _eth1_ with the name of your network interface.

5) If you have connected successfully, you should see a message similar to the following:

```
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.
```

Now, you should be able to surf the net. I hope it helps.:p

I tried this and got back that "eth0 is not configured" when I entered the first line?:confused:

---

### Post by jts0803odon on 2008-12-22
Wanted to chime in again and say that [The Cog @ #9]("http://ubuntuforums.org/showpost.php?p=6385527&postcount=9") posted the comment that worked for me. 

Commented out anything (per The Cog's comment) that wasn't in the two lines for the loopback. Upon boot this morning "Auto eth1" shows up in Network Manager. 

Quick "less /etc/network/interfaces" confirms nothing changed in the file that I didn't enter myself. So, fixed over here. Thanks to The Cog.

---

### Post by pedro.leite on 2008-12-22
Just to let you know that I've had the same problem, but these instructions solved it (at least for my DHCP configuration)!

Thanks zika!

> **zika said:**
> this is what worked for me in october when I updated from 8.04 to 8.10 and lost all networking also:

```

sudo nano /etc/network/interfaces

```then make this file look like:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```or, if You need static address:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface static
auto eth0
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask xxx.xxx.xxx.xxx
    gateway xxx.xxx.xxx.xxx
    broadcast xxx.xxx.xxx.xxx
```andcode] sudo nano /etc/resolv.conf[/code] and make it look like:```
nameserver xxx.xxx.xxx.xxx
``` with Your DNS ...

then restart networking (or start, since it's not working) with:

```
sudo /etc/init.d/networking restart
``` or ```
sudo ifdown eth0
sudo ifup eth0
```that way You might see a orange triangle on Network manager or no NM at all but have working connection. You can prevent NM from showing up by disableing it in Preferences->Sessions->uncheck Network Manager.

hope You'll have lasting network connection and forget about NM.

---

### Post by rggavubt on 2008-12-23
Thanks to Zika....I made his changes and now it works.  It will not connect automatically.   It first connects wirelessly and then I have to click ethernet and reconnect.  It still shows as "eth0 never" in the connection manager.:popcorn:

---

### Post by crazyness003 on 2008-12-23
it appears i got this problem when i did some modding to get my VirtualBox client (XP) to access my home network.

I added a bridge and a tunnel to the /etc/network/interfaces. this is what my file looks like:
```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports eth0 vbox0

#the loopback NI
auto lo
iface lo inet loopback
```I got instruction for this from [here]("http://help.ubuntu.com/community/VirtualBox#line-182")

At first my network didnt work! but i did a [FONT=Courier New]sudo /etc/init.d/networking restart[/FONT] and it worked. Im guessing i have to do that after every restart. I wonder if i should comment out the eth0 from the interfaces file?...hmmm

---

### Post by zika on 2008-12-24
> **crazyness003 said:**
> it appears i got this problem when i did some modding to get my VirtualBox client (XP) to access my home network.

I added a bridge and a tunnel to the /etc/network/interfaces. this is what my file looks like:
```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports eth0 vbox0

#the loopback NI
auto lo
iface lo inet loopback
```I got instruction for this from [here]("http://help.ubuntu.com/community/VirtualBox#line-182")

At first my network didnt work! but i did a [FONT=Courier New]sudo /etc/init.d/networking restart[/FONT] and it worked. Im guessing i have to do that after every restart. I wonder if i should comment out the eth0 from the interfaces file?...hmmm


just put ```
[FONT=Courier New]sudo /etc/init.d/networking restart[/FONT]
```[FONT=Courier New] in ```
/etc/rc.local
``` or make an entry in Preferences->Sessions with that command and forget about it ... ;)[/FONT]

---

### Post by crazyness003 on 2008-12-24
> **zika said:**
> just put ```
[FONT=Courier New]sudo /etc/init.d/networking restart[/FONT]
```[FONT=Courier New] in ```
/etc/rc.local
``` or make an entry in Preferences->Sessions with that command and forget about it ... ;)[/FONT]
i guess that could work. I still havent tried to comment out the 
```
auto eth0
iface eth0 inet manual
``` from the file and see if i can still play with my Vbox, while not messing with Network Manager. I have other things to get done for now.
But thanks for the idea. I rarely restart this machine, but that will come in handy.

---

### Post by chitresh4u on 2009-01-02
I am facing the same problem. Network manager shows that my wired connection device is unmanaged after an update. I also noticed that firefox connects to internet without any problem but pidgin and update manger cannot. Though I am able to get the packages from synaptic without any problem.

Is the problem solved??

---

### Post by chidge on 2009-01-02
> **chitresh4u said:**
> I am facing the same problem. Network manager shows that my wired connection device is unmanaged after an update. I also noticed that firefox connects to internet without any problem but pidgin and update manger cannot. Though I am able to get the packages from synaptic without any problem.

Is the problem solved??

I had exactly the same problem only resolved by altering my **/etc/network/interfaces** file as outlined in [this post]("http://ubuntuforums.org/showpost.php?p=6385527&postcount=9") then altering Network Manager re: [this post]("http://ubuntuforums.org/showpost.php?p=6136768&postcount=4") so that my static IP was remembered.

Hope this helps :KS

---

### Post by chitresh4u on 2009-01-03
> **chidge said:**
> I had exactly the same problem only resolved by altering my **/etc/network/interfaces** file as outlined in [this post]("http://ubuntuforums.org/showpost.php?p=6385527&postcount=9") then altering Network Manager re: [this post]("http://ubuntuforums.org/showpost.php?p=6136768&postcount=4") so that my static IP was remembered.

Hope this helps :KS

Yeah it helped. Thanks a lot. :D

---

### Post by pgmer6809 on 2009-01-04
I have not been able to get wired LAN working on Ibex either.
Previous809ly on gutsy I could get it to work by manually setting things up.
But in IBEX even that does not work.
Wireless network is fine though. 
This problem with wired network has now been around for at least 3 releases. What is the point of a live CD if they cant get simple networking to work.
pgmer6

---

### Post by dulbirakan on 2009-01-14
I faced this problem for the first time yesterday on my GF's desktop.

The symptoms were similar.

There was a never after eth0 in the connection manager, so I went ahead and opened my Laptop to browse for information only to find out my Laptop was also suffering from the same problem.

Then I added those two lines to my /etc/networking/interfaces and the problem seemed to go away.

But today my GF called to inform that it was broken again...

---

### Post by balbina on 2009-01-21
I've got the same, but this problem is bit deeper. It affects also the mobile broadband connections. I gave up after a month and decide to reinstall system :(
now the wired network is fine but I'm bit worried to install all updates. Does anybody know which one was causing the problem?

---

### Post by oygle on 2009-01-21
It's bug/s in Network manager. You may be safer to keep your system up to date but do a full backup first. If something doesn't 'work' after the updates, then untar the full backup and comprae it with your file system (say, use kdiff3 for this), the latered/modified files will be the ones causing the problem/s.

Seems a few people have found a workaround at [http://ubuntuforums.org/showthread.php?t=1034664](http://ubuntuforums.org/showthread.php?t=1034664)

I have mobile broadband as well, and it makes it more complex, becasue its not just ethernet, its ppp0 and eth0 to get 'going'.

---

### Post by n5wy on 2009-01-24
Well, I have been running Ibex since December and have had no problems with NM while using various combinations of DHCP and static config profiles for eth0 and wlan0 NIC cards on my computer. Today I did a bunch of new updates (about 60 I think) and after the reboot and such, I noticed that the wlan0 card is still working fine in NM, but the eth0 says its unmanaged. 

I can get eth0 working by editing the config files directly, but this is a pain since I am now so used to using NM to quickly switch back and forth between my various profiles. 

I find it odd that I am having this trouble all of a sudden, when it appears to have cropped up earlier for so many others that have posted in this thread. Is it simply a problem with NM, or is it also related to the NIC card hardware drivers?

---

### Post by oygle on 2009-01-24
60 updates is a lot, as I had only 2 last night for Intrepid, so I guess you don't do daily updates ?

Do you use a backup app, like simple backup, so that you can tell which files have changed ?

> 
.. the wlan0 card is still working fine in NM, but the eth0 says its unmanaged.

That is 'normal' for NM though, it can't manage 2 connections concurrently. I don't think you should have to modify files , just to get eth0 working, I'm using ppp0 and eth0 with NM and Intrepid, see [http://ubuntuforums.org/showthread.php?t=1022569](http://ubuntuforums.org/showthread.php?t=1022569) ; although NM says eth0 is unmanaged for me also, I just added some cli commands, and all is working fine since.

Oygle

PS  No doubt the [ACPI update]("http://ubuntuforums.org/showthread.php?t=1042755") was included in the 60 updates.

---

### Post by hundrambit on 2009-01-29
New version of NetworkManager completely ignores the **/etc/network/interfaces** file, it does own configuration and saves all settings in **/etc/NetworkMnagager**, (there is one known bug with saving settings aswell, but that's another apple). I don't know what NetworManager developers were thinking when they released version 0.7.0, atleast they could have thought about importing settings from **/etc/network/interfaces** on first start, but they haven't. Awful release. My knowledge about **/etc/network/interfaces** has always helped me, and from now on NetworkManager takes it away from me, well, **sudo apt-get remove** is the way to go. :)

---

### Post by delboy1 on 2009-02-07
Hi

I am having a real nightmare with a Dell Mini 9 and ubuntu involving 4 OS reinstalls in the week that I have had it and an XP disc getting ever closer to hand

This morning I installed 8.10 and all seemed fine after install. I got sound working, connected to the internet (wired) and also checked wireless.

I then installed the 245 updates that were notified and now my wired connection will not work. I have tried all the suggestions in this thread but nothing works.

Can anyone help?

---

### Post by dragonmojo on 2009-02-08
You are not alone. I am wondering if the good folks at Ubuntu will be releasing an update to correct this?

I've tried all the suggestions in the forums, to no avail.

---

### Post by nurazizah on 2009-02-12
I have the same problem. Wired network just stopped working after updates. or maybe it never worked at all because i update using the wireless. but after updating, the "wired networks" in the network manager menu disappears. There's only the "wireless networks".

---

### Post by nurazizah on 2009-02-13
I've found something that might be the source of my problems. Just would like to share with others who are using MadWifi.

It is said here [http://wiki.debian.org/DebianAcerOne](http://wiki.debian.org/DebianAcerOne) that 

"A little note about WiFi and network-manager: It has been observed that network-manager does not work properly with the updated MadWiFi driver (incompatible hal, perhaps). You may need to configure the WLAN (e.g. ESSID, WEP/WPA) manually. Alternatively, wicd is performing beautifully for me."

So am trying wicd when I get back. Hopefully this'll work.

---

### Post by Lucrothe on 2009-03-02
Hello,

Kinda a first time Linux user here, so go easy on me!

I’m also experiencing similar problems as described above. I just did a clean install of 8.10 from a CD. After the install, the ethernet port (eth0) was working properly. 

I was able to go online, and then after a few minutes - baam it said 260 updates! So, as the Ubuntu noob I am, I go ahead and do the updates. I reboot the system like advised by the installer, and then the ethernet port no longer works.

I've tried setting a static IP, and that doesn't work either.

The Wi-Fi (eth1) is working properly.

I have a Dell Mini 9, 64bg SSH, 2 GB RAM, and Bluetooth. 

Anyone have any suggestions about fixing this?

Thanks in advance!

---

### Post by versai on 2009-03-03
yep, exactly the same for me. dell mini 9, 64gb, 2gb ram, blue. having same issues with wired, wireless works flawlessly. dual boot xp (itunes, iphone, bah apple :( gimme drivers) xp works fine. know it's not the hardware.

versai

---

### Post by ironblossom on 2009-03-04
i got a Realtek chipset........facing the same problem
attached 2 screenshots which shows the output of *ifconfig* and *sudo etc/init.d/networking restart*



[ATTACH]105276[/ATTACH]

[ATTACH]105277[/ATTACH]

im a newbie on linux help me out plz

---

### Post by ironblossom on 2009-03-04
> **The Cog said:**
> I think that network-manager is supposed to ignore any interfaces that have configuration entries in the file /etc/network/interfaces. This may be why it is ignoring eth0. The only 2 lines you should have in there are:

network-manager seems to be very problematic in Intrepid. I recommend installing **wicd** instead. This can be downloaded from [http://wicd.sourceforge.net](http://wicd.sourceforge.net) . I couldn't make their install instructions work, so I downloaded the .deb file from here [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573) and double-clicked the file in nautilus to install it. Works a treat!
i tried WICD 
first i shows its stutus: CONFLICT WITH OTHER PROGRAM NETWORK MANGER INSTALLED IN YOU SYSTEM
then i unstalled NM, then reboot and try the WCID again, but the same status appears.
what to do now?

---

### Post by Kristopher on 2009-03-04
Noticed that there was a NetworkManger update today...still not fixed. :(

---

### Post by snebtor on 2009-03-05
I had the same problem in ubuntu studio 8.10 and wicd worked. Follow instructions in [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and then on synaptic package manager uninstall network manager-gnome and network manager. then instal wicd.

---

### Post by odium1 on 2009-03-05
what kernel is everyone running? type this in and post the result:
```
uname -a
```

there's a problem with kernel 2.6.27-11 that affects the wired networking.. it usually happens to people with (by what i've seen and personal experience) broadcom chipsets (dell mainly) and the fix i found worked really well. i downloaded KernelCheck and tells you what kernel you're currently running and you can also get it to tell you what the latest stable kernel is *and* you can get it to download the latest kernel, compile it and install it for you. i had it download and install 2.6.28-4 and it worked just fine. i did this to a few more dell machines that were experiencing the problem after the 230+ updates following 8.10 install and it worked for every one of them. hope all works out well.

cheers!

---

### Post by mangasan on 2009-03-06
I can confirm that chidge's workaround has worked fine also for me.
The /etc/network/interfaces must be cleaned in order to have only two entries.

```

auto lo
iface lo inet loopback

```

My kernel at the moment is 

2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

cheers.

---

### Post by Runaway1956 on 2009-03-09
> **The Cog said:**
> I think that network-manager is supposed to ignore any interfaces that have configuration entries in the file /etc/network/interfaces. This may be why it is ignoring eth0. The only 2 lines you should have in there are:

network-manager seems to be very problematic in Intrepid. I recommend installing **wicd** instead. This can be downloaded from [http://wicd.sourceforge.net](http://wicd.sourceforge.net) . I couldn't make their install instructions work, so I downloaded the .deb file from here [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573) and double-clicked the file in nautilus to install it. Works a treat!


My problem was self-induced - but your post solved it.  Many thanks!!

(reminder to self: don't tamper with stuff you don't understand, you idjit!!)

Imagine the feeling of everyone in the house having internet via internet connection sharing THROUGH YOUR MACHINE, but you have no internet!!  Talk about wierd!!

---

### Post by timmahhny on 2009-04-30
I was running 8.10, which ran fine at first. Then after update, I could not connect to the internet, yet I can connect to the network. I would ping the router, then I would be able to connect, but that would only last a few minutes, after which I would not be able to connect to the internet, yet network would be fine. 
 I got tired of trying to do anything, uninstalled Ubuntu. I reinstalled 8.10 had the same problem. I downloaded 9.04 and that seemed to work from CD, so I installed that, but again, can't connect to the internet, only router. I mess around with things, and can connect, but it doesn't last very long. 
 I also can't use wired, which worked fine before, but not any more. 
 Any suggestions, let me know.
Thanks

---

### Post by napzilla on 2009-04-30
Ditto here. I'm also using a wired connection on a stationary machine. I was just going to ignore it, but then I found that it's causing Firefox to start up with the "Work Offline" option checked. I'll try removing network-manager to see if that resolves the issue. Come to think of it, I forget why I had it on there to begin with... :confused:

Yep, getting rid of network-manager solved the problem. It also got rid of the silly icon.

---

### Post by timmahhny on 2009-04-30
> **napzilla said:**
> Ditto here. I'm also using a wired connection on a stationary machine. I was just going to ignore it, but then I found that it's causing Firefox to start up with the "Work Offline" option checked. I'll try removing network-manager to see if that resolves the issue. Come to think of it, I forget why I had it on there to begin with... :confused:

This is what I have found that sort of works for me. 
Go to Admin, then network tools. I have placed a shortcut on the desktop. I then ping my router, then will see if firefox or Opera work. If not, I use the port scanner and that typically works. 
 Right now I am redoing my laptop hard drive, since I placed Windows 7 Beta on it with Ubuntu, but just going to get rid of Windows 7, which I like by the way. 
 See if the network tools will help you out and I have no clue why. 
 Timmahhny

---

### Post by mittwit on 2009-08-12
I had wicd on my laptop as it was good for wifi then I noticed on another laptop that was running 9.04 the great connection tool for 3G usb modems that Network Manager has so I thought I would switch back.
I installed Network Manager and uninstalled wicd and network-admin but Network manager would only do the 3G connection.

I came here and read this:

> it depends of the switch in the file
Code:

/etc/NetworkManager/nm-system-settings.conf

that is
Code:

[ifupdown]
managed={true,false}

true=let NM rule.
false=let ifup/ifdown rule.

This worked for me, well not completely tested, but the red x is gone and Network Manager seems to be in control. My eth0 is connected, haven't tested wlan0 yet but I see Network Manager now has a "connect to hidden wireless" option which is good.

Thanks

---

### Post by richmarks20 on 2011-07-13
Suggest look at [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606").

---

### Post by TheSnowSnake on 2012-01-02
Add my to the list just upgraded and lost my wired connection, But have a plug in usb wireless adaptor so still rockin....

---

### Post by zika on 2012-01-02
> **TheSnowSnake said:**
> Add my to the list just upgraded and lost my wired connection, But have a plug in usb wireless adaptor so still rockin....You still have 8.10?

---

