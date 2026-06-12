---
title: "Xubuntu 10.04 - where is network? Network Manager?"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by displayaway on 2010-07-28
Just installed Xubuntu 10.04 via the alt install CD.
I would like to configure my wireless card.


Nowhere did the install attempt to utilize the wireless card, opting to config the eth0 wired connection instead.

When I use the menus, I can't find a network control panel anywhere in Xubuntu 10.04 virgin install.  All the Ubuntu docs point to using network manager.

Applications>System>...   there is no network manager choice. There are no items named network at all under System.

Applications>Network>... contains choices that use the network like: Firefox, Thunderbird, Transmission. But no network control panel or network manager.

Applications>Accessories>Application Finder... does not find network manager anywhere.


BUT...
sudo apt-get -us install network-manager
tells me that on my system, the installed
network-manager is already the newest version.


So how do I convince Xubuntu menus that network-manager is there?

FYI, my card is recognized and is using the ath5k driver. 
iwlist scan will show lots of cells active nearby.

Can someone help me figure out which forum messages to follow and which to ignore, since most are depreciated by ath5k being in the kernel for Xubuntu 10.04 and the card being recognized automatically?

Thanks

---

### Post by snowpine on 2010-07-28
Network Manager is a little icon on your toolbar.

If you don't see it, you can launch it with Alt+F2, "nm-applet" (without the quotes).

Sorry but I am not familiar with your specific graphics card.

---

### Post by ajgreeny on 2010-07-28
It may make things easier if you temporarily disable or disconnect the wired network connection, as the system may be making that the default, and therefore ignoring the wireless.

---

### Post by displayaway on 2010-07-28
Nothing happened. Well, at least that's what my screen displays.

Try to run via a terminal... unfortunately, it says it's already running.

~$ ps ax | grep nm
 1376 ?        Ss     0:00 nm-applet --sm-disable

If I log out the desktop user, and access via ssh the applet is not running.
If I log in the desktop user, there is a nm-applet process running automatically.

Any clues why the applet is backgrounded automatically?

Thanks

---

### Post by displayaway on 2010-07-28
Rebooted with eth0 cord disconnected.

login as Admin user

~$ ps ax | grep nm
1376 ? Ss 0:00 nm-applet --sm-disable

nm-applet is still auto started. Does not display. Won't allow me to open another instance.

---

### Post by iponeverything on 2010-07-28
try to kill off the running instance and starting from the terminal so that you can any errors generated. 


```
killall -v -9 nm-applet
nm-applet&
disown
```

---

### Post by displayaway on 2010-07-28
> **iponeverything said:**
> try to kill off the running instance and starting from the terminal so that you can any errors generated. 


```
killall -v -9 nm-applet
nm-applet&
disown
```
Still does not appear to work. No icon on the menu, no window. I get this from the command line instead.

DEBUG: old state indicates that this was not a disconnect 0
DEBUG: old state indicates that this was not a disconnect 0

thanks though

---

### Post by ajgreeny on 2010-07-28
In gnome the nm applet now sits in the notification area, and not as a separate applet.  I don't even know if there is a notification area in the panel of xfce, but I wonder if this, or the xfce equivalent, is what's missing in your setup.

---

### Post by MAFoElffen on 2010-07-28
> **ajgreeny said:**
> In gnome the nm applet now sits in the notification area, and not as a separate applet.  I don't even know if there is a notification area in the panel of xfce, but I wonder if this, or the xfce equivalent, is what's missing in your setup.
On mine (Ubuntu 10.04.1 LTS), if you do what you asked- it cycles through the small network "connecton" applet for each device... showing it's connections.

If you click on the upper bar "arrows" icon (upeer right), that indicates "Network", it drops down a network magement menu.  The options are:  Wired Networsk and Device statuses, Wirless network and statuses, Connect, Disconnect, Available Networks, VPN Connections, Connect to Hidden Wireless Network, Create New Wireless Network... etc.

If you right clip on the same applet icon, it will do the same with a different menu. Options: Enable Networking, Enable Wireless, Enable Notifications, Correction Information, About.

Is this what you two are looking for?  I think this has evolved since the earlier "Window" that I see in tutorials on earlier versions of the network manager.

---

### Post by displayaway on 2010-07-29
I think you've nailed it. Can this gnome applet even display in  xfce notification area?


Behavior is consistent across three virgin installs. No such item displays.
Anyone know where to file a bug for Xubuntu?

---

### Post by displayaway on 2010-07-29
The issue is, the icon does not display on Xubuntu 10.04.

The icon/choice does NOT appear in the application menu, or any of it's sub-sections.
Nor can it be found when selecting from the menus  Applications>Accessories>Application Finder.

I think this is a bug for Xubuntu implementation.
Wicd will display on xfce. network-manager does not.

---

### Post by bobcollard on 2010-08-19
Right click Panel>+Add New Items>Notification Area: Add

---

### Post by displayaway on 2010-08-19
thanks for the suggestion.

OK, did that (add notification area) and Ubuntu Sez:
"There is already a notification area running on this screen."

