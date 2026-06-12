---
title: "Network Configuration Problem in Xubuntu"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by user1111 on 2009-01-22
OK, I've just upgraded Xubuntu from 8.04 to 8.10. Now the network is not working (it was before). I normally connect to the internet through my LAN but Xubuntu is not connecting. I checked the included help on how to configure networking and it says to go to Applications -> System -> Network to do so but there is no "Network" entry under "System". What's going on, did the upgrade go wrong? Should I reinstall?

Luckily I also have a Windows system available to me so I used it to go to the Xubuntu site (and here) and there they have different instructions. There they say to go to System -> Administration -> Network to configure networking. Well, I don't have a "System" entry on my menu bar. So thinking that maybe what they actually meant was Applications -> System -> Administration -> Network, I tried to follow that path. But there is no "Administration" under "System" there. Again, what's going on? Did the upgrade mess up and do I need to reinstall to fix the menus?

There is an icon in the upper right of the screen that looks kind of like two computers next to each other with a red X on it. Left clicking on this icon pops up a box that lists my network card but clicking on it doesn't do anything. Under the listing for my card (Intel Ethernet Pro 100) it says "device is unmanaged". So this approach doesn't work either.

What am I doing wrong?

---

### Post by dmizer on 2009-01-22
> **user1111 said:**
> OK, I've just upgraded Xubuntu from 8.04 to 8.10. Now the network is not working (it was before). I normally connect to the internet through my LAN but Xubuntu is not connecting. I checked the included help on how to configure networking and it says to go to Applications -> System -> Network to do so but there is no "Network" entry under "System". What's going on, did the upgrade go wrong? Should I reinstall?

Luckily I also have a Windows system available to me so I used it to go to the Xubuntu site (and here) and there they have different instructions. There they say to go to System -> Administration -> Network to configure networking. Well, I don't have a "System" entry on my menu bar. So thinking that maybe what they actually meant was Applications -> System -> Administration -> Network, I tried to follow that path. But there is no "Administration" under "System" there. Again, what's going on? Did the upgrade mess up and do I need to reinstall to fix the menus?

There is an icon in the upper right of the screen that looks kind of like two computers next to each other with a red X on it. Left clicking on this icon pops up a box that lists my network card but clicking on it doesn't do anything. Under the listing for my card (Intel Ethernet Pro 100) it says "device is unmanaged". So this approach doesn't work either.

What am I doing wrong?

There should be a network manager applet on your panel in your notifications area. If you don't have a notifications area on your panel, right click on the panel to add one.

If that doesn't work, install gnome-network-admin via synaptic (you'll need the xubuntu install cd or internet access). Then you get the Applications -> System -> Administration -> Network

---

### Post by user1111 on 2009-01-22
> **dmizer said:**
> There should be a network manager applet on your panel in your notifications area. If you don't have a notifications area on your panel, right click on the panel to add one.
Clicking on the icon I described above and selecting "About" identifies it as NetworkManager Applet 0.7.0. It's there, it just doesn't seem to be of much use. One thing I find curious: Since Ubuntu wan't let you run as a superuser, how is NetworkManager supposed to make system network changes given that it never asks for a superuser password?

> If that doesn't work, install gnome-network-admin via synaptic (you'll need the xubuntu install cd or internet access). Then you get the Applications -> System -> Administration -> Network I don't have an install CD (I did a network upgrade as recommended) or internet access on it (now).

So far this is looking like multiple bugs rather than user error to me.

---

### Post by dmizer on 2009-01-22
> **user1111 said:**
> Clicking on the icon I described above and selecting "About" identifies it as NetworkManager Applet 0.7.0. It's there, it just doesn't seem to be of much use. One thing I find curious: Since Ubuntu wan't let you run as a superuser, how is NetworkManager supposed to make system network changes given that it never asks for a superuser password?
Ubuntu uses the sudo (or graphic gksudo) function to temporarily assign super user ability so administrative functions can be performed. You can also get a root prompt with the -i switch in sudo:
```
sudo -i
```

> **user1111 said:**
> I don't have an install CD (I did a network upgrade as recommended) or internet access on it (now).

So far this is looking like multiple bugs rather than user error to me.
If you're willing to work in the command line, it will probably be trivial to get you online. This probably isn't a bug. I simply haven't used network manager to connect to networks.

Are you trying to connect to a wired or wireless network?

---

### Post by user1111 on 2009-01-22
> **dmizer said:**
> Ubuntu uses the sudo (or graphic gksudo) function to temporarily assign super user ability so administrative functions can be performed.
I understand that. However, when most programs, such as the package manager, need SU they prompt for it. Not NetworkManager. Maybe Ubuntu doesn't require SU privileges for network configuration?
> If you're willing to work in the command line, it will probably be trivial to get you online. This probably isn't a bug. I simply haven't used network manager to connect to networks.  I would really rather learn what I'm doing wrong if it isn't a bug. If it's a bug with the GUI tools i'd rather learn how to fix that. Giving up on getting it to work right and going to the command line instead is not really the way I would like to go.
> Are you trying to connect to a wired or wireless network?
Wired, as I indicated above (Intel Ethernet Pro 100).

