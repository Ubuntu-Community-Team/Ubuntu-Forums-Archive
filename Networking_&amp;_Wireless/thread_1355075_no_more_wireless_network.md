---
title: "no more wireless network"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by plh on 2009-12-14
Hello,

I switched to karmic a couple of weeks ago, and everything worked fine, no problem...
Until last WE, when my wireless network ceased to work suddenly (after an update / reboot I think, without being sure...).

When I try to manually launch the wireless network using the applet, nothing happens. If I run the applet from the command line I get:
-------------------------------------------
$ nm-applet

** (nm-applet:4575): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:4575): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
--------------------------------------------

I googled that but found nothing that fixes the problem, though several mails/posts mention the same error message.
Can anyone give me a hint on what to do?

Thanks in advance!

---

### Post by MaindotC on 2009-12-14
Please try following the steps in the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  A kernel was recently released and it may not work with your wireless card, but you will find that out from following the guide.

---

### Post by plh on 2009-12-15
Hi strAlan, thanks a lot for replying!

I ran into trouble with the link you indicate:

1) "In 9.04 and 9.10 the information is found either by right clicking on the panel applet and selecting "Edit Connections" or in System > Preferences > Network Connections."
Right clicking on panel applet only proposes the ordinary "move/delete/etc" options, and the "System > Preferences > Network Connections." window does not propose a "OK" button, only a "cancel / apply" couple that does not change anything :-(

2) "lshw -C network" answers the following:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:21:f3:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f0300000-f0300fff
So I assume my hardware and device drivers  are recognized... Moreover, if I boot from my original karmic USB key, wifi is available without any problem...


3) lsmod gives an encouraging
iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore

4) iwlist scan gives the following:
wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:6A:64:7B:3B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Livebox-fc15"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007012c2c07
                    Extra: Last beacon: 2584ms ago
                    IE: Unknown: 000C4C697665626F782D66633135
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD790050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084C697665626F7832102400043132333410420004353637381054000800060050F2040001101100084C697665626F783210080002000A103C000101
... and so on until cell 09

By the way, might there be a conflict between wmaster0 (which I don't remember to have seen before the problem appeared) and wlan0 (my traditional wifi interface) in the above excerpts?

Thanks for your opinion and advice!

---

### Post by MaindotC on 2009-12-15
> **plh said:**
> Right clicking on panel applet only proposes the ordinary "move/delete/etc" options, and the "System > Preferences > Network Connections." window does not propose a "OK" button, only a "cancel / apply" couple that does not change anything :-(

I'm not sure if this will help but it seems that you may be right-clicking on the wrong area.  Note the location of my pointer:
[[IMG]http://img51.imageshack.us/img51/2635/screenshotij.png[/IMG]](http://img51.imageshack.us/i/screenshotij.png/)

Do you see an entry under the wireless tab and if so did you try activating it with the "Apply" button and it didn't work?

> 
2) "lshw -C network" answers the following:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:21:f3:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f0300000-f0300fff
So I assume my hardware and device drivers  are recognized... Moreover, if I boot from my original karmic USB key, wifi is available without any problem...

Yes this means the iwl3945 driver is installed and recognizes your device.
> 
3) lsmod gives an encouraging
iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore

Yes this means the iwl3945 drivers are in use.
> 
4) iwlist scan gives the following:
wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:6A:64:7B:3B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on

This line:
> 
                    ESSID:"Livebox-fc15"

means there is a wireless network named Livebox-fc15.  Can you see that network in your network connections (top right of the desktop panel) and can you click on it to connect to it?
> 
By the way, might there be a conflict between wmaster0 (which I don't remember to have seen before the problem appeared) and wlan0 (my traditional wifi interface) in the above excerpts?

There's nothing wrong with wmaster0 being there.  From linuxwireless.org:
> 
Lets clarify device names first. Regularly you should only see two new device names:

wmaster0
wlan0
The wmaster0 device is what we call the master device. The master device is an internal master device used only by mac80211. It should be ignored by users. If possible we will try to hide it from users later.

On distribution releases with old udev rules you may end up with strange network device names, for example, wlan0_rename. You may also end up with master device names such as eth3, when this was actually intended to be named wmaster0. This happens because master interface has the same MAC address as the real interface, and it is created first. The old udev rule, which keys on the MAC addres, may rename it to device names like eth3, for example. Then the real interface is created, udev sees that it has already renamed an interface with that MAC and gives it the wlan0_rename name.


---

### Post by linux6994 on 2009-12-15
I had to switch to Karmic on Linux Mint to get wireless to fly like normal.

---

### Post by plh on 2009-12-16
Quoting strAlan: "Do you see an entry under the wireless tab and if so did you try activating it with the "Apply" button and it didn't work?"

No, this little symbol is absent from my panel. It disappeared a few days after I installed karmic, but I didn't mind when it did since network was running all right...

---

### Post by MaindotC on 2009-12-16
> **plh said:**
> Quoting strAlan: "Do you see an entry under the wireless tab and if so did you try activating it with the "Apply" button and it didn't work?"

If you want to quote me just press the "Quote" button which is next to the reply button.

I don't know why your nm-applet isn't starting.  I searched my system for anyplace that nm-applet is located:[[IMG]http://img687.imageshack.us/img687/4182/screenshot9filesfoundse.png[/IMG]](http://img687.imageshack.us/i/screenshot9filesfoundse.png/)
Can you check to see if yours is located in the same directories and files?

---

### Post by peepingtom on 2009-12-16
I'm pretty certain this is a problem with NetworkManager's configuration. Or Dbus. I'm not sure.
[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)
Here's what you're dealing with: a layer that abstracts control over wifi and other networking stuff.
The issue may also lay with DBus
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)
They really do make it easier to use linux, but something has broken in your case.

Did you upgrade from Jaunty?
Does networking function properly when you boot to a liveCD?
If so, this is some sort of configuration issue, things like this happen during Ubuntu upgrades, often as a result of changes you made to your previous install. Not your fault, it happens :)  If you want a really easy solution that fixes it with a sledgehammer rather than a scalpel, back up your files and reinstall. The problem shouldn't reoccur.

