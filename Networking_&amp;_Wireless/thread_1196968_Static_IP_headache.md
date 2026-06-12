---
title: "Static IP headache"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by xi_Slick_ix on 2009-06-25
Trying to set up static IP on my desktop running 8.10.  Using it as a network share through samba so my xbox running xbmc can connect to it.  I've had success on the windows side getting this to work, and have almost everything right on the Linux side, except for the damn static IP.

I've tried editing the /etc/network/interfaces.  That successfully would chance the IP address during that session (such as during that session I successfully streamed media and was also able to view files across the network from my laptop running windows at the time), but upon reset, it bombs, and will not connect to the network, with the little caution symbol by the networking logo.

```
auto lo
iface lo inet loopback
```
-Default settings

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```
-What I changed it to.

When this failed to connect to the network, I deleted my changes and set it back to DHCP

After this headache, and the having multiple swap files pop up for the /etc/network/interfaces and fighting to delete them, I thought I might try the GUI side instead.  So I manually added 'Network' to the Administration menu, and opened up Network Settings.  Tried changing eth0 to a static IP that way.  It says the changes are successful, but upon using 'ifconfig' is shows the IP address is 192.168.1.3 and not .8.

If this is some error associated with 8.10 please let me know, and it seems I've caught glimpse and pieces of this murmur associated with 8.10.  If 9.04 doesn't suffer from this, I would probably upgrade on the spot.  If there's a more simple work around to make DHCP stop trying to take control that's great too

Any help is greatly appreciated!!

---

### Post by wojox on 2009-06-25
check this link out [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by jonobr on 2009-06-25
I was having network manager problems, so as far as I recall, I got tired of it and stopped it controlling my ethernet devices

If I recall it was in 
/etc/NetworkManager/nm-system-settings.conf 
and I set the following 

[ifupdown]
managed=false

(it was true)

I control things the old fashioned way using hostname routes, resolv,conf and so on.

Thanks

---

### Post by xi_Slick_ix on 2009-06-25
Tried the ubuntu geek method - this didn't seem to work

**NOTE**
I'm concerned 'Network Settings' under administration could be interfering.  eth0 has a check box by it and has the same settings as I was trying to implement for the static IP, but I assume this _could_ be creating an argument somewhere. 
**ENDNOTE**

When I have the restart network command, this is what I got:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4249
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:01:29:fc:a7:c6
Sending on   LPF/eth0/00:01:29:fc:a7:c6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
                                                                         [ OK ]


```

I'll go out on a limb here and assume that isn't promising.. thanks for the suggestion though!

---

### Post by paul_be on 2009-06-25
You may be able to set a static IP in your router for the device(while keeping dhcp enabled)

My netgear lets me do this, which I find quite helpful.

---

### Post by xi_Slick_ix on 2009-06-25
Thanks - I'll see if I can do that - Really the only reason i need the static IP is for the sharing - so as long as assigning it from the router side does the same thing I'm fine with that.

---

### Post by xi_Slick_ix on 2009-06-25
So while following the guide from ubuntu geeks and removing network manager, it not appears that I don't have the ability to re-enable network connections - any idea how I can get back what used to be there?

---

### Post by paul_be on 2009-06-26
you should be able to reinstall using add/remove programs

---

### Post by xi_Slick_ix on 2009-06-26
> you should be able to reinstall using add/remove programs

Unfortunately not that easy - the remove command that was used ripped it out the kernel if I understand everything correctly - I'm working on recompiling one from debian at the moment.

---

### Post by snkiz on 2009-06-26
network manager and /etc/interfaces do not play nice together. AS you have seen. you have to use one or the other but not bloth. If you want to use /etc/ntwork/interfaces it should look somthing like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```
and network manager like this:
[IMG]http://cknet.thruhere.net/screenshots/static.png[/IMG]

---

### Post by KarlIvan on 2009-06-26
> keep what you had in the /etc/networks/interfaces when you first posted, and then put this into the command prompt: 
$ sudo chkconfig NetworkManager off
$ sudo chkconfig network on

it has to do with networkmanager, so kill that. chkconfig keeps networkmanager off until you retype the command and tell it to turn back on (sudo chkconfig NetworkManager on/// sudo chkconfig network off)(including reboot)

so keep your interfaces file the same, type those two commands into the command prompt, forget everything youve read thus far, reboot computer, find out that it works, post a reply saying thanks :) lolnm, that was for fedora i beleive

anyway, i dont think you need the network and broadcast address in there. just keep address, netmask and gateway

---

### Post by xi_Slick_ix on 2009-06-26
Well this is the code I put into the /etc/network/interfaces using sudo nano:
```
auto lo eth0
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

then the ```
sudo nano /etc/resolv.conf
``` to set the 'nameserver' (192.168.1.1)

and then told network services to restart ```
sudo /etc/init.d/networking restart)
``` which gave me this error message

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:4: interface eth0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:4: interface eth0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]


```

Any ideas?

---

### Post by Iowan on 2009-06-26
> **xi_Slick_ix said:**
> We
```
auto lo [COLOR="Red"]eth0[/COLOR]
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Get rid of one of the eth0 auto def's. That should fix the error message and might be why the file couldn't be read.

---

### Post by snkiz on 2009-06-26
> **Iowan said:**
> Get rid of one of the eth0 auto def's. That should fix the error message and might be why the file couldn't be read.

the auto lo needs to stay its for localhost get rid of the other one

---

### Post by Iowan on 2009-06-26
Yes, though I *meant* to refer only to the "eth0" entry, the highlight suggested otherwise.  I've edited it - delete one of the red entries. Thanks for pointing that out...

