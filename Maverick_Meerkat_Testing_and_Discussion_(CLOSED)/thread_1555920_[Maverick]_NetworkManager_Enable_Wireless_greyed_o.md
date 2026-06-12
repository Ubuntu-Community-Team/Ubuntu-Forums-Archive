---
title: "[Maverick] NetworkManager: Enable Wireless greyed out"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by airfrizz on 2010-08-18
Hi,

I'm having trouble with the NetworkManager Applet on ubuntu 10.10. After startup, there's no connect to a (configured) wlan. "Enable wireless" (right-click) is not selected and can't be selected, because it's greyed out. When I do something that requires authentication, e.g. right-click and select "Edit connections", then "Enable wireless" can be selected and after doing so, it will connect to the wlan.

Choosing "make available to all users" in the wlan definition, or adding the "connect to wireless and ethernet networks" privilege to my user had no effect.

Any idea, what I'm doing wrong?

Thanks,
Christian
__

---

### Post by Iowan on 2010-08-18
Moved to Maverick Meerkat Testing and Discussion.

---

### Post by cariboo on 2010-08-18
Are the proper drivers for your wireless device installed and active?

---

### Post by dxxvi on 2010-08-18
It happens to me too. Before I could use the wireless card, now I cannot anymore. When I run ifconfig, I still see the wlan0 and its HWaddr.

---

### Post by Untitled_No4 on 2010-08-19
I'm using Kubuntu and I don't know if that applies to Gnome as well, but when I have this problem I have to edit /var/lib/NetworkManager/NetworkManager.state and change NetworkingEnabled to true (the other two should be true as well).

---

### Post by moviemaniac on 2010-08-19
Same here - it's pretty annoying because I can't disable WiFi and am prompted every few minutes to enter the password for the only (protected) network in reach (not my network so I don't know the password).

---

### Post by dxxvi on 2010-08-19
> **Untitled_No4 said:**
> I'm using Kubuntu and I don't know if that applies to Gnome as well, but when I have this problem I have to edit /var/lib/NetworkManager/NetworkManager.state and change NetworkingEnabled to true (the other two should be true as well).
Everything is true in my NetworkManager.state but the wireless is still not working.

After upgrade to 2.6.35-16, I don't see the wireless card anymore (don't see it with ifconfig).

---

### Post by LiquidMeson on 2010-08-20
> **moviemaniac said:**
> Same here - it's pretty annoying because I can't disable WiFi and am prompted every few minutes to enter the password for the only (protected) network in reach (not my network so I don't know the password).

if you right click and go to edit connections you can delete the setting for wifi networks that dont' work. that way your pc won't try to auto connect to them. You laptop should also have a physical disable wifi switch.

---

### Post by dxxvi on 2010-08-20
> **dxxvi said:**
> Everything is true in my NetworkManager.state but the wireless is still not working.

After upgrade to 2.6.35-16, I don't see the wireless card anymore (don't see it with ifconfig).
After a reboot I can see the wlan0 with ifconfig, but there's no wireless network when I left click the network icon next to the clock & calendar.

---

### Post by cariboo on 2010-08-20
What wireless chipset are those of that have problems with wireless using? Do you all have the same wireless device?

---

### Post by airfrizz on 2010-08-22
> **cariboo907 said:**
> What wireless chipset are those of that have problems with wireless using? Do you all have the same wireless device?

I have a Broadcom Corporation BCM4313 802.11b/g LP-PHY., but to me it looks more like a problem of the NetworkManager(-applet). After booting, iwconfig shows the device.

However, even if I grant my user "connect to wireless and ethernet networks", I have to authenticate, when I try to "Edit Connections..." in the applet.

Regards,
Christian

---

### Post by moviemaniac on 2010-08-22
Broadcom 4311 here....

---

### Post by dr_kabuto on 2010-08-22
Hi,
today I've upgrade to Maverick. Wireless is not working and I can't turn on the killswitch. Intel card here.

---

### Post by airfrizz on 2010-08-23
> **Untitled_No4 said:**
> I'm using Kubuntu and I don't know if that applies to Gnome as well, but when I have this problem I have to edit /var/lib/NetworkManager/NetworkManager.state and change NetworkingEnabled to true (the other two should be true as well).

