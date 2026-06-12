---
title: "Network Applet Manager not working"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by SynapseR on 2006-06-08
Hi,

My ethernet and wireless networking works, but the abovementioned applet always reports no network connection.
Any way to fix this ?

-Thanks

---

### Post by andyman on 2006-06-08
Interestingly I have exactly the same issue.  Atheros chipset wireless card that works out of the box, but gnome network manager says no connection.....

---

### Post by nanotube on 2006-06-08
i tried the dapper livecd, installed networkmanager, and it did the same thing - even though my wireless was connected, network manager showed no connection.

anyone have any idea what's up with this? i can't upgrade to dapper until the networkmanager can be shown to work...

---

### Post by Nekrataal on 2006-06-09
Yeah same problem here, im posting this with a NO CONECTION notice from network manager..

---

### Post by eferrari on 2006-06-09
I have a similar problem: My wired interface (eth0) works just fine with NetworkManager and nm-applet, but NetworkManager does not even show that my wireless NIC exists. Using the Network Settings dialog I can make wireless work, but NetworkManager does not even recognise that eth1 (my wireless interface) exists.

running nm-tool (while my wireless eth1 interface is connected and working fine) shows only my wired interface:
```
eferrari@t42:~$ nm-tool eth1

NetworkManager Tool

State: disconnected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            e1000
  Active:            no
  HW Address:        00:0D:60:FD:CC:31

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           65535 Mb/s

  Wired Settings
    Hardware Link:   no

```

---

### Post by nanotube on 2006-06-09
[QUOTE=eferrari]I have a similar problem: My wired interface (eth0) works just fine with NetworkManager and nm-applet, but NetworkManager does not even show that my wireless NIC exists. Using the Network Settings dialog I can make wireless work, but NetworkManager does not even recognise that eth1 (my wireless interface) exists.

running nm-tool (while my wireless eth1 interface is connected and working fine) shows only my wired interface:
```
eferrari@t42:~$ nm-tool eth1

NetworkManager Tool

State: disconnected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            e1000
  Active:            no
  HW Address:        00:0D:60:FD:CC:31

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           65535 Mb/s

  Wired Settings
    Hardware Link:   no

```[/QUOTE]

yep, this is exactly what happened to me.

---

### Post by heffo_j on 2006-06-10
Hi folks,

For what it is worth, I have the same as the rest of you. Sorry I don't have an answer of any kind.  ](*,) 

Regards
John

---

### Post by Nekrataal on 2006-06-10
It seems to be a common issue, hopefully someone could find an answer, im working on it, but its a dead end for me

---

### Post by Jad on 2006-06-11
I hope they can solve it soon

---

