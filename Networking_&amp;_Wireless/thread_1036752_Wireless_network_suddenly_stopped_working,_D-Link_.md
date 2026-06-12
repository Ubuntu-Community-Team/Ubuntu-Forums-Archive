---
title: "Wireless network suddenly stopped working, D-Link DWA-111"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by Scarlath on 2009-01-11
Hello everyone!

Typing this from Windows XP on my dual-boot machine (Ubuntu 8.10 - Windows XP) using a wirless dongle called "D-Link DWA-111". 

When I first got Ubuntu I had another wireless adapter but it wouldn't really work, when I got a new one for christmas (for another reason though), the one I'm using now, it would work right away. No problems what so ever.

So I updated Ubuntu, got graphics drivers and misc applications and so on. About a week or so later, having done nothing special except of installing updates every now and then - I can no longer see any wireless networks. When I click the icon it says "Wireless Networks:" but there's nothing (networks) under it like there used to be, it's sort of greyed out.

I have tried using an older kernel but same thing happened there.

I believe the adapter uses the RT73 driver (not too sure though).

Anyone have any ideas how to fix this?

Thanks in advance!

---

### Post by Scarlath on 2009-01-11
Forgot to mention that the kernel I'm using is 2.6.27-9-generic (if it's of any relevance).

---

### Post by derouge on 2009-01-11
Paste the output of:

```
lspci | grep Network
```

I suppose it's also worth checking to see if your device is shown, maybe just not working:

```
iwconfig
```

You should have something like lo (loopback device), eth0 (ethernet), and one other (maybe wlan0?) which is probably your wireless card. Maybe paste that output here, too.

Check the module is loaded:

```
lsmod | grep rt73
```

Can you manually connect to a network? I think the network manager applet has an option for connecting to hidden networks or something like that which will let you fill in the details.

If not something like iwconfig *cardname* essid *network name* key *encryption key* channel *channel number*

One other question, is the network encrypted with WEP? WPA?

---

### Post by Scarlath on 2009-01-12
Thanks for the reply!

Here's the requested information:

```
**ludvig@ludvig-desktop:~$ lspci | grep Network**
ludvig@ludvig-desktop:~$ 

```

Seeing as the above didn't give anything I decided to post the entire lspci (without | grep Network).

```
**ludvig@ludvig-desktop:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
ludvig@ludvig-desktop:~$
```

However, as my network adapter is plugged in through the USB port, wouldn't "lsusb" be the appropriate command? Either way, here it is:

```
**ludvig@ludvig-desktop:~$ lsusb**
Bus 005 Device 002: ID 07d1:3c06 D-Link System 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ludvig@ludvig-desktop:~$
```

And the rest of the commands:

```
**ludvig@ludvig-desktop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=1 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ludvig@ludvig-desktop:~$ 
```

```
**ludvig@ludvig-desktop:~$ lsmod | grep rt73**
rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
usbcore               148848  5 rt73usb,rt2x00usb,ehci_hcd,uhci_hcd
ludvig@ludvig-desktop:~$ 
```

(as I said, I'm not sure if this is the driver (or is it chipset...?) it uses, but I *think so*, any way to check that...? EDIT: I think I found a webpage saying it uses that particular chipset, so.. yeah :p)

Thanks in advance!

---

### Post by derouge on 2009-01-12
Oh, didn't realize it was a USB dongle. Hehe. Ok, so it appears that the device is still "seen" by the system. That's good. Did you try connecting to the network manually? 

You can try scanning using the command "iwlist scan" (might be "iwlist wlan0 scan") and then running the command I gave you before:

iwconfig wlan0 essid NETWORK-NAME key ENCRYP-KEY channel CHANNEL-#

After that run:

dhclient wlan0

Also, is the network you're connecting to encrypted? If so, WEP or WPA?

---

### Post by Scarlath on 2009-01-12
Sorry, forgot to answer your questions when you asked for the commands and such, either way here the answers are:

> Can you manually connect to a network? I think the network manager applet has an option for connecting to hidden networks or something like that which will let you fill in the details.

I tried that, the icon spins around for a while then it just says "disconnected" (basically).
> 
You can try scanning using the command "iwlist scan" (might be "iwlist wlan0 scan") and then [...]:

*iwlist scan* returned "no networks found" (or something along those lines, cant remember exactly) on wlan1.

> One other question, is the network encrypted with WEP? WPA?

No, I'm not using any encryption.

Thanks in advance!

---

### Post by derouge on 2009-01-12
If you know the essid and channel of the network do this:

**iwconfig essid** *essid here* **channel** *channel # here*

Then do **dhclient wlan0**

---

### Post by Scarlath on 2009-01-13
Unfortunately I do not know my channel, I believe my router has it set to automatically assign one. :/

---

### Post by derouge on 2009-01-13
Do rmmod rt73usb. Then do modprobe rt73usb. Then paste the output of dmesg.

---

### Post by Scarlath on 2009-01-15
I'm really busy right now due to school and misc. things. I will try those instructions as soon as possible (most likely tomorrow or this weekend) and will then post here again. Thanks for the help so far :)

If anyone else have any more ideas how to fix this feel free to post!

---

### Post by Scarlath on 2009-01-16
Here's the output, I didn't get all of it it sorta scrolled everything out of the way so to speak. I will not post the entire output (seeing as that was probably 9 A4 pages). I dont think you need all of it anyway (if you do, please tell me so though :)):```
[   25.142467] firmware: requesting rt73.bin
[   25.365527] NET: Registered protocol family 17
[   29.793925] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   29.793934] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   34.403325] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   34.403334] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   65.133687] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[   65.133702] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[   79.638793] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   79.638807] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   86.228909] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   86.228923] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   87.325296] usbcore: deregistering interface driver rt73usb ***# This is probably where I did the rmmod, right?***
[   93.571444] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   93.571458] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   96.173234] phy1: Selected rate control algorithm 'pid'
[   96.175449] Registered led device: rt73usb-phy1:radio
[   96.176791] Registered led device: rt73usb-phy1:assoc
[   96.180464] udev: renamed network interface wlan0 to wlan1
[   96.182614] Registered led device: rt73usb-phy1:quality
[   96.183524] usbcore: registered new interface driver rt73usb
[  100.216274] firmware: requesting rt73.bin
```