---

### Post by xi_Slick_ix on 2009-06-27
So I made the changes suggested to /etc/network/interfaces:

```
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

and then restarted networking

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
                                                                         [ OK ]
```

So that part didn't bark at me this time.. but I can't load websites and when I look for the desktop on the network from my laptop it doesn't see it.

---

### Post by snkiz on 2009-06-28
did you setup your name server? no dns then no internet. see ```
man resolv.conf
```

---

### Post by xi_Slick_ix on 2009-06-29
This issue will be put to the side short term - just got an Error 18 in grub earlier yesterday - So I'll be flashing my bios and praying a bit.

Thanks everyone who contributed so far - As soon as I boot into Ubuntu (any OS for that matter) I'll check the DNS, though I'm fairly certain I configured it to 192.168.1.1 as well.

---

### Post by Popaul on 2009-07-27
ifUpDown problems...
I got a similar problem I believe, after upgrading to 9.04. 
I am on fixed IP, only one ethernet card (on the mother board), but suddenly got 2 connections:
- one called eth0, that was blocked for editing, and called as 'ifupdown' when left clicking on Network Manager icon. This one was apparently the 'default'. It connected (got good ping return when testing IP addresses with their real numbers, but nothing when entering the lettered addresses like [www.google.com](www.google.com)), but I could not get anything from the web.
- second one called 'Wired connection 1': this one was editable, and when I switched to this one after left click on Network Manager, everything was fine. But I had to do that after every boot.
This happened on a DELL machine delivered with Ubuntu on it (8.04 if I remember), So nothing to do with the hardware I presume.

I recently got another machine, a little Samsung NC10. I installed partition (Win XP on one side, Ubuntu on the other), and Ubuntu was a dream (apart recording... need to fix that). So checked on this one how were the 2 files:
- /etc/NetworkManager/nm-system-settings.conf
- /etc/network/interfaces
and changed the same file on the DELL to the same: it works fine.
nm-system-settings.conf=
---------
[main]
plugins=ifupdown,keyfile

no-auto-default=(insert here the full MAC address you can find on right-clicking Network Manager/edit connections for the connection you want, the one that's editable, followed by a COMMA with no space),

[ifupdown]
managed=false
-----------

interfaces=
-----------
auto lo
iface lo inet loopback
-----------

nothing else.

Oooo... and by the way, it has 'cleaned my internet connection big time. Since I got the DELL, connection to web-sites etc... were always slow. Once on a site, no problem, but to get on one site there was always quite some times. I thought it was the DELL card... no! It was the config of Ubuntu... as this was slow with previous versions of Ubuntu.
Now that I have done these modif, real fast, as it should be.

---

### Post by snkiz on 2009-07-28
Your problem was a little different. First off in network manager Auto eth0 requires a dhcp server to supply ip and dns info. So your connection problems were because your router (or whatever your using for dhcp) wasn't configured correctly. Auto eth0 is a system wide setting so policy-kit should ask you for a password to edit it. Wired connection 1 is a user setting (no need for root) to edit, but it will not be available to other users on the system. Since you edited wired connection 1 you put in the ip and dns info so no need for a dhcp server. As for speed it can vary depending on witch dns server you use, time of day or hardware you connect with.

---

### Post by irv on 2009-07-28
After reading through all the posts in this thread, I see no one mentioned wicd network manager. I had trouble in 8.10 on my server so I switched to wicd and it removed gnome-network-manager and all my problems when away. I now use wicd on all my computers. Here is a screen shot of my server setup in wicd.
[IMG]http://wabasha-server.net/Screenshot.png[/IMG]

Here is my laptop.
[ATTACH]122723[/ATTACH]

---

### Post by snkiz on 2009-07-28
Gnome network-manager works fine if you understand it (most of the time). That said, wicd seems much simpler. One issue I do have with Gnome net.. is that it does not connect til you log in, playing hell with samba and various other services. Does wicd follow that behavior as well?

---

### Post by irv on 2009-07-28
> **snkiz said:**
> Gnome network-manager works fine if you understand it (most of the time). That said, wicd seems much simpler. One issue I do have with Gnome net.. is that it does not connect til you log in, playing hell with samba and various other services. Does wicd follow that behavior as well?
I believe it does, but I am not sure since I set it to login automatic. I will have to check net time I boot up. The automatic might be just starting the manager before the destop fully loads. I am not really sure. I know that as soon as I get the desktop it is login.

---

### Post by Popaul on 2009-07-31
snkiz
I have no idea about the dhcp, but the router cannot be configured I guess (it's a speedtouch). Anyway, the 'wiredconnection 1' I have finally is through the 'interface eth0', and I can edit it only through root (dialog box pupping up etc...). 
The 'old' eth0 connections was not, repeat not, editable: there was not box popping out to ask whatever. 
Regarding the speed, I changed no hardware, nothing at all but the settings I put in the post above. So yes, I would tend to believe that Ubuntu is not to blame, but DELL people who fixed the set-up of the 'inspiron 530 Ubuntu'... but I am sure they are getting better at it. After all Ubuntu is a new thing, while Windows has been around for 15 years.

---

### Post by xi_Slick_ix on 2009-08-02
I ended up upgrading to 9.04 yesterday, which reinstalled the networking utilities.  I'm able to give it a static IP through the gnome GUI, and thats working fine.

I'm aware this really doesn't resolve me problem, but I really ran out of options and time, so the upgrade method did what I needed it to.


I am having some issues getting samba properly configured, but I started another post for that.

Thanks everyone who replied, I appreciate your time & effort!

---

