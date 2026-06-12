---
title: "Can't connect to internet on Intel Motherboard!"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by solis88 on 2009-04-17
Hello everyone I decided to build a new computer and chose to install  a fresh copy of Ubuntu 8.10 64-bit. The only problem I have now is not being able to connect to the internet.  I'm using an Intel DP45SG Motherboard with the Intel 82567LF LAN chipset. I'm using a DSL connection where no username/pass is required. It's just one of those connections where when I connect the ethernet cable into the back of the computer, you wait a few seconds and you're online. I know the internet is working because when I reconnect to my other computer (running windows XP home) it works just fine. When I connect my dsl model into the ethernet port of my new Intel motherboard, I can see the little computers on top of my Ubuntu desktop turn to 2 arrows as it tries to find the network to connect to the internet. After about a minute it just says it can't connect to the network. I know it has something to do with the Motherboard's LAN not have the driver for Ubunto unless I'm way off and it's something  more technical. I really want to like Linux but these things aren't making it easy. Any help would be greatly appreciated.

P.S. I'm not familiar at ALL with any type of Linux code talk or other things. I'm just barely learning today actually but I'd rather use Linux than Windows Vista. Thanks.

---

### Post by solis88 on 2009-04-17
Any help here? I really am looking to using Linux. If this doesn't work I'll have to buy a windows CD. bleh

I've tried everything but can't figure out why it's not connecting to the internet on a working DSL connection.

---

### Post by DGortze380 on 2009-04-17
Who is your ISP (Internet Service Provider) because DSL is almost always a PPPoE connection, thus requiring a username and password. 

Purhaps the username and password are saved in Windows and that's why it connects correctly?

Please open a terminal (Applications -> Accessories -> Terminal)

Enter the following command and press enter. It will ask you for a password, type your password and press enter (NOTHING will show on the screen while you type).

```

sudo apt-get install pppoeconf

```

post the results here.

---

### Post by chili555 on 2009-04-17
If you Google/linux for '82567LF' you will see two things: bug and patch. It seems that the NIC is so new that support is not built in to the driver, *e1000e.* That means you can insert the driver module, but it doesn't recognize that it belongs to your 82567LF NIC and doesn't do anything. There is a later version of e1000e that might help: [http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=272252&release_id=669479](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=272252&release_id=669479)

You can download it to a USB key and transfer it to your Ubuntu machine. Download it to your Desktop. Then right-click it and select extract here. A folder will be created called e1000e-0.5.18.3. Then open a terminal and type:```
cd e1000e-0.5.18.3/src
sudo make install
```With any luck, it will install with no errors, although, when I installed it, I got a complaint about 'man pages.' Not really a deal breaker.

Then type:```
sudo rmmod -f e1000e
sudo modprobe e1000e
ifconfig
```Do you see a shiny new interface, eth0 perhaps? If so, you should be able to click the networking icon and request that you be connected.

---

### Post by solis88 on 2009-04-17
Wow thanks for the help! I googled for those drivers but I couldn't make or tails of what was what.

I'll download it now and try it on the new machine.

btw, no user/pass required for my connection.

---

### Post by wsonar on 2009-04-17
Most likely your ISP has the MAC address of your modem so you shouldn't worry about authentication

---

### Post by solis88 on 2009-04-17
> **chili555 said:**
> If you Google/linux for '82567LF' you will see two things: bug and patch. It seems that the NIC is so new that support is not built in to the driver, *e1000e.* That means you can insert the driver module, but it doesn't recognize that it belongs to your 82567LF NIC and doesn't do anything. There is a later version of e1000e that might help: [http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=272252&release_id=669479](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=272252&release_id=669479)

You can download it to a USB key and transfer it to your Ubuntu machine. Download it to your Desktop. Then right-click it and select extract here. A folder will be created called e1000e-0.5.18.3. Then open a terminal and type:```
cd e1000e-0.5.18.3/src
sudo make install
```With any luck, it will install with no errors, although, when I installed it, I got a complaint about 'man pages.' Not really a deal breaker.

Then type:```
sudo rmmod -f e1000e
sudo modprobe e1000e
ifconfig
```Do you see a shiny new interface, eth0 perhaps? If so, you should be able to click the networking icon and request that you be connected.

I just tried to install the driver onto my new machine. Everything seemed to work fine when I extracted and opened the terminal. When I type the code, I type cd e1000-0.5.18.3/src then I press enter.
Then I get a line that says "bash: cd: e1000e-0.5.18.3/src: No such file or directory. But it IS sitting there on my desktop.
Well, I ignored that and typed sudo make install after the "username@username-desktop:"
Then it asked for my admin password I use when I log onto Ubuntu. I typed that in and I got:

make: *** No rule to make target  'install'. Stop.


What's that about????

Oh and wsonar you're right: When I check the settings on my network settings I see "auto etho" I go to edit and see that there's already a Mac address in there.

---

### Post by DGortze380 on 2009-04-17
> **solis88 said:**
> I just tried to install the driver onto my new machine. Everything seemed to work fine when I extracted and opened the terminal. When I type the code, I type cd e1000-0.5.18.3/src then I press enter.
Then I get a line that says "bash: cd: e1000e-0.5.18.3/src: No such file or directory. But it IS sitting there on my desktop.
Well, I ignored that and typed sudo make install after the "username@username-desktop:"
Then it asked for my admin password I use when I log onto Ubuntu. I typed that in and I got:

