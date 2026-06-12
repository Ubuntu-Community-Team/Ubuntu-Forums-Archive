---
title: "Zonet ZEW2500P (RT73) no drivers found?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by khughitt on 2009-09-30
Hello all,

I recently purchased a Zonet ZEW2500P external USB wireless adapter to use in Ubuntu 9.10 (2.6.31-10-generic-pae 32-bit), but have been running into issues getting online. 

When I plug-in the device and run lsusb, it shows up fine:

```

lsusb
...
Bus 001 Device 006: ID 148f:3070 Ralink Technology, Corp.

```

When checking to see which driver it is using, however, none are listed:

```

lshw -C network

  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:a1:b0:c0:2b:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

```

I am also not able to find any wireless networks, either using NetworkManager, or on the command-line:

```

iwlist wlan0 scan
wlan0     No scan results

```

Any suggestions as to how to get things working? 

I've read several threads relating to this device, most of which are over a year old, however, the posts all suggest that the wireless drivers should be supported out-of-the-box starting around 8.04.

Any suggestions would be greatly appreciated.

Thanks!

---

### Post by Alpinist on 2009-10-10
I just got one of these along with a nettop pc and after going through a bunch of posts of getting it running decided to use ndiswrapper.

Followed the instructions on the community document page

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Got the windows drivers by running the set up CD that came with the zonet card in a VM with XP on it.

This card is not supported out of the box as far as I can tell.  At least it is now working for me.

---

### Post by Alpinist on 2009-10-10
OK, I found a better native solution that is somewhat easier.  (Though far from out of the box)  There are long threads on this topic with lots of confusing posts.

Here's what I did:

1: rt2870sta is already installed with 9.04.  I just did a "sudo modprobe rt2870sta" to enable it.  (You can make this automatic on boot by adding rt2870sta to the end of the /etc/modules file.)

2: type the command "sudo ifconfig ra0 up"  You can just type "ifconfig" to verify ra0 is in the list of interfaces.

3: install wicd.  This removes the default network manager.  In the preferences for the wicd manager I set wireless interface to ra0 and ran a refresh and my networks showed.

I did a reboot to verify everything is working still and all is good.

---

### Post by Alpinist on 2009-10-10
I haven't tried 9.10 yet but I've seen some posts that suggest you may need to blacklist rt2800usb in karmic

---

### Post by itsjareds on 2009-10-11
Perfect. Actually in Jaunty I had to install the rt3070sta driver manually from ralink, and it worked fine. I tried installing from source again in my new Karmic installation and I get compile errors.

I think the issue may be blacklisting that 2800usb driver. Thanks

---

### Post by arrrghhh on 2009-10-16
Evidently I have this same chipset (148f:3070) is what I get for my wifi card with lsusb.

I've tried everything, and using modprobe to enable the rt2870sta driver shows some networks, but I can't ever connect.  Compiling manually doesn't work, I've tried the newest 2.2.0 drivers from ralink, and it fails, error 2 on the the make.  I've installed linux-headers-`uname -r` and build-essential.  Maybe I'm missing something?  I really want this wireless card to work!  Thanks!!

---

### Post by itsjareds on 2009-10-16
Yeah, compiling from the source gives make errors for me too. Try this:
```
sudo rmmod rt2800usb
sudo modprobe rt2870sta
```

Then unplug and replug your adapter, it should be detected so then try to connect to your network.

If this all works, then blacklist the rt2800usb module with this line:
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Your adapter should now work across reboots.

---

### Post by khughitt on 2009-10-16
> **itsjareds said:**
> Yeah, compiling from the source gives make errors for me too. Try this:
```
sudo rmmod rt2800usb
sudo modprobe rt2870sta
```

Then unplug and replug your adapter, it should be detected so then try to connect to your network.

If this all works, then blacklist the rt2800usb module with this line:
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Your adapter should now work across reboots.

Worked perfectly! Thank you :)

---

### Post by arrrghhh on 2009-10-17
[quote=arrrghhh]using modprobe to enable the rt2870sta driver shows some networks, but I can't ever connect.[/quote]

i've tried that.

for *some* reason it does actually show networks, unlike the rt2800usb driver which shows nothing.  but it doesn't show all of 'em (there's an unsecured apple network that always shows up, and is always a good test... but it never shows with this card) - it does show my network, however with wpa2 it doesn't connect, and i've tried disabling the security entirely, still doesn't want to connect!  this is frustrating, as the card works flawlessly in win7, i didn't even have to install any drivers.  so i know the hardware is fine.

i'm not sure what else to do at this point... maybe it's the 3070 driver i need?  i'm not sure.  my chipset id matches the one in this thread, that's why i was hopeful.

ALRIGHTY THEN!!  I tried the RT3070STA driver on a whim, and I get it to connect... Having issues with my WPA2 network, but I'm going to try it again real quick... Don't know why I didn't try that one in the first place!!

And I can connect if I turn off the security, but if I have the WPA2 passphrase enabled, I can't connect?  Any ideas why?


Well I switched the security to WPA2 Personal "Mixed" and changed the algorithm from TKIP+AES to just TKIP... and now it works!  I'd like to know why this works, I'm going to do some research on this chipset... I'm just glad at this point that I got it working at all!

---

### Post by ifraser on 2009-10-30
The card worked out of the box for me in 9.04 but was nonfunctional immediately after upgrading to 9.10.  

Blacklisting rt2800usb did the trick and it is now working with the much-besmirched Network Manager - no WCID necessary.

Thanks for everyone's input and help.

---

