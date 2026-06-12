---
title: "Network Manager acts disconnected"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by stevo1977 on 2009-04-20
Howdy, all.  So I was very stoked when my wireless card and network were detected immediately after installation of ubuntu 8.10.  Unfortunately, I noticed that I was getting ridiculously slow download speeds while trying to get all my program and package updates (no more than 40kbps, and averaging around 10kbps on a DSL connection where I usually get around 140kbps).  Needless to say I was a bit annoyed by this.

Through some searching I found out that some configuration or other was setting my rate to 1Mb/s.  Using "sudo iwconfig wlan0 rate 54Mb/s" I was able to correct this odd setting, and my connection was back to normal.

Naturally, I don't want to have to open a terminal and type this command every time I reboot, so I sought a method by which I could fix the basic problem.  I found some posts suggesting editing the "/etc/network/interfaces" file to do this, but here are the contents of that file:

>>>>>>>>>>>>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
>>>>>>>>>>>>

As you can see, there is no mention of 'wlan0,' and adding entries to that effect simply resulted in Network Manager refusing to do anything.

I have ruined my fair share of Linux installations, so I knew enough to back up that interfaces file before editing, and promptly restored it when the 'fix' didn't.

But then a weird thing happened: when I restarted, the nm-applet decided that networking had been disabled.  I tried unchecking and rechecking the "Networking" & "Wireless" boxes, and then went into configuring my connections.  As soon as I entered my password (upon completing my edits), the connection automatically started up.

This lead me to believe it was a keyring issue, but I haven't been able to find any joint references to the gnome-keyring and Network Manager in System > Preferences or System > Administration.

So my queries are twofold:
- Any other suggestions about permanently setting my wireless rate to 54Mb/s?
- Any way to return Network Manager to auto-connecting my wireless (even with the keyring prompt)?

Thanks for any help at all.

---

### Post by celthunder on 2009-04-20
/etc/network/interfaces add 



auto wlan0
iface wlan0 inet dhcp
wireless_essid ssidofyourrouter
#wireless_key "keyhere" (put if needed)
up iwconfig wlan0 rate 54M

if you dont want dhcp set address/broadcast/subnet like normal

---

### Post by stevo1977 on 2009-04-20
celthunder,

Thank you very much for the quick and helpful response.  I added the suggested lines to my 'interfaces' file, and it appears to have worked.  The reason I say 'appears' is because the nm-applet is acting like it's disconnected and when I click on it, no wireless connections are detected.  However, I'm using the internet right now, the ping on google.com worked fine, and I checked iwconfig and the rate indeed started up at 54Mb/s.  Any idea why nm-applet is confused?  Any other info I can provide?

Thanks again for the detailed and instructive response.

---

### Post by celthunder on 2009-04-20
Not sure why, I don't ever really use the network manager.  I have a wireless card that doesn't work right in the network manager either.  I'm using the wired connection atm though so maybe that has something to do with it.  Glad you got your internet working at least, maybe someone else know's what is wrong with the network manager.

---

### Post by t0mppa on 2009-04-20
The problem is that you're using the /etc/network/interfaces file to determine your network settings. From what I've gathered, at least on Intrepid (probably on older versions as well) Network Manager is by default in Unmanaged state, where it ignores all interfaces set up in the interfaces file. For more information, see: /usr/share/doc/network-manager/README.Debian

---

### Post by stevo1977 on 2009-04-20
Well, I read the suggested readme.debian (thanks t0mppa), and it seemed pretty straightforward.  I went into the /etc/NetworkManager/nm-system-settings.conf, found the entry

[ifupdown]
managed=false

and changed it to true.  Then I executed "sudo killall nm-system-settings" as suggested by the readme.  However, that just succeeded in removing all functionality from the Network Manager.  It wouldn't connect to the default wireless connection (I would click on the panel icon, then click on my essid, and a notification would pop up that said the connection had been disconnected), but it had added an entry in the wired connections of "ifupdown(wlan0)."  Even after a reboot Network Manager wouldn't connect to anything, automatically or manually.

So I restored the nm-system-settings.conf, rebooted again, and the wireless is functioning again.  The icon in the panel is telling me it's disconnected, but all the diagnostics I run from the terminal tell me it's working fine (including rate=54Mb/s, which was my original goal, thanks again celthunder).  Plus, it autoconnects w/o prompting me for my keyring password, which is a nice bonus.

I am not too stressed about the nm-applet icon weirdness; the only thing I don't have are those nice blue bars to show me how poor my signal really is.  Thanks for helping me get this straightened out, guys.  Have a good one.

---

### Post by stevo1977 on 2009-04-25
Unfortunately, that fix was not satisfactory.  A few days ago I lost the connection for no apparent reason.  Since Network Manager was not detecting any networks, I could not try to reconnect.  I went into /etc/NetworkManager/nm-system-settings.conf and changed the 'managed' option to 'true.'  So now the Network Manager works again, but it won't autoconnect to anything, and when I trick it into connecting it's back to the default 1Mb/s.

Here are the contents of some informative files:

[Results of lspci -vnn]:
>>>>
01:08.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
	Subsystem: Linksys Device [1737:0032]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdefe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: rt2500pci
	Kernel modules: rt2500pci
>>>>

[/etc/NetworkManager/nm-system-settings.conf]:
>>>>
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
>>>>

[/etc/network/interfaces]:
>>>>
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# wlan0 configuration
auto wlan0
iface wlan0 inet dhcp
wireless_essid 2WIRE953
wireless_key "5622508638"
up iwconfig wlan0 rate 54M
>>>>

Another forum suggested adding the line "iwconfig wlan0 rate 54M" to the /etc/rc.local script.  What do you guys think?

I recently found the CD for my wireless card (WMP54G v4.0).  Should I try to install those drivers via ndiswrapper?  I'm a little wary of that, just because my wireless works now, except for all the terminal trickery I have to do every time I reboot.

Thanks for any help and/or suggestions.

---

### Post by racerraul on 2009-08-25
Was a solution ever reached?

I have the same problem with a wireless connection that has suddenly refused to stop auto-connecting after a reboot.

I have to edit the connection details for the wireless adapter in the nm-applet enter the su pw before it connects.  Very annoying.

---

### Post by stevo1977 on 2009-08-25
Nope.  I still have to use my root password every time I start up to unlock the default keyring.

I did end up putting together a script that will force my wireless connection to run at 54mb/s (as opposed to 1mb/s), but I have to run that at startup manually as well, since it requires root privileges.

---