### Post by nanotube on 2006-06-12
i have a possible solution. according to this wiki page: [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

> Dapper

If it is not managing your network connections after upgrading to Dapper, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let NetworkManager handle them. 

that page has a bunch of nice stuff. maybe that will solve the problems. (havent tried myself yet, since i'm running breezy still).

---

### Post by Nekrataal on 2006-06-12
[QUOTE=nanotube]i have a possible solution. according to this wiki page: [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)



that page has a bunch of nice stuff. maybe that will solve the problems. (havent tried myself yet, since i'm running breezy still).[/QUOTE]


Yes, that solved it for me, another question, Network manager can handle static IP address?

---

### Post by nanotube on 2006-06-12
[QUOTE=Nekrataal]Yes, that solved it for me, another question, Network manager can handle static IP address?[/QUOTE]
apparently the answer to that is "somewhat, depending on what you want to do". please see this message:
[http://mail.gnome.org/archives/networkmanager-list/2006-February/msg00198.html](http://mail.gnome.org/archives/networkmanager-list/2006-February/msg00198.html)

---

### Post by eferrari on 2006-06-12
Indeed this worked for me as well.  The NetworkManager/applet works beautifully now (much better than the previou version I used back in Breezy)

A few minutes ago, I actually found the same solution in an old posting on these forums:
[http://www.ubuntuforums.org/showthread.php?t=134251](http://www.ubuntuforums.org/showthread.php?t=134251)

---

### Post by JSVH on 2006-06-14
This thread helped me so much!

The only problem I have is everytime I try to boot up in my home wireless network I get a message:

"Enter password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked"

And I have to enter my root password for it to unlock my WEP network. Is there anyway I can make it automatically connect so I dont have to enter my password everytime I boot up?

---

### Post by .tommie on 2006-06-14
[QUOTE=JSVH]This thread helped me so much!

The only problem I have is everytime I try to boot up in my home wireless network I get a message:

"Enter password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked"

And I have to enter my root password for it to unlock my WEP network. Is there anyway I can make it automatically connect so I dont have to enter my password everytime I boot up?[/QUOTE]

Indeed, NetworkManager does its thing after commenting out the wireless NIC... to bad, because it should have worked in the first place. These are the little things which keeps home users from using Linux. Otherwise very nice tool indeed!

It's working for me, but an automatic solution instead of entering a password after every reboot (for nm-applet) would be nice, because other users can't connect with the WLAN.

Any idea's?

---

### Post by .tommie on 2006-06-17
Uhm just in case...

Someone with some more information about the password nm-applet present? 

We really need a solution, because the other users can 't use Internet... :(

---

### Post by ssmaxss on 2006-06-18
I have problem with NetworkManager: my wireless card is connected and I install network-manager-gnome. Applet reports "no connection". I remove my config from /etc/networking/interfaces and then my network isn't working but nm-applet shows no connection. But nm-tool only lists wired connection. I am using atmel-based usb wifi dongle.

---

### Post by .tommie on 2006-06-19
[QUOTE=ssmaxss]I have problem with NetworkManager: my wireless card is connected and I install network-manager-gnome. Applet reports "no connection". I remove my config from /etc/networking/interfaces and then my network isn't working but nm-applet shows no connection. But nm-tool only lists wired connection. I am using atmel-based usb wifi dongle.[/QUOTE]

I'm no expert in this, but you might have commented out the wrong ethernet interfaces.

Could you post your /etc/network/interfaces file?

---

### Post by ssmaxss on 2006-06-19
only this:

auto lo
iface lo inet loopback

---

### Post by .tommie on 2006-06-20
You probably removed these wired connections from your /etc/network/interfaces file. Insert those again, and I suppose it should work.

My /etc/network/interfaces as **_example_**:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
```

---

### Post by ssmaxss on 2006-06-20
I do not have wired connection (I have wired card but never insert cable). I'll try this.

---

### Post by yee.wei.law on 2006-06-25
[QUOTE=.tommie]Indeed, NetworkManager does its thing after commenting out the wireless NIC... to bad, because it should have worked in the first place. These are the little things which keeps home users from using Linux. Otherwise very nice tool indeed!
[/QUOTE]

I agree. I suppose it has not been done properly because prior to the Network Manager era every distribution handles their network interfaces differently, so it's hard for Network Manager to decide for the users which configuration scripts to modify. It is [FONT="Courier New"]/etc/network/interfaces[/FONT] for Ubuntu but different files for other distro's. 

I am also wondering if the distro developers or Network Manager developers should handle this differences.

---

### Post by yee.wei.law on 2006-06-25
[QUOTE=.tommie]You probably removed these wired connections from your /etc/network/interfaces file. Insert those again, and I suppose it should work.

My /etc/network/interfaces as **_example_**:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
```[/QUOTE]


Actually, according to the [Ubuntu documentation]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"), you should let Network Manager handle *all* interfaces other than the loopback interface. And this is what I have done, and it works.

---

### Post by unkalledfor on 2006-07-21
After I commented out all the interfaces from /etc/network/interfaces.. my wireless was still not being detected by NM..only my wired was being detected..

I then remembered I am running Ndiswrapper, and it was probaly not being loaded correctly, so i added a "ndiswrapper" line in /etc/modules

I rebooted and boom.. it was working perfectly... hope this helps someone.. it took me half an hour to think of this...

---

### Post by dppowell on 2006-09-30
Following up on an earlier message in this thread, has anyone discovered how to make NM play nicely with the Gnome keyring manager?  I get prompted for my keyring password every time NM wants to connect to a protected WLAN.

---

### Post by vayde on 2006-10-03
I'd love to hear about a solution to that one too.  I've installed gnome-keyring-manager, and it's set to allow nm-applet to read and write to the default keyring, but still no joy.

---

### Post by windows_sucks_try_unix on 2007-03-26
Hi,
First time ever that I discovered an answer :)
I am using mint linux bianca and ndiswrapper loaded drivers for an amtel usb nic and had the same network applet problem as soon as I changed (ESSID) from my default "NETGEAR" to "any" in the network config section the applet is doing what it is supposed to. hope this helps someone cheers

---

