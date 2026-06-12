---
title: "Curious about the /etc/network/interfaces file"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by bdemers on 2010-11-13
Using 10.04 desktop.  I just took a peek at my interfaces file to discover that only the required loopback info is in place.  Eth0 (or anything for that matter) is not in the file.  I wonder about the mechanism with that.  Eth0 is in place, working just fine. Is dhcp controlled.  Shows up, along with lo in ifconfig -a.  I did find a file called eth0 in etc/NetworkManager it is not a text file, however. There is also a conf file called nm-system-settings that references only eth0's mac address.  So where else is the system getting its info from?  I think this would be a good thing for me to know.

---

### Post by uncaspi on 2010-11-13
If additional cards were listed in the interfaces file they are not handled by the network-manager.

---

### Post by chili555 on 2010-11-13
Network Manager has its own whole set of configuration files and will manage any interfaces that are *NOT* listed in /etc/network/interfaces. The /etc/network/interfaces file is part of the process to manually manage network interfaces. Network Manager is the automagic way.

If you have a stay-at-home desktop computer that you will not be lugging down to the library/cyber cafe/coffee shop, then it's perfectly reasonable to remove NM and populate the /etc/network/interfaces file, as I have done on three of my four computers.

Laptops, on the other hand, typically need to be carried around to other locations, find a network and connect with a minimum or no fuss. NM is one, but not the only way to accomplish this.

---

### Post by bdemers on 2010-11-13
OK, let's see if I'm getting this.  The interfaces file is a manual override and takes priority over the auto controls in "nm" .  If given sufficient justification I can assign eht0 thru eth(n) via the the interfaces file.

Where does the system map these values to the physical pci address.  I assume its by pci address that the system routes from eth(x) to the correct nic port. 