---

### Post by dmizer on 2009-01-22
I'm at work at the moment, but I'm on my way home in a few minutes.

Since I rarely play with network manager I'll need to look at it closely in Xubuntu. If no one else has any input for you, I'm planning to install Xubuntu Ibex in a virtual machine tonight.

---

### Post by dmizer on 2009-01-22
I knew something was telling me that you were using wired.

You're not using a static IP are you? Everything worked automatically for me.

---

### Post by user1111 on 2009-01-22
> **dmizer said:**
> I knew something was telling me that you were using wired.

You're not using a static IP are you? Everything worked automatically for me.

No, automatic (DHCP) configuration from my local router.

I went ahead and ran ifconfig from the command line to see if eth0 was being assigned an address and it was. However, any attempts to ping using host names results in "unknown host xxxxxxx". So I took a look at etc/resolv.conf. It has just one line in it which says
```
# Generated by NetworkManager
```
No name servers are listed. This same machine had no problems being configured from DHCP before the upgrade.

---

### Post by dmizer on 2009-01-22
I run into this problem quite frequently. Not sure why you're not getting DNS servers but the fix is fairly easy. Just take a look under the section labled "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:" here [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

---

### Post by user1111 on 2009-01-22
> **dmizer said:**
> I run into this problem quite frequently. Not sure why you're not getting DNS servers but the fix is fairly easy. Just take a look under the section labled "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:" here [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

Unfortunately, that's not really a fix. Their first step, gksudo network-admin, doesn't help much because "The program network-admin is currently not installed".

Their following steps are just a way of statically assigning OpenDNS servers. That doesn't do anything to fix fix the broken DHCP function.

I did a fresh install of Xubuntu under Windows on another machine and the NetworkManager had no problem recognizing the wired network connection. But it didn't have any problem doing so before the upgrade on the broken machine either.

So far, it still doesn't look to me like I'm doing anything wrong. Unless someone can show me otherwise, I'm going to file a bug report on this. I imagine it's probably some configuration that the upgrade process messed up but I'm not familiar enough with it to find it. While I appreciate your help, nobody here seems to be able to help me actually fix it. So, it's starting to look like the way to fix it is going to be to backup files, reformat the drive, reinstall, restore files and avoid following the recommendation of upgrading rather than reinstalling in the first place because the upgrade process seems to be broken.

Thanks again for your efforts.

---

### Post by Loosewheel on 2009-01-23
Hi user1111,
You should look at '/etc/network/interfaces' file. It should look like:

auto lo
iface lo inet loopback

Any other lines, (ie.auto eth0... should be commented out with '#'.
Also 'right click nm-applett, (the icon in the upper right),>Edit connections>Select the wired tab>Auto eth0,(highlite it)>Edit,(in the right pane)....and make sure to check the box 'Connect automatically'. And 'System setting' should be unchecked.
Then reboot and see if it comes up.

---

### Post by dmizer on 2009-01-23
> **user1111 said:**
> Unfortunately, that's not really a fix. Their first step, gksudo network-admin, doesn't help much because "The program network-admin is currently not installed".

Their following steps are just a way of statically assigning OpenDNS servers. That doesn't do anything to fix fix the broken DHCP function.

I did a fresh install of Xubuntu under Windows on another machine and the NetworkManager had no problem recognizing the wired network connection. But it didn't have any problem doing so before the upgrade on the broken machine either.

So far, it still doesn't look to me like I'm doing anything wrong. Unless someone can show me otherwise, I'm going to file a bug report on this. I imagine it's probably some configuration that the upgrade process messed up but I'm not familiar enough with it to find it. While I appreciate your help, nobody here seems to be able to help me actually fix it. So, it's starting to look like the way to fix it is going to be to backup files, reformat the drive, reinstall, restore files and avoid following the recommendation of upgrading rather than reinstalling in the first place because the upgrade process seems to be broken.

Thanks again for your efforts.

Since you indicated that you're getting an IP address, DHCP seems to be working fine. What seems to be broken is DNS. This could be caused by a number of things including router problems. The best way I know how to fix this problem is to:
1) Manually assign DNS servers in Ubuntu.
-or-
2) Manually assign DNS servers in your router.

DNS issues sometimes happen under fresh installs, as well as after upgrades. More often than not, the problem is related to cheap retail level routing equipment. Also, years of experience with retail routers tells me that just because it works on one computer and not another doesn't mean that the problem isn't the router.

