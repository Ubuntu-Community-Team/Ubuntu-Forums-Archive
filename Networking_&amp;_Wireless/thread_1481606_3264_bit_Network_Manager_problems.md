---
title: "32/64 bit Network Manager problems"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by McRat on 2010-05-12
Same problem.  I know the OS can see the network device (USB Hawkings) because it appeared during one of the network commands line functions I did trying to figure this out.  

No idea what a [COLOR="blue"]Notification Area[/COLOR] is, or what a [COLOR="blue"]NetworkManager[/COLOR] icon would look like.  I'm assuming it's the lower right area with the trashcan, but there is nothing there but holding boxes for active applications.

On a standard 64bit 10.04 install, the [COLOR="blue"]etc/NetworkManager[/COLOR] directory belongs to the [COLOR="blue"]root[/COLOR], and the user does not have permission to edit the files.

So those two command line thingys won't work unless you have set up the system against the advice given during the install.  I think this is a simple ENABLE type thing, but can't see how it could be done, command line or otherwise.  If I attempt to launch NetworkManager, it says it's already running.

---

### Post by pdc on 2010-05-12
Hi Patrick;

here is an old post about a notification area

[https://help.ubuntu.com/7.04/user-guide/C/panel-default.html](https://help.ubuntu.com/7.04/user-guide/C/panel-default.html)

and here is where ubuntu may head

[http://www.neowin.net/news/ubuntu-to-kill-its-notification-area-system-tray](http://www.neowin.net/news/ubuntu-to-kill-its-notification-area-system-tray)

network manager is on the top line; towards the right, but usually the most left of the right-sided icons at the top !! (used to be two TV screens, but on ubuntu looks different; on eth0 has a chevron appearance; with wireless and mobile broadband looks triangular .......... well illustrated in the last thread ........

to edit files such as etc/NetworkManager one needs to assume sudo powers

> sudo gedit etc/NetworkManager

and you enter your sudo password

whereas if you just go 

> gedit etc/NetworkManager you just get to read the file and cannot save changes: sort of a safe way to look without changing

stops you pressing the "let wings fall off" button by mistake ...

---

### Post by McRat on 2010-05-12
Thanks!  :)

OK, more data:

The NetworkManager Icon looks like a WLAN/Rainbow symbol and it's at the **upper right** of the title bar.

I'm on a 32bit 10.04 machine right now and NetworkManager is working.  It does not appear when you have an ethernet cable plugged in.  Disconnect ETH plug in USB, then restart.

This icon is not present on a 64bit machine with the Hawkins USB 802.11n device.  

The Belkin Wireless G+ MIMO USB works Plug-n-Play with no issues.  Works very smooth, smoother than Win installs.  Built-in Ubuntu driver auto-installs, throw disk away.  This is a $15? device that will work with any USB computer.  Perhaps if you can't get OEM wireless to work, disable it in BIOS, then use a Belkin G+ USB.

Oh, the reason this Belkin USB was sitting here is because it would not work on a 3 yr old XP SP3 machine even with the disk, Windows problem.  Score One for Ubuntu.

---

### Post by McRat on 2010-05-12
AH HA!  Now there is a UpArrow DownArrow symbol where the Rainbow was on this 32bit machine.  I don't believe it was there earlier.  It signals that Ethernet Cable is active.

---

### Post by McRat on 2010-05-12
OK, now I hot-disconnected the cable, the icon switched to Rainbow (no connection warning) then I hot-connected the G+ USB.  The icon went back to full Rainbow, and autoconnected.

So now I know how it's SUPPOSED to look and act, so it will be easier to troubleshoot the 64bit machine.

---

### Post by Iowan on 2010-05-12
Moved to a separate thread from [here]("http://ubuntuforums.org/showthread.php?p=9283901#post9283901").

Perhaps the [Ubuntu pocket guide]("http://www.ubuntupocketguide.com/index_main.html") would be helpful. This is not a sales pitch (AKA spam).

---

### Post by McRat on 2010-05-12
Thanks! :)

I posted that stuff in the hope it might help other newbies.  Things as simple as Notification Area are simple to experienced users, but to others it might not be.  In my case, the example of what the notification area looks like is a null-file (busted link?).  Descriptions indicate it's on the bottom right.  It's not.

AFAIK, my wireless is solved.  If I can't get the Hawkings device to work, I load U32 and install a Belkin USB stick.

---

### Post by McRat on 2010-05-12
OK, home again.  Ubuntu 64 with Gnome on top.  No icon will appear under any conditions for Network Manager.  Normal ethernet works fine, but the UpArrow/DownArrow never appears.

Belkin G+ USB will not enable.  Seems to be specific to 64bit system.  

So I will just install U32 instead and start again.

---

### Post by McRat on 2010-05-13
OK, up and running with U32 10.04 normal install. Network functions perfect.

No other changes.  

U64 with Gnome frontend will not show Network Manager Icon or attempt to hook wireless devices that work fine on U32.

Performance:
Wireless (Belkin 802.22G turbo) = 9.8 mbps speedtest.net
Ethernet = 26 mbps
Dell Wireless/XP = 14.0 mbps

---