Thanks in advance!

---

### Post by Scarlath on 2009-01-17
Just giving this thread a little push to the first page :)

---

### Post by Scarlath on 2009-01-18
... and again ;)

---

### Post by Scarlath on 2009-01-20
... and once again :(

---

### Post by Scarlath on 2009-01-21
Bumping this today again!

---

### Post by Scarlath on 2009-01-22
Not giving up on this! There's got to be *someone* with at least a theory!

---

### Post by derouge on 2009-01-23
[http://dreamlinuxforums.org/index.php/topic,334.0.html](http://dreamlinuxforums.org/index.php/topic,334.0.html)

Could try those instructions.

---

### Post by j7%&lt;RmUg on 2009-01-24
Iv just checked and it appears that your USB wireless card is not on the Supported Cards list. The list can be found [HERE.]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

If you want to check which other USB cards are supported find the USB section which is right at the bottom of the page.

I hope this helps.

Nisshh

---

### Post by krojc on 2009-01-24
Eee, I think I'm having the same problem.
Problems started at the same time, but I didn't think about it, since link is many times lost due to ISP problems. In the meantime, again not thinking about it, I purchased TL-W651G pci wireless, which was recognized during the first startup, got it confugured to work with wpa2, got connected to the router, but that's it. From then on, I never connected to wireless nor wired.

ifconfig shows ath0 wifi0 lo and eth0 configured correctly, starting ath0 or eth0 states, that the network is up ... settings are exactly the same as on windows xp where both wired and wireless work. I changed settings so many times that now I'm not sure which should work.

It also takes too much time to check the forum and search engines for ideas, then boot and then again ...

---

### Post by Scarlath on 2009-01-24
> **derouge said:**
> [http://dreamlinuxforums.org/index.php/topic,334.0.html](http://dreamlinuxforums.org/index.php/topic,334.0.html)

Could try those instructions.

I've been thinking of that but I mean... the driver (RT73) should already be built in, so I'm confused why it isn't working. If no one can come up with another solution though I guess I'll do the above. I'm also uncertain about different parts of that walkthrough, what exactly you're supposed to do and so on (e.g the following steps: "Open the rtmp_def.h file for editing (change the command to reflect the situation on your drive)", "Open the interfaces file for editing", etc.).

> **nisshh said:**
> Iv just checked and it appears that your USB wireless card is not on the Supported Cards list. The list can be found [HERE.]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

If you want to check which other USB cards are supported find the USB section which is right at the bottom of the page.

I hope this helps.

Nisshh

It worked right out of the box at first though, as I said. It uses the same chipset as e.g DWL-G122 (rev C) which is supported out of the box, etc. I don't see how it wouldn't be supported :o

> **krojc said:**
> Eee, I think I'm having the same problem.
Problems started at the same time, but I didn't think about it, since link is many times lost due to ISP problems. In the meantime, again not thinking about it, I purchased TL-W651G pci wireless, which was recognized during the first startup, got it confugured to work with wpa2, got connected to the router, but that's it. From then on, I never connected to wireless nor wired.

ifconfig shows ath0 wifi0 lo and eth0 configured correctly, starting ath0 or eth0 states, that the network is up ... settings are exactly the same as on windows xp where both wired and wireless work. I changed settings so many times that now I'm not sure which should work.

It also takes too much time to check the forum and search engines for ideas, then boot and then again ...

Yeah, I hear ya. It's really weird and time consuming. :(

Thanks for the help so far everyone!

---

### Post by Scarlath on 2009-02-01
<pokes this thread a little>

Is there really no other things to try than to build a driver by myself that is already included in the OS for an adapter that DID work for a while without having to do anything? :(

---

### Post by danielmelo on 2009-02-05
Same problem here. It works out-of-box, but slowly. After an update, stops working at all. Ndiswrapper doesnt work with windows driver. Any ideas?

---

### Post by Scarlath on 2009-02-07
> **danielmelo said:**
> Same problem here. It works out-of-box, but slowly. After an update, stops working at all. Ndiswrapper doesnt work with windows driver. Any ideas?

Well, you could always try what **derouge** posted [_here_]("http://ubuntuforums.org/showpost.php?p=6606895&postcount=17"). I haven't tried it myself yet though.

---

### Post by danielmelo on 2009-02-09
> **Scarlath said:**
> Well, you could always try what **derouge** posted [_here_]("http://ubuntuforums.org/showpost.php?p=6606895&postcount=17"). I haven't tried it myself yet though.
Thanks! I've tried. No luck...

---