make: *** No rule to make target  'install'. Stop.


What's that about????


Try this instead
```

cd Desktop/e1000-0.5.18.3/src

sudo make install

```

> **solis88 said:**
> 
Oh and wsonar you're right: When I check the settings on my network settings I see "auto etho" I go to edit and see that there's already a Mac address in there.

That's different.

---

### Post by solis88 on 2009-04-17
> **DGortze380 said:**
> Try this instead
```

cd Desktop/e1000-0.5.18.3/src

sudo make install

```



That's different.

I have my new machine on here so I'm trying it all right away. When I typed "desktop" in the code it asked me again for my password. I typed it in but nothing showed up? I just typed it and I didn't see the password or even those black circles that appear for every letter typed in the password to hide it. Well, I typed it anyway, pressed  enter and it said the same thing:
No rule to make target 'install'. Stop.

This is very strange.

Edit:

Ok got it to work. it was supposed to have Desktop/e1000(e) <---- that extra e  was supposed to go in there. 
@ the very end of the install  I see a "cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode e1000e.

Is that something to worry about?

---

### Post by solis88 on 2009-04-17
Well, I installed the driver it seems then put in the code:

sudo rmmod -f e1000e
sudo modprobe e1000e
ifconfig

I got a bunch of code that I really don't understand but left it like that anyway. I connected the ethernet cable and then I could see it trying to connect. It showed 2 green  circles with some type of comet swirling  in a circle. At the end it said it disconnected from the network. So I'm thinking it's not going to work. Is this why people say linux sucks? lol

---

### Post by chili555 on 2009-04-17
> Is this why people say linux sucks?They say it for a variety of reasons, either because they are not willing to do a bit of work to set something up or they think everything should be in a neatly wrapped GUI window or because they think everything should work for everybody all the time. I have answered posts like yours, concerning NICs or other equipment that came out very recently and for which there is not yet any working module, or some ancient ancient PCMCIA card that was old twenty years ago and for which Linux dropped the driver from the kernel years ago. Sure enough, the one remaining card owner comes on the forum and begs to get it working!

Please do these commands:```
sudo /etc/init.d/NetworkManager stop
ifconfig > ifconfig.txt
sudo ethtool eth0 > ethtool.txt
sudo dhclient eth0 > dhclient.txt
```Please put the three .txt files on your USB key and transfer them to a machine where you can post them here.> I see a "cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode e1000e. Is that something to worry about? Nope.> I didn't see the password or even those black circles that appearNo indication of your password appears in the terminal for security reasons. That's normal.

---

### Post by solis88 on 2009-04-17
> **chili555 said:**
> They say it for a variety of reasons, either because they are not willing to do a bit of work to set something up or they think everything should be in a neatly wrapped GUI window or because they think everything should work for everybody all the time. I have answered posts like yours, concerning NICs or other equipment that came out very recently and for which there is not yet any working module, or some ancient ancient PCMCIA card that was old twenty years ago and for which Linux dropped the driver from the kernel years ago. Sure enough, the one remaining card owner comes on the forum and begs to get it working!

Please do these commands:```
sudo /etc/init.d/NetworkManager stop
ifconfig > ifconfig.txt
sudo ethtool eth0 > ethtool.txt
sudo dhclient eth0 > dhclient.txt
```Please put the three .txt files on your USB key and transfer them to a machine where you can post them here.Nope.No indication of your password appears in the terminal for security reasons. That's normal.

Hey thanks for your help. I did a google on that motherboard and ethernet and it seems that ubuntu 64-bit doesn't support that ethernet port. It was written back in Oct of 2008 so I'm sure things have changed. Anyway, here is what my terminal showed when I typed in those commands:

user@user-desktop:~$ sudo /etc/init.d/NetworkManager stop
 * Stopping NetworkManager...                   [OK]
user@user-desktop:~$ ifconfig > ifconfig.txt
user@user-desktop:~$ sudo ethtool eth0 > ethtool.txt
sudo: ethtool: command not found
user@user-desktop:~$ sudo dhclient eth0 > dhclient.txt
There is already a pid file /var/run/dhclient.pid with pid 9061
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1c:c0:90:01:22
Sending on   LPF/eth0/00:1c:c0:90:01:22
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@user-desktop:~$

---

### Post by solis88 on 2009-04-17
Any insight on the problem there?

---

### Post by solis88 on 2009-04-17
Well I've been reading reviews from people familiar with my particular motherboard and it seems that Ubuntu just doesn't have the drivers to recognize the motherboard's Ethernet port. Basically, any new motherboard (for the time being) will be useless with Linux if you plan on going online. I guess if you can't go online all you have is a very expensive calculator and word processor. Well, that's the end of that. At least Win XP is still selling and better than Vista.

---

### Post by DGortze380 on 2009-04-17
> **solis88 said:**
> Well I've been reading reviews from people familiar with my particular motherboard and it seems that Ubuntu just doesn't have the drivers to recognize the motherboard's Ethernet port. Basically, any new motherboard (for the time being) will be useless with Linux if you plan on going online. I guess if you can't go online all you have is a very expensive calculator and word processor. Well, that's the end of that. At least Win XP is still selling and better than Vista.

You can buy and install a PCI NIC for like $10...

---