Suppose I had 4 nics, and for whatever weird reason I wanted to reassign eth0 from its current location to one of the other ports (why?, but let's say) I should be able to do that by altering the map. That map must be in a file somewhere.  And is it a text file? Is there more than one file I need to step on? If the nics are different, then drivers enter the picture, where does that fit in?  Same file, perhaps?

---

### Post by chili555 on 2010-11-13
The mapping is done and, with some care, can be adjusted in /etc/udev/rules.d/70-persistent-net.rules. It maps the MAC address, driver and interface names.

If you had four NICs, for instance, if you wanted to set up your old Pentium 2 as a router, firewall and server for your home use, Network Manager is not going to be your friend, only careful manual configuration will work.

I'm not sure I would describe /etc/network/interfaces as the manual override; rather, that the newfangled upstart Network Manager aims to automate the process for all the URANOOBs out there who came from the point-and-click GUI world and can't be troubled to learn what /etc files do and how to bend them to their supreme domination.

Oops! Sorry for the semi-rant.

Either system does the same exact thing. One is automagic and one is all manual.

---

### Post by bdemers on 2010-11-14
Here's a snippet from my /etc/udev/rules.d/70-persistent-net.rules file.


# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:8b:7e:2d:2d", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

I learned that DRIVERS=="?*" means that the driver info comes from 
/lib/udev/rules.d/80-drivers.rules :

 DRIVER!="?*", ENV{MODALIAS}=="?*", RUN+="/sbin/modprobe -b $env{MODALIAS}"

I have yet to figure out how to get to the modprobe listing file, if such a file exists. --help doesn't exist for modprobe, and honestly, that's all I've tried so far.  -C (with the file name) will list out the findings?  Back to discovering the filename.

It does appear that I can reassign eth(x) quite simply by altering the NAME parameter (keeping it kernel friendly, of course)

As far as changing anything other than the name, that all seems more academic than anything else.  Physical properties don't change just because you say they're changed.

Looking at modprobe, I think that could be interesting.

---

### Post by chili555 on 2010-11-14
modprobe is a command. It's found in /sbin/modprobe.

If you are wondering how modules get loaded automagically, they are referenced by the pci.id or the usb.id of the device and loaded dynamically. Here is an example from my computer:```
lspci -nn
--- snip --
Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [[COLOR="Red"]8086:4227[/COLOR]] (rev 02)
```Now the system looks for a module with 8086:4227 as a pci.id and finds this:```
modinfo iwl3945 | grep 4227
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]4227[/COLOR]sv*sd*bc*sc*i*
```It then loads, or modprobes *iwl3945*.

Sometimes, the system gets forgetful and we can explicitly load modules in /etc/modules. For example:```
cat /etc/modules
lp
coretemp
some_module
```We know this sytem works dynamically because a module will load immediately, assuming a module exists that recognizes the device, when we insert a PCMCIA or USB device, including mice, webcams and all sorts of devices.

Keep learning and I'll keep trying to explain.

My apologies to the purists who are scoffing at my simplistic explanation.

---

### Post by bdemers on 2010-11-14
I tried lspci -nn I found my network card, along with A value inside square brackets.  This is the pci.id? If I have 2 nics of same make and model will this value change on the second?  If its an address, then it should.

Moving on.
You wrote:

Now the system looks for a module with 8086:4227 as a pci.id and finds this:
Code:

modinfo iwl3945 | grep 4227
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*

I also ran modinfo iwl3945 | grep 4227, and got the same results you did.
This results makes me very curious.  the 8086:4227 can't be an address, well it could, but what kind of coincidence would that be?  Especially since I don't have a wireless adapter on this computer.
  
Another possibility would be that 8086:4227 is broadcast to the system from the card, the card telling the system who it is.  A list inside the driver, perhaps in a header? will qualify the driver for the announced hardware.

So, what exactly is 8086:4227?  My guess is manufacturer:model. (In your case Intel being 8086 -- follows)
I did find that /etc/udev/rules.d/70-persistent-net.rules file also gives this info along with the discovered driver name :# PCI device 0x14e4:0x170c (b44) in my case.
I also noted the module name (b44 in my case).  So I tried this modinfo b44 | grep 170c, expecting to see an alias pop back, but got nothing returned.  lsmod shows b44 as a loaded driver, and b44.ko is in the /lib/.../net/ folder.  Seems that should have worked.  I tried a search for 14e4 170c, but stupid me, did it as a text string.  What I need to do is convert the hex value 14e4 170c to its ascii eq and rerun the search.
Think I'll post this and then try that

---

### Post by chili555 on 2010-11-14
> I tried lspci -nn I found my network card, along with A value inside square brackets. This is the pci.id?Exactly so.> If I have 2 nics of same make and model will this value change on the second? No. It is, as you surmised, the manufacturer and model. Every Intel 3945ABG will have the same manufacturer and model. What *will* change is the MAC address:```
sudo lshw -C network
--- snip ---
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       [COLOR="Red"]serial: 99:19:d2:c2:1b:88[/COLOR]
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945
```As you can see from /etc/udev/rules.d/70-persistent-net.rules, the MAC address is part of the map.> Another possibility would be that 8086:4227 is broadcast to the system from the card, the card telling the system who it is. A list inside the driver, perhaps in a header? will qualify the driver for the announced hardware.More or less correct; not so much broadcast as read by the system. Yes, the list is inside the driver, including Windows .inf files.> So I tried this modinfo b44 | grep 170c, expecting to see an alias pop back, but got nothing returned.Please try:```
modinfo b44 | grep 170C
```The alias values are upper case; coincidentally, I used a pci.id without letters, so that wasn't illustrated.> I tried a search for 14e4 170c, but stupid me, did it as a text string.I am not sure where you searched, but check here:

[http://www.google.com/linux?q=14e4+%3A170c&sourceid=mozilla-search](http://www.google.com/linux?q=14e4+%3A170c&sourceid=mozilla-search)

Searching for the pci.id or the usb.id to try to figure out what driver drives what card is a tool I use every day to help me answer posts here.

---

### Post by bdemers on 2010-11-14
aha! There you go.  upper case it is.  I was doing a standard gnome (nautilus) file search. Never considered Google.  Why not I wonder?

---

### Post by chili555 on 2010-11-14
You could be a real terminal geek and make grep insensitive to case:```
modinfo b44 | grep -i 170c
```To see the whole list of aliases, simply run:```
modinfo b44
```Compare the long list of aliases for some chipsets that have been re-branded by many different vendors:```
modinfo rt2870sta
```

---

### Post by bdemers on 2010-11-15
Chili555 thanks so much for the pointers.  I am going to take what we've discussed to a test computer that I have and mess with this a bit.  It's a Dell2650, 3 onboard ports, 2 general purpose and 1 for the opsys, set up in the bios.  In addition I have 2 dual Pro100 cards, one Intel, one Compaq banner.  Be interesting to see how the system selects drivers and assigns logical names to each port.  What I haven't seen yet is a listing of the pci addresses.  That info may hold a clue as to how (in what order) each peripheral device is cataloged.
Labeling each port is certainly doable with the info currently obtainable by me, having the pci address doesn't improve on that.  I will need to do some manual probing (tracert, ping, whatever) to sort out the duplicate ports.  The pci address thing is just so I can see how the system relates to physical conditions.

Thanks again for you time.  Great!!!!

---

### Post by chili555 on 2010-11-15
The PCI addresses are, I think, the bus number; viz:```
lspci -nn
[COLOR="Red"]00:00.0[/COLOR] Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
[COLOR="Red"]00:01.0[/COLOR] PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
--- snip ---
[COLOR="Red"]02:00.0[/COLOR] Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
[COLOR="Red"]03:00.0[/COLOR] Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
---snip ---
```Have fun and report back so we may learn from your success.

---