Setting these 3 properties to true (WirelessEnabled was set to false) didn't change anything. The "Enable Wireless" was still unchecked and greyed out.

BTW, I'm not on gnome or kubuntu, but on xubuntu.

---

### Post by 4leite on 2010-08-24
hiya,

May not be related, but I was experience a similar thing:
I connect to the internet using dial-up networking on my cell phone via blue tooth (blueman). Once enabled in blueman, the connection becomes available in nm-applet and autoconnects.

So far so good and mostly works as expected but some times when the connection drops, as cell connections sometimes do, then nm-applet seems to disable wireless connections and at this stage the only thing I have found that fixes it is a reboot. I have tried killing/restarting nm-applet, blueman (and applet and daemon), networking etc, to no avail.

I can't reproduce it in order to bug test, but the end result is the same: wireless connection is greyed out and unavailable regardless of the actual state and there is no way of enabling it.

Hope this provides some clues for someone...

---

### Post by ciiccii on 2010-08-26
same here. wlan0 is not shown in ifconfig output. However i can use wireless networking if i start livecd o.O But after fresh install it's doesn't work. I use an atheros chipset.

---

### Post by hexsel on 2010-08-26
Broadcom chipset always cause me grief when a new kernel comes in.  I'm not using Maverick yet, but try seeing if there's a proprietary driver in System/Administration/Hardware Drivers.



> **4leite said:**
> hiya,

May not be related, but I was experience a similar thing:
I connect to the internet using dial-up networking on my cell phone via blue tooth (blueman). Once enabled in blueman, the connection becomes available in nm-applet and autoconnects.

So far so good and mostly works as expected but some times when the connection drops, as cell connections sometimes do, then nm-applet seems to disable wireless connections and at this stage the only thing I have found that fixes it is a reboot. I have tried killing/restarting nm-applet, blueman (and applet and daemon), networking etc, to no avail.

I can't reproduce it in order to bug test, but the end result is the same: wireless connection is greyed out and unavailable regardless of the actual state and there is no way of enabling it.

Hope this provides some clues for someone...

---

### Post by cariboo on 2010-08-26
I've got a broadcom 4312 chipset in my netbook that works quite well, the only thing, is I need to have to be connected to the network via a cable in order to install the STA drivers. 

On one of my maverick installs, I've have enable networking greyed out, although it connects and works well with zero problems.

Has anyone tried connecting by the command line to see if it works that way? Instructions are [here]("http://ubuntuforums.org/showthread.php?t=571188").

---

### Post by yoblin on 2010-08-31
Finally figured this one out I think... Press the enable wireless button on your keyboard ;)

Took me a week to figure out, hopefully same problem for you guys.

Looks like one of the updates about a week ago disabled it.

---

### Post by kyleabaker on 2010-09-03
> **yoblin said:**
> Finally figured this one out I think... Press the enable wireless button on your keyboard ;)

Took me a week to figure out, hopefully same problem for you guys.

Looks like one of the updates about a week ago disabled it.
I just ran updates and only had an update for Chrome's web inspector and Connman so I installed them both. After rebooting, the option to enable networking is disabled as everyone else has mentioned.

Connman updated to version 0.55-0ubuntu3 for me now, but it worked perfectly fine before updates.

EDIT:
All options in /var/lib/NetworkManager/NetworkManager.state or marked true.
> 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


My card is a [Ralink rt2500]("http://www.google.com/#hl=en&q=ralink+rt2500&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=5673716d440c1f33").

---

### Post by keypox on 2010-09-03
Very similar issue here but with wired network

---

### Post by kyleabaker on 2010-09-03
> **keypox said:**
> Very similar issue here but with wired network

Did that happen right after the same update (connman)?

---