Try rebooting your router.

If that is not successful, before filing a bug I suggest installing Xubuntu hardy on another machine, and then upgrading it to Ibex to see if you can duplicate the issue. I was unable to.

> **Loosewheel said:**
> Hi user1111,
You should look at '/etc/network/interfaces' file. It should look like:

auto lo
iface lo inet loopback

Any other lines, (ie.auto eth0... should be commented out with '#'.

user1111 indicated [in post #8](http://ubuntuforums.org/showpost.php?p=6597348&postcount=8) that Xubuntu had an IP address, so I think this step is not necessary, but it can't hurt to try.

---

### Post by Loosewheel on 2009-01-23
Hi dmizer,user1111,
I did notice he has an IP in post #8. But in post #1, NM says "device unmanaged". Nothing in 'resolv.conf' either.
So where did the IP come from? Maybe 'network-admin', which is 'Applications>System>Network' in Xubuntu....installed by default in 8.04, and not instaled in 8.10. (Note user1111, Ubuntu is different and  would be 'System>Administration>Network')

Ubuntu and Debian,modified NetworkManager so it would not manage anything listed in the 'interfaces' file. So I'd make sure 'eth0' isn't in there.
After that I'd check that 'Auto eth0' is checked so NM can bring it up, and make sure, (under 'IPv4 tab'), dhcp is selected.
I believe a reboot is needed.

---

### Post by user1111 on 2009-01-24
> **Loosewheel said:**
> Hi user1111,
You should look at '/etc/network/interfaces' file. It should look like:

auto lo
iface lo inet loopback

Any other lines, (ie.auto eth0... should be commented out with '#'.
...
Thanks Loosewheel, that fixed it.

---

### Post by dmizer on 2009-01-24
> **user1111 said:**
> Thanks Loosewheel, that fixed it.

That is fantastic. I learned something new! :)

---

### Post by user1111 on 2009-01-24
> **Loosewheel said:**
> Hi dmizer,user1111,
I did notice he has an IP in post #8. But in post #1, NM says "device unmanaged". Nothing in 'resolv.conf' either.
So where did the IP come from? Maybe 'network-admin', which is 'Applications>System>Network' in Xubuntu....installed by default in 8.04, and not instaled in 8.10. (Note user1111, Ubuntu is different and  would be 'System>Administration>Network')

Ubuntu and Debian,modified NetworkManager so it would not manage anything listed in the 'interfaces' file. So I'd make sure 'eth0' isn't in there.
After that I'd check that 'Auto eth0' is checked so NM can bring it up, and make sure, (under 'IPv4 tab'), dhcp is selected.
I believe a reboot is needed.
I now believe that what may have happened was that sometime in the past the network administrator tool may have been used to set a static IP and everything appeared to be working under 8.04 with NetworkManager. The DHCP server was configured to always give this MAC the same IP so DHCP appeared to be working. The 8.10 upgrade then removed the network administrator tool used to manage those settings but left the settings in place and replaced NetworkManager with a version that no longer worked with the those settings.

Short story, they removed one tool but left its settings behind and replaced it with a new tool that would not work with those left behind settings in place, kind of leaving things locked up. Perhaps the upgrade process should import those old settings into the new version of NetworkManager?

---

### Post by dmizer on 2009-01-24
> **user1111 said:**
> Short story, they removed one tool but left its settings behind and replaced it with a new tool that would not work with those left behind settings in place, kind of leaving things locked up.

As long as there is not one submitted already, this is probably worthy of a bug report :)

---

### Post by Loosewheel on 2009-01-24
> **dmizer said:**
> As long as there is not one submitted already, this is probably worthy of a bug report :)

user1111,dmizer,

Seems the 'Ubuntu documentation', here:
[https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html)

didn't quite make the transistion from ubuntu-8.04 to -8.10.
People trying to follow the guides comming back with "it said...",but "I don't have...". ('sys>admin>network'. Not installed on 8.10) 

And, In chapter2:
"If you are not connected to a network after following the procedure above:

   1. Left-click the Network Manager icon again and press Manual configuration..."

Those instructions are for NM-0.6.6...there's no 'Manual config...' with NM-0.7.

Take a look at the first page, ch.1 Connect to the Internet:

"Network Manager is used in many sections of this guide - you can find it:

   1. In System &#8594; Administration &#8594; Network

      
   2. In the Notification Area. Its icon resembles two computer screens on top of each other, or a wireless signal indicator if you are connected to a wireless network."

Step 1 = not there.
step 2 = That is the nm-applett, and it pulls up, what looks to me to be, 'network-admin'. (Using 8.04/0.66 and selecting 'Manual config...')

So it kinda looks like a guide for 8.04 and not 8.10

reguards

---

