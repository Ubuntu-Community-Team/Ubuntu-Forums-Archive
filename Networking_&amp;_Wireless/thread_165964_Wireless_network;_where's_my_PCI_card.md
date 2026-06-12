---
title: "Wireless network; where's my PCI card?"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2006-04-25
Hi, all.

I've been working through [this set of instructions]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29") to try to get my NetGear WG311v3 card working.

I get as far as:
# ndiswrapper -i WG311v3.INF
Installing wg311v3

Check it:
# ndiswrapper -l
Installed ndis drivers:
wg311v3 driver present

Should it have reported that the hardware was present, too?

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82815 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:01.0 Non-VGA unclassified device: Gammagraphx, Inc.: Unknown device 82b0 (rev 08)
0000:01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

I don't see the wireless card there, and network-admin just shows me the onboard wired ethernet interface.

What else can I do?


Beef.

---

### Post by KLineD on 2006-04-25
For the card to be picked up by network-admin look inside the /etc/network/interfaces file and see if there's an entry for any other card besides lo and your wired nic (mine was listed as ath0)

If there is, comment it out. Restart network-admin (or just relogin to your session) and it should be listed.

As for not being listed in lspci well.. I really don't know. :-k

---

### Post by Keith_Beef on 2006-04-26
[QUOTE=KLineD]For the card to be picked up by network-admin look inside the /etc/network/interfaces file and see if there's an entry for any other card besides lo and your wired nic (mine was listed as ath0)

If there is, comment it out. Restart network-admin (or just relogin to your session) and it should be listed.


As for not being listed in lspci well.. I really don't know. :-k[/QUOTE]


Here it is:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.2
        dns-search localnet.net

auto eth0

```

So, I booted the machine this morning, commented out that last line, did modprobe ndiswrapper again, and no joy.

I had a look at the BIOS to see if the PCI slots had somehow been disabled, but didn't see anything like that.

Maybe there is something I need to do in there. This is a quite old computer; an HP Vectra that I found sitting in the garage (abandoned by a previous tenant). There was no hard drive in it. This computer has three PCI slots, and the third has a PCI riser in it. It must have had a card in at sometime, because one of the caches in the back plate had been removed. I put the wg311v3 card in that slot.

Are there any other PCI probing tools I could use to find out if the hardware is working, i.e. if the slots are OK?

Beef.

---

### Post by Keith_Beef on 2006-04-26
Still trying with this...

The computer won't boot if the PCI riser is not present; the POST stops with an error, and I cannot disable this check.

Physically, the metal framework around the riser prevents the wg311v3 PCI card from occupying slots PCI2 and PCI3; it can only go in one of the three slots of the riser (which occupies PCI1) (riser slots are labelled PCI11, PCI12 and PCI13).

I've tried the card in all three riser slots; no change in lspci output.

But I just discovered a tool called "hal-device-manager". Surprise! This can see the card, and recognize the vendor, but not much else. I suppose the card is too recent to have been put into the databases.

I don't see how I can dump the text from "hal-device-manager", so I've attached a screen-shot.


Beef.

---

### Post by Keith_Beef on 2006-04-28
I just had an idea!

Looking at the output from "hal-device-manager", I tried using the hex values given as "pci.product_id" and "pci.subsys_product_id", as shown highlighted in the screen-shot attached to this post.
# ndiswrapper -d 82b0:6b00 wg311v3

Driver 'wg311v3' is used for '82B0:6B00'
# ndiswrapper -l
Installed ndis drivers:
wg311v3 driver present, hardware present

Wow! Now I get the report that both driver and hardware are present.

Now, when I run network-admin I can see an entry for the wireless NIC, too!

Looks like a step in the right direction.

Beef.

---

### Post by Keith_Beef on 2006-04-29
Done it! It works.

So here, in detail, is the method.

Mount the CDROM (supplied with the card) containing the drivers. Go to the directory containing the Windows 2000 drivers. (I had read that the WinXP drivers didn't work; I didn't test them.) 

```
mount /cdrom
cd /cdrom/Driver/Windows\ 2000/

```


Tell ndiswrapper to use this driver to drive the PCI card 82b0:6b00 and to automatically do this at boot time in the future.

```
ndiswrapper -d 82b0:6b00 wg311v3
ndiswrapper -m

```


Now, in network-admin, I made sure that eth0 and wlan0 were down before setting the ESSID to the same string as that announced by the router (I did this once while wlan0 was up and the machine hung).

Still in network-admin, I set the static IP address, subnet mask and gateway address.

Then still in network-admin, I activated wlan0.

Next stop, I suppose, is getting WEP or some other sort of security going.


Beef.

---

### Post by Keith_Beef on 2006-04-30
Now, the wireless link seems to be working more or less as it should, with the slight hiccup of me having badly configured the DHCP server in the router, while having static IP addresses set by each host.

I sorted that, and then sorted another problem with the firewall rules (dropping packets that really shouldn't have been dropped).

But I have to bind the driver to the device (is that the right terminology?) and load the ndiswrapper module "by hand" after each boot. 

When I do this:

```
ndiswrapper -d 82b0:6b00 wg311v3
ndiswrapper -m
```

I get a reply that "modprobe config already contains alias directive". 

What can I do to fix this, so that wlan0 starts at boot time?

Now, about security.
I wanted to secure the link between the router and porter, but I'm unsure how to do this.

A first, though small step, was to change the SSID on the router, and to not broadcast it. But that still doesn't encrypt the exchange of data.

I wanted to set up WEP, or maybe WPA-PSK with TKIP. But looking in network-admin, I can only see a field to define a single WEP key and a switch to define whether the key is hex or plain text.

Beef.

---

### Post by Keith_Beef on 2006-05-01
[QUOTE=Keith_Beef]But I have to bind the driver to the device (is that the right terminology?) and load the ndiswrapper module "by hand" after each boot. 

When I do this:

```
ndiswrapper -d 82b0:6b00 wg311v3
ndiswrapper -m
```

I get a reply that "modprobe config already contains alias directive". 

What can I do to fix this, so that wlan0 starts at boot time?[/QUOTE]

It seems that all I need to do is to stop banging away at the problem, sit down and post here, and suddenly things become clearer in my head and I can fix the problems myself...

All it took to get wlan0 up at boot time was to add this line to the /etc/modules file:

```
ndiswrapper
```


Beef.

---

### Post by Keith_Beef on 2006-05-01
That's it. WEP encryption is working.

It might sound like no big deal to many of you, but it made me happy.


So I followed the instructions on [this page]("https://www.wireless.org.au/~jhecker/wepgen/index.php") on generating a random stream of hex values to serve as a key.

I tried generating a 64 bit value, but the NetGear router only wanted ten hex digits for a 64 bit encryption.

I'm obviously getting confused here, since I though I would need a 64-bit key for 64-bit encryption, but there it is. 

I entered the same key in the "WEP Key" field in network-admin as in the router's configuration dialog.

It works. I'm happy.

Now the Ubuntu box can move out of the basement, and up to the living room to be connected to the stereo.


Beef.

---

### Post by Keith_Beef on 2006-05-04
I broke it.

I don't know why, but since I tried using wifi-radar to test for any other networks within range, I can't get my own network to work again.

Every time I try to connect to my own network, either with network-admin or with wifi-radar, the computer hangs.

The machine also hangs when shutting down. It gets as far as "stopping wifi-radar daemon". So this is probably what is causing the other hang, too.

Beef.

---