### Post by Milos_SD on 2010-09-03
I have simular problem, but here nm-applet says there is no network devices available. That happend after I tried indicator-network (installed, tried and then removed). 
[http://pastebin.com/B8vZBybv](http://pastebin.com/B8vZBybv)

---

### Post by andrewabc on 2010-09-03
> **keypox said:**
> Very similar issue here but with wired network

I have same problem beta on liveusb, I can not connect to wired network.
Sometimes eth1 appears and I tell to connect but it can't.

I will try my wireless usb dongle to see if it can connect wirelessly. EDIT: wireless usb works.

Image shows two things greyed out even though it is listing wired and wireless connections.

I have a second wired ethernet port, but I'm not going to try it yet because it screws up my other port if I unplug it (it dies for a day or so, a hardware/wiring problem).

---

### Post by keypox on 2010-09-03
It did happen after I installed then updated. Not sure o.n which update but that sounds familiar.

---

### Post by keypox on 2010-09-03
It thinks the network cable is in pluggEd but it isn't. It's the same in windows now, not sure if the Ethernet I'd out.  I doubt it but not sure what's causing this issue though

---

### Post by kyleabaker on 2010-09-03
I've been updating since Alpha 2, so I think I'll try a fresh Beta install and see if the problem disappears. I'm going to backup some Connection Manager (connman) configuration files first so I can compare them if the Beta works properly. Maybe that will help shed some light..

---

### Post by cariboo on 2010-09-03
I found that if you set a static ip address, enable networking on some systems is greyed out, and others it is visible. On this system it is visible, on another system that's been upgraded since alpha 1, it's greyed out.

---

### Post by mamers.sdtb on 2010-09-04
I had the same issue after updating the connman package. Removing connman is helpful.

---

### Post by philipballew on 2010-09-09
my computer is greyed out but wired still works and every few restarts the network manager isn't greyed out

---

### Post by PGHammer on 2010-09-09
> **philipballew said:**
> my computer is greyed out but wired still works and every few restarts the network manager isn't greyed out

Not a single problem (wired or wireless) with my 10.10 AMD64 clean install.

Wired is nVidia MCP73 gigabit Ethernet (which is the default); wireless is SMC USB wireless-G WPA2.  Both are also DHCP.

Wireless configuration couldn't have been any easier!  Right-click the Network icon in the tasktray (same place it would be in Windows, actually)->Network Management Settings->Wireless->New->Scan (click to select)->enter passphrase.  A few more steps than Windows 7, but not much different from 7 (or XP, for that matter).

I haven't had a network configuration issue with Kubuntu since Gutsy Gibbon was in beta.

---

### Post by jorge2904 on 2010-09-10
Im experiancing this same issue. Has a workaround been found or is there a bug report on lunchpad? Im using a Broadcom Corporation BCM43225 802.11b/g/n

---

### Post by jorge2904 on 2010-09-10
I created a bug report referancing this thread. [https://bugs.launchpad.net/ubuntu/+bug/635091](https://bugs.launchpad.net/ubuntu/+bug/635091)

---

### Post by jorge2904 on 2010-09-10
Turns out this is a Network Manager problem and not a driver problem. Download the wcid package and disable Network Manager from startup and use wicd to connect to your networks

```
sudo apt-get install wicd
```

---

### Post by cariboo on 2010-09-10
I have a fresh install, using today's daily build, wireless is greyed out, but it does work.

---

### Post by philipballew on 2010-09-10
i am the same as cariboo907. all mine work but are still grayed. will this bug be fixed by the time 10.10 moves away from beta?

---

### Post by cariboo on 2010-09-10
Four pages, and not one bug report, I couldn't find anything on this matter so I created one, bug #[lpbug]635371[/lpbug]

---

### Post by Wooglin on 2010-10-09
When right-clicking Network-Manager in toolbar, "Enable Wireless" is disabled on my HP G60-519WM with an Atheros AR9285. This option worked flawlessly prior to updating to Maverick RC on 10-6-10.

Tried the following in a terminal:
```
norlando@wooglin:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

So I checked the following:
```
norlando@wooglin:~$ rfkill list
0: hp-wifi: Wireless LAN
 Soft blocked: yes
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
norlando@wooglin:~$ sudo rfkill unblock all
norlando@wooglin:~$ sudo rfkill list
0: hp-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
```

At this point, right-clicking on the Network-Manager tool showed my wireless was now enabled, and in the process had actually had auto-connected to one of my saved networks!

Hope this works for someone else too!

---

