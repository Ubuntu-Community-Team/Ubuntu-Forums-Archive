---
title: "How to set up wireless on a Compaq D150"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by dubois.ford on 2009-02-23
Hello All,
I am new to Linux/Ubuntu. I installed it on my compaq D150 desktop. When I had windows, I was able to simply plug in my linysis USB wireless adapter and the pc would auto connect to the network. The USB adapter does not appear to work with Ubuntu. What do I need to do to set up wireless on this desktop? I have Ubuntu 8.10

Thanks,
Ford

---

### Post by Miguel on 2009-02-23
Hello dubois.ford,

First, do you know the chipset used by that Linksys adapter? If not, it would be very useful if you gave us the full model name/number so that google can help us. One thing you can do to check whether your USB adapter is recognice is opening a terminal (Applications -> Accesories -> Terminal) and, after inserting the adapter and waiting for a few seconds, issue the command
```

lsusb

```

This will list all the USB stuff that linux detects in your system, and you should see something about Linksys. Also, if after that you post here the output of the command
```

dmesg | tail -20

```

It should also help us. Anyway, after a while, you should be able to left-click in the NetworkManager icon (the one with computers in the top right corner of the screen) and see the available networks. Click on the one you want to connect.

---

### Post by dubois.ford on 2009-02-23
Hello Miguel,
I though I had a linysis adapter but it is actually a netgear USB adaptor. The model number is WG111

I typed it that command and it looks like it is recognized:

```

ford@ford-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This is the 2nd command

```

ford@ford-desktop:~$ dmesg | tail -20
[ 1478.407358] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 2378.064287] usb 1-4: USB disconnect, address 3
[67268.308885] type=1505 audit(1235166698.976:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=8518
[67268.570402] type=1505 audit(1235166699.236:6): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=8523
[67268.573469] type=1505 audit(1235166699.240:7): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=8523
[332523.287932] UDF-fs: No VRS found
[332523.330716] ISO 9660 Extensions: Microsoft Joliet Level 3
[332523.378521] ISO 9660 Extensions: RRIP_1991A
[332609.200019] usb 1-4: new high speed USB device using ehci_hcd and address 4
[332609.352561] usb 1-4: configuration #1 chosen from 1 choice
[332609.725962] phy0: Selected rate control algorithm 'pid'
[332609.837604] phy0: hwaddr 00:1f:33:7b:67:19, RTL8187vB (default) V1 + rtl8225z2
[332609.838069] usbcore: registered new interface driver rtl8187
[332622.633677] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[332625.584808] wlan0: authenticate with AP 00:1f:33:3b:2f:b0
[332625.589981] wlan0: authenticated
[332625.589992] wlan0: associate with AP 00:1f:33:3b:2f:b0
[332625.594238] wlan0: RX AssocResp from 00:1f:33:3b:2f:b0 (capab=0x401 status=0 aid=4)
[332625.594247] wlan0: associated
[332625.595137] wlan0: disassociating by local choice (reason=3)
```


Any Suggestions?

-Thanks

---

### Post by dubois.ford on 2009-02-23
It started working!! Maybe it was working all along. I clicked the network connection icon and the ssid's appeared.

Thanks,

---

### Post by Miguel on 2009-02-23
Okay, thanks for the info you provided. As you guessed, the USB WiFi dongle is correctly recognised and, according to the dmesg output (well, the last 20 lines, that's why we used "tail -20"), your adapter is using the Realtek 8187 chipset (I've seen that there is another version of your adapter using the Prism 54 chipset). I think that both versions should work with Ubuntu 8.10 without much issues.

Those were the good news. I'm actually puzzled with the last dmseg line, the one saying "wlan0: disassociating by local choice (reason=3)"

Anyway, let's see if you can see any WiFi networks with your adapter. After inserting the adapter and waiting for a short while, please left-click on the computer icon on the top right corner. You should see a list of the detected WLANs. Could you put the output of the command...?

```

iwconfig

```

The alternative, if this icon doesn't seem to work, is typing again in a terminal (you will be asked your password):

```

sudo iwlist wlan0 scanning

```

I'll also put the manual mode (i.e. using the command line, which I have almost never done) to connect to your ESSID. I'm not 100% sure it will work though, but you may want to try it. Note that the "" are needed characters! Just put the name in there.

```

sudo iwconfig wlan0 essid "put-your-essid-here"

```

BTW: To what kind of network are you trying to connect? Unencrypted, WEP or WAP?

---

### Post by Miguel on 2009-02-23
LOL, 8 minutes late! 

I'm glad it works. In case you have problems and your connection drops, you may want to install linux-backports-modules-intrepid. This package usually updates wireless drivers, which may be interesting for your adapter. And keep posting!

---

### Post by dubois.ford on 2009-02-23
Where can i download "linux-backports-modules-intrepid?" One think I noticed is that although I am able to connect, the signal strength is very low. The signal strength is only 24% and my  wireless router is right next to the desktop/USB wireless adaptor.

---

### Post by Miguel on 2009-02-23
> **dubois.ford said:**
> Where can i download "linux-backports-modules-intrepid?" One think I noticed is that although I am able to connect, the signal strength is very low. The signal strength is only 24% and my  wireless router is right next to the desktop/USB wireless adaptor.

If you have access to internet in linux (which it seems you have), just open the package manager in System -> Administration -> Synaptic Package Manager, and once there search for "linux-backports-modules-intrepid". You should easily find it. Double-click on it, and you will be told that a couple more packages need to be installed. Just accept and hit apply. It will downoad and install all the needed stuff for you.

If you can't surf in linux, tell me and I'll put direct links for the needed stuff.

BTW: I don't know how long have you been in linux but at the risk of sounding patronising, I'll say this is the recommended way of installing stuff. Look for the programs you need, double-click, and let synaptic do its magic. You can also remove programs from here, but be careful ;-)

---

### Post by dubois.ford on 2009-02-24
Hello Miguel,
There are 3 versions of "linux-backports-modules-intrepid" which are:
generic
server
virtual

Which one do I need for my desktop?

---

### Post by laithbsoul on 2009-02-24
i'd say generic then again you could install all of them it would not hurt lmao

---

### Post by Miguel on 2009-02-24
Plain "linux-backports-modules-intrepid" should do the trick. Else, always go for the "-generic" version.

---

