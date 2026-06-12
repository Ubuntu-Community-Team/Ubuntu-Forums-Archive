---
title: "Sharing net from windows desktop to ubuntu laptop?"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by johnnydotexe on 2009-08-19
I have my IBM ThinkPad z61m loaded with Ubuntu 9.04, first time user.  Sometimes the Ubuntu network manager automatically finds and establishes the cat5 crossover cable connection to my windows-desktop's ethernet card, and sometimes it doesn't.  When it doesn't connect, or when it does and I end the connection, I can't reconnect at all.  In order to reconnect, I have to reboot the windows-desktop.  This is HUGE inconvenience, having to reboot the windows-desktop each time I want to get the ethernet connection between it and the ubuntu-laptop working so I can get online with the laptop using my desktop's active internet connection.

In the TCP/IP properties on the windows-desktop, the IP is set to 192.168.0.1 and the Subnet Mask is set to 255.255.255.0, the DNS and Gateway fields are empty.  Internet connection sharing is enabled.

The settings on the ubuntulaptop network manager are...

Connection Name = Shared
Connect Automatically = Yes
MAC Address = 00:16:36:71:FB:87
MTU = Automatic
802.1x Security = No
Method = Automatic (DHCP)
Addresses = None
DHCP Client ID = None
Routes = IP 192.168.0.1 / Netmask 255.255.255.0

I also tried the following settings in the ubuntu-laptop's network manager, which instantly establish the LAN connection but won't allow the internet to work on the laptop...

Connection Name = Shared
Connect Automatically = Yes
MAC Address = 00:16:36:71:FB:87
MTU = Automatic
802.1x Security = No
Method = Manual
Addresses = IP 192.168.0.1 / Netmask 255.255.255.0 / Gateway (what IP config on the desktop shows under the internet addresses, Gateway and IP are the same in there)
DHCP Client ID = None
Routes = None

Does anyone notice anything obviously wrong with the settings above?  Does anything need to be changed, set, etc on the ubuntu-laptop or windows-desktop?

I'm also wondering if it would be a better/easier idea to just buy a wireless adapter card for the windows-desktop, since my ubuntu-laptop has the integrated Intel PRO/Wireless 3945abg adapter, and just connect the two that way.   Is that possible?  Is it easy to set up?  Would it be more reliable than my current ethernet/cat5 crossover connection?  Could I still share the internet from the windows-desktop to the ubuntu-laptop over that wireless connection?  My ubuntu-laptop's wireless adapter is recognized by ubuntu, but I have no known way to test it since there's no wifi hotspots near me and I have no other computers in the house with wireless cards.  If going the wireless route is a better/easier/more reliable answer to what I need to do, I can buy the wireless adapter card for the windows-desktop tonight from my local wally world.  I believe they sell Belkins and Linksys.

EDIT:  I get online with the desktop via tethering.  I hook my Alltel Blackberry Pearl 8130 up to the windows-desktop via USB, and use the Alltel-supplied program to "dial-up" through my phone to the Alltel data network.  It dials #777, using my 10digit number as the username and no password.  Bluetooth dial-up does this as well, minus the USB cable obviously.  There are no routers or anything like that involved, just my phone and the USB cable or bluetooth connection.

---

### Post by tripolitan on 2009-08-19
sudo gedit /etc/network/interfaces

it should look something like this:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.10 (or_any_number_other_than_192.168.0.1)
netmask 255.255.255.0
gateway 192.168.0.1 (IP_number_of_desktop)
auto eth0

---

### Post by johnnydotexe on 2009-08-19
I ran...

```
sudo gedit /etc/network/interfaces
```in terminal, it opened a new window that said...

```
auto lo
iface lo inet loopback
```Do I input what you wrote in to that and save it?  Does it matter if I deleted "Auto eth0" from the Network Manager, and created my own connection called "Shared" with the same settings that "Auto eth0" had?  I noticed you had "Auto eth0" in what you posted, so I figured I'd mention that.

Also, I *think* I just discovered something.  I couldn't get the LAN/net to work with the first set of settings in my first post, it usually randomly works when it wants to.  After several laptop reboots, still nothing.  I shut down the laptop and the desktop to go eat dinner, came back, booted both up...it works, I'm currently posting this from the laptop.  I *think* my desktop rebooting is what fixed it.  What could this mean?

EDIT:  I disconnected the connection, and added the following to the interfaces file...

```
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
Shared
```and deleted the IP 192.168.0.1 and Netmask 255.255.255.0 from Routes in the IPv4 tab of the edit connection window for network manager.  Couldn't reconnect.  Put everything back to the way I had it, still can't reconnect.  I'll reboot the windows-desktop to see if that fixes not being able to connect.

EDIT2:  Rebooted the windows-desktop, left-clicked the network manager on the ubuntu-laptop and it connected...so rebooting my windows-desktop fixes the no-connection issue, but I still need to find out exactly what causes that issue because I shouldn't have to reboot my windows-desktop each time I want to connect the two together.  This was with my first set of settings in the first post, by the way.  I could try yours again, but do I need to change anything in the connection edit area, like remove the Routes I set or anything?  And do my settings in the above code tags look correct for my setup?