Note: the volume control/speaker icon has always displayed, along with the time and that funny little door. It's just network-manager that won't display on Xubuntu 10.04.

I still feel this is a problem with network-manager vs xfce. 

There is ample anecdotal evidence that network-manager won't work with xfce, while wicd will work on gnome, xfce, kde, etc. Unfortunately, Ubuntu main branch has much history with network-manager and so probably won't change to wicd, just because of xUbuntu issues. So Xubuntu users are in a catch 22.


I'd still like to have this resolved;
 for those who'd like to roam to multiple access points, newbies, first time ubuntu / linux users, etc.

**fortunately I'm using 10.04 on machines in static locations. 
So I just ran
sudo apt-get -u remove --purge network-manager-gnome
sudo apt-get -u remove --purge network-manager
and set the wireless up directly in /etc/network/interfaces.

I could have also installed wicd at this point and been done with it.

 Just don't try to use /etc/network/interfaces and network-manager together. Or network-manager and wicd together. Sure fire way to get everything conflicting.

---

### Post by bobcollard on 2010-08-19
> **displayaway said:**
> thanks for the suggestion.

OK, did that (add notification area) and Ubuntu Sez:
"There is already a notification area running on this screen."

Note: the volume control/speaker icon has always displayed, along with the time and that funny little door. It's just network-manager that won't display on Xubuntu 10.04.

I still feel this is a problem with network-manager vs xfce. 

There is ample anecdotal evidence that network-manager won't work with xfce, while wicd will work on gnome, xfce, kde, etc. Unfortunately, Ubuntu main branch has much history with network-manager and so probably won't change to wicd, just because of xUbuntu issues. So Xubuntu users are in a catch 22.


I'd still like to have this resolved;
 for those who'd like to roam to multiple access points, newbies, first time ubuntu / linux users, etc.

**fortunately I'm using 10.04 on machines in static locations. 
So I just ran
sudo apt-get -u remove --purge network-manager-gnome
sudo apt-get -u remove --purge network-manager
and set the wireless up directly in /etc/network/interfaces.

I could have also installed wicd at this point and been done with it.

 Just don't try to use /etc/network/interfaces and network-manager together. Or network-manager and wicd together. Sure fire way to get everything conflicting.
When and if you install wicd it will automatically remove  network-manager.  It's a no-brainer.  As you can see in my Signature, I  am not even using Ubuntu.  It's Sabayon, a Gentoo derivative and they  use Network-Manager for Xfce.  I have used xubuntu in the past with no network problems.  I love Xfce and would not use another desktop manager.

---

### Post by bobcollard on 2010-08-19
As an added thought here is a [pic] of my corner.  Icons are Sound Mixer, Update Manager, Network-Manager, Wally (Background Changer), Time and Log-Out/Quit.

---

### Post by displayaway on 2010-08-19
If you use Sabayon, and successfully use Network-Manager for Xfce. 

Then this must be a bug in Xubuntu implementation. 
Happened on four machines (two separate downloads of the install media) so far.

I guess I should go file a bug, somewhere.

Anyone know where the Xubuntu bugs are filed?
This is my first project with Xubuntu, usually I work with debian.

---

### Post by bobcollard on 2010-08-19
> **displayaway said:**
> If you use Sabayon, and successfully use Network-Manager for Xfce. 

Then this must be a bug in Xubuntu implementation. 
Happened on four machines (two separate downloads of the install media) so far.

I guess I should go file a bug, somewhere.

Anyone know where the Xubuntu bugs are filed?
This is my first project with Xubuntu, usually I work with debian.
Bugs go here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by displayaway on 2010-08-19
Thanks,

I filed Bug 620624;
now to wait and see
 if anyone can reproduce what has happened on my (four) Xubuntu 10.04 alt CD installs.

---

### Post by agibby5 on 2010-11-15
> **displayaway said:**
> Thanks,

I filed Bug 620624;
now to wait and see
 if anyone can reproduce what has happened on my (four) Xubuntu 10.04 alt CD installs.

I installed from the regular install CD and this is happening for me too.  

I checked out your bug.  It looks like they're asking for more information.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620624](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620624)

---

### Post by pboyce on 2010-11-17
I am running Gnome and have the same problem. No Network manager.
I updated to 10.04 from Hardy Heron and the wireless is now not connected. The USB card is there and so is the correct drover, but the status is "disconnected".

When I run live from the CD everything is fine. I get the Network Manager and a good wireless connection. But how can I get the Network Manager to appear in the notification area on my updated install? Do I have to re-install? And can I do that and keep all my files and settings? I have tried all the suggestions in this thread to no avail.

---

### Post by dineshs on 2010-11-17
To get the icon back try
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set
```
managed=true
```
If there is no progress please post the results of ```
cat /etc/network/interfaces
```and```
sudo lshw -C network
```

---

### Post by bobcollard on 2010-11-17
reinstall network-manager-gnome  see screenshot.

---

### Post by Jack Waugh on 2011-03-19
> **dineshs said:**
> To get the icon back try
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set
```
managed=true
```


That worked for me!!
Thank YEW, very much!
This problem has left the building.

---