If this is from a fresh Karmic install, this is a horrible and unforgivable problem that we must solve :D
Most people don't care WHY it's broken, they just want to fix it in the easiest way possible. There's nothing wrong with that.

The following advice has no warranty. It should work, but don't get upset if it doesn't. Your data will still be on your system and you can save it with a LiveCD, but your OS might break and require reinstall. I think it will likely work.


A slightly more precise way to fix it, but still very blunt:
This will allow you to connect to the net without using NetworkManager.
You can then purge your system of NetworkManager, and reinstall it. It will then likely have a working configuration.

Connect you computer to your router using an ethernet cable.
I assume it has DHCP, meaning that it gives your computers an IP whenever you plug them in.
This is most likely the case

So, on your broken Ubuntu computer:
Open a terminal
Configure your network using /etc/network/interfaces 
```
sudo gedit /etc/network/interfaces
```
add the following lines ```
auto eth0
iface eth0 inet dhcp
```
Save and exit. Restart your computer. Does it connect to the net? Great! Proceed...

In terminal:
Uninstall NetworkManager's components, along with its configuration files and any programs that depend on it.
```
sudo apt-get purge libnm-glib2 libnm-util1 modemmanager network-manager network-manager-gnome
```
Please make note of the additonal things that are uninstalled, you'll want to install them again after this. Copy them into a text file and save it.
Then restart your computer.
Does it boot and can you still connect to the net? Great!
Install what you just uninstalled.
In terminal:
```
sudo apt-get install *****the items you uninstalled, pasted here without stars******
```
Then restart.
Did it work? 
If it didn't, I think you have a problem with Dbus. 
I have no useful advice for that, I'd recommend reinstalling Ubuntu as I initially said.


Please let me know what your situation is, this kind of problem is so common that i'm trying to get a decent "Fix Networking With A Sledgehammer" guide put together.

---

### Post by plh on 2009-12-17
In fact nm-applet can be started from the command line, but the applet won't show up in the panel...
When I start it from the command-line, it gives the error message I wrote in my first post

---

### Post by plh on 2009-12-17
> **peepingtom said:**
> 
Did you upgrade from Jaunty?

Yes 

Does networking function properly when you boot to a liveCD?

Yes

If so, this is some sort of configuration issue, things like this happen during Ubuntu upgrades, often as a result of changes you made to your previous install. Not your fault, it happens :)  If you want a really easy solution that fixes it with a sledgehammer rather than a scalpel, back up your files and reinstall. The problem shouldn't reoccur.

Yes, I think you're right. But this is precisely what I'd like to avoid, it makes me feel like if I was using window$ ;-)



A slightly more precise way to fix it, but still very blunt:
This will allow you to connect to the net without using NetworkManager.
You can then purge your system of NetworkManager, and reinstall it. It will then likely have a working configuration.

Connect you computer to your router using an ethernet cable.
I assume it has DHCP, meaning that it gives your computers an IP whenever you plug them in.
This is most likely the case

So, on your broken Ubuntu computer:
Open a terminal
Configure your network using /etc/network/interfaces 
```
sudo gedit /etc/network/interfaces
```
add the following lines ```
auto eth0
iface eth0 inet dhcp
```
Save and exit. Restart your computer. Does it connect to the net? Great! Proceed...


Yes I had access to the next thanks to a cable, that's what I used to post my problem ;-)

In terminal:
Uninstall NetworkManager's components, along with its configuration files and any programs that depend on it.
```
sudo apt-get purge
```
Please make note of the additonal things that are uninstalled, you'll want to install them again after this. Copy them into a text file and save it.
Then restart your computer.
Does it boot and can you still connect to the net? Great!
Install what you just uninstalled.
In terminal:
```
sudo apt-get install *****the items you uninstalled, pasted here without stars******
```
Then restart.


OK, I try it and let you know

Thanks anyway!


An easy way to back up files without another disk is to just rename your user folder, delete everything else and reinstall your OS without formatting. 
I'm going to post an easy guide on how to do this above in a couple days. It really makes reinstalling easy, and on home systems run by people who don't really want to learn a whole lot about Linux's underpinnings, it saves a lot of time. The basic process is boot to a liveCD, mount your local disk. Run nautilus as sudo, browse to /media/yourdisk/ and rename /media/yourdisk/home. Delete everyting except this renamed folder. Then reinstall Ubuntu, without formatting your disk. When you're reinstalled, run nautilus as sudo and move your files into your new home folder. Make sure to move only the hidden files you need, like .mozilla etc. To show hidden files in nautilus, press ctrl+h.

Thanks again, I let you know

---

### Post by plh on 2009-12-17
It worked! :)
Many thanks to both of you, I would have been very disappointed if I had had to reinstall my OS ;-)

Hope I can help in some way in the future!

:lolflag:

---

### Post by peepingtom on 2009-12-17
Great, this will now be my generic answer to NetworkManager problems :D
Just make sure to remove those lines from /etc/networking/interfaces if you ever want NetwoekManager to control your ethernet port.

---

### Post by MaindotC on 2009-12-17
Actually I did most of the work so I wouldn't be giving peepingtom very much credit.

---