Edited first post to show the new info I came across and etc.

---

### Post by johnnydotexe on 2009-08-19
Just tried this fix...

[http://ubuntuforums.org/showpost.php?p=7280398&postcount=3](http://ubuntuforums.org/showpost.php?p=7280398&postcount=3)

and it didn't work, so I put the file back to the way it was before the edit.

The connection was working until I disabled networking, then turned networking back on and it will not reconnect which means the windows-desktop needs to be rebooted for it to work again.  This is becoming a huge headache having to reboot the windows-desktop each time I want the two computers connected, will doing this with a wireless connection work better, like I had mentioned at the bottom of the first post?

Can anyone help me figure this out?

---

### Post by johnnydotexe on 2009-08-20
Still trying to get this working, could really use the help. :(

---

### Post by tripolitan on 2009-08-20
Start by turning off the windows-desktop

1-Now, for this exercise, please stop using Network Mangler all together, don't even open it's window. On my Linux machines, it is the first piece of ....software that gets removed but that is based strictly on my own experience.

2-Edit your /etc/network/interfaces exactly as I mentioned, not as you posted above. (yes, remove "shared" because eth0 is NOT shared and must put back auto eth0, because you want eth0 to start upon reboot. You must save this file.

your interfaces file, again, should look like 

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

once the file is saved, make sure the crossover cable is physically connected (unplug then plug back in)

3-turn OFF the ubuntu machine.
4-Start your Windows machine that is configured to share its internet connection (wait a good 10 minutes)
5-Start Ubuntu. (that's all, stop messing with Ubuntu at this point, you don't need to restart/reboot anything)
You should be able to normally shutdown your Ubuntu laptop and restart without having to go through any hoops.

If you are still having problems connecting, mention the exact circumstances (assuming you're using Firfox to connect to the Internet?), post the output of the command "route" and while you wait for an answer, re-evaluate your network topography starting and ending at the Windows-desktop (don't mess with Ubuntu).

List all the computers that connect to this desktop(if any), with their IP addresses and the IP address of the desktop computer and finally, how is the windows-ddesktop connected to the Internet and what is its IP address that is provided to it by the provider/router (only list it if it starts with 192.168 or 10. ) no info is useless info.

---

### Post by johnnydotexe on 2009-08-20
I connect to the internet on my windows-desktop by connecting my Alltel Blackberry Pearl 8130 to it via USB cable, I then use the Alltel Axcess dial-up program to access the net.  Basically it dials #777 through my phone, using my 10digit number as my username and no password.  That connects me to the 1XEV/CDMA Alltel data network.  I can also do this on the laptop using Berry4All, but when I am home the windows-desktop has priority over the laptop because it has all my stuff on it, my games, etc.  Hence the reason for needing this LAN/shared net connection to work between the windows-desktop and the ubuntu-laptop, so I can be online with both at the same time.  No other computers are involved in this "network" of mine, just the windows-desktop and ubuntu-laptop.

I followed your steps, windows-desktop is turned on and online which is where I am currently posting from, just turned the ubuntu-laptop on and it is loaded/at desktop.  The windows-desktop recognizes the LAN connection now that the ubuntu-laptop is on, but the ubuntu-laptop shows no active connection...so if editing that file was supposed to automatically connect/establish the LAN, it did not.  I confirmed this by viewing the NM icon in the ubuntu tray(didn't touch NM), by opening Firefox and trying to access various pages, and by trying to start PigdinIM.

When submitting "route" in to the terminal on the ubuntu-laptop while the cat5 crossover is connecting it to the windows-desktop(with the connection not working on the ubuntu-laptop currently) and the windows-desktop is powered-on and online, this is what's displayed...

```

Kernel IP routing table
Destination       Gateway           Genmask            Flags    Metric   Ref   Use  Iface
192.168.0.0      *                   255.255.255.0     U         0        0      0     eth0
link-local       *                   255.255.0.0        U        1000     0      0     eth0
default           192.168.0.1       0.0.0.0             UG      100       0      0     eth0

```

On the windows-desktop, Internet Sharing is enabled.  If you go to Network Connections, then right-click the Local Area Connection 1 and go to properties, then go to TCP/IP properties...it is set to "Use the following IP Address automatically" with the IP set to 192.168.0.1 and the Subnet mask set to 255.255.255.0.  Default Gateway is blank.  Due to the above option "Use the following IP Address automatically" being checked, "Use the following DNS server addresses" is automatically checked and won't allow itself to be changed to "Obtain DNS server address automatically" , and the Preferred DNS server and Alternate DNS server fields are blank.

When submitting "ipconfig" in to the command prompt on the windows-desktop, while online and while connected via cat5 crossover to the ubuntu-laptop(with the connection not working on the ubuntu-laptop currently), this is what's displayed(the Internet IP and Gateway change each time I connect to the net)...

```

Ethernet adapter Local Area Connection 1:

Connection-specific DNS suffix . :
IP Address. . . . . . . . . . . . . . . . : 192.168.0.1
Subnet Mask. . . . . . . . . . . . . . .: 255.255.255.0
Default Gateway. . . . . . . . . . . . :

PPP adapter Axcess Mobilelink:

Connection-specific DNS suffix . :
IP Address. . . . . . . . . . . . . . . . : 174.43.23.157
Subnet Mask. . . . . . . . . . . . . . .: 255.255.255.255
Default Gateway. . . . . . . . . . . . : 174.43.23.157

```

I just now left-clicked the NM icon on the ubuntu-laptop to see if there were even any connections under wired, none exist.  I then right-clicked the NM icon and went to Edit Connections...none exist under wired, even though I created one called "Shared" in there yesterday.  I didn't touch anything, didn't change anything on either computer other than the interface file on the ubuntu-laptop like you had instructed.

If I unplug the cat5 crossover cable from the ubuntu-laptop, restart the ubuntu-laptop or shut it down completely...the windows-desktop does notify me that the connection was lost, and then notified me when the connection is regained once the cable is plugged back in or the ubuntu-laptop turned back on.  It has always done this, but I figured it was worth mentioning.

If it matters any, the Intel PRO/Wireless DOES work on this ubuntu-laptop.  I was in town earlier in the McDonalds parking lot leeching their wifi.  Network Mananger kept itself current in regards to scanning for available networks, connected to them without any hassle.  Wifi-Radar scanned for networks and found them easily, but when trying to connect it would take forever to establish an IP and then would "connect without IP", and the net wouldn't work.  I may have to adjust some of the settings on Wifi-Radar, I'll mess with it tomorrow.  I would much rather use it, and try to rid of NM.

If you need any more info, just lemme know.  I've got all day to tinker with this thing.

---

### Post by johnnydotexe on 2009-08-21
Still needing help with this.

Have to find out why the ubuntu-laptop sometimes establishes the LAN on startup, and sometimes doesn't which requires the windows-desktop to be rebooted for it to work for some reason that is beyond me.  When the LAN is established, it will run and net will work on the ubuntu-laptop without any issues as long as I want it to unless I shut down the laptop or disconnect the LAN.

---

### Post by johnnydotexe on 2009-08-21
Anyone?

---

### Post by johnnydotexe on 2009-08-22
Still no luck getting this ethernet connection working properly, could really use some advice.

Would I be better off going wireless?  This laptop has the Intel/PRO Wireless adapter and it does work, does connect to wifi and home wireless networks just fine.  What piece of equipment would I need to install in the windows-desktop?  Wireless router or wireless card/usb adapter?  Keep in mind the way I connect to the net on the desktop, doesn't involve a router or modem, just my Blackberry.

---

### Post by johnnydotexe on 2009-08-23
No one on here has ever set up a LAN on ubuntu before? :confused: :(

---

### Post by johnnydotexe on 2009-08-23
Went back to Windows XP.  Over a week to still not be able to set up something on a Linux OS that takes 15 seconds on Windows OS is un-acceptable.

/endthread.

---

### Post by Nyoro on 2009-08-24
Your setup is NOT simple lan, it is windows xp ICS, which means your XP box needs to be routing and natting traffic from the LAN. And of top of this you add USB networking via wireless device? Thats a pretty complex setup. You can't expect to have this work without jumping through some hoops. 

The following article outlines a bug in the ICS service that fits your described problem quite well. It was introduced with SP3 (and apparently it is not scheduled to be fixed). I suggest trying to restart the service next time you run into the problem (see the article for instructions). At the least restarting the service is quicker than rebooting your computer.


[http://support.microsoft.com/kb/951446](http://support.microsoft.com/kb/951446)

---

### Post by johnnydotexe on 2009-08-24
It does sound similar, but the problem is the connection will work sometimes and not work other times without any settings being changed, no cables touched, etc.  Just works when it wants to, so I was hopping that meant it was something that could possibly be fixed.

Will going wireless for this connection fix the issue?  If so, what kind of wireless hardware would I need on the windows-desktop?

---

### Post by tripolitan on 2009-08-24
> **johnnydotexe said:**
> When the LAN is established, it will run and net will work on the ubuntu-laptop without any issues as long as I want it to unless I shut down the laptop or disconnect the LAN.

As far as network connections are concerned, shutting down the laptop=physical disconnect.

Thanks to Nyoro for the link below, I would have banged my head against several walls before arriving at that. Evidently, this is a Windows issue, changing the hardware to wireless will not fix it.

---

### Post by johnnydotexe on 2009-08-24
I think I have arrived at that above windows article actually being what's wrong here.  Unfortunately(Read: Fortunately) the LAN connection has been working fine today so I haven't been able to see if the problem fits that article.

Once the connection stops working and won't reconnect, I'll run those two commands in the run window on the windows-desktop and see if that fixes it.  If it does, we finally know what's wrong.  I may go back to SP2 if that's the case, or SP1.  Windows security is garbage anyways.

---

### Post by Nyoro on 2009-08-25
I hope it works out for you, poking the same problems for long periods does get annoying.

---

### Post by johnnydotexe on 2009-08-25
Now the LAN is working, and now I'm dual-booting Ubuntu on the laptop next to XP Pro.  Wtf?

Oh well, I'm not complaining...even though the problem did mysteriously fix itself. :)

---

