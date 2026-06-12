---
title: "What are the first basic steps to setup a wireless connection?"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by jlunse on 2010-08-07
I have a computer with both wire and wireless connections. Wired connection works fine, but I would also setup the wireless connection.
(I also have a dual boot on this cumputer with WinXP where both wire and wireless connections works fine. So, wire and wireless configuration of the actual router is not an issue here.)

I have newly installed ubuntu 10.04 for the first time, so this setup is new to me.

At this point I just want to know the main/overview basic steps of setting-up the wireless connection on the computer. Also if you could suggest any links to guidelines for these steps. I have been thinking about something simple like this, but I might have missed a lot:)

[LIST=1]
[*]Investigate if Ubuntu finds the wifi-hardware - the installed wifi card.
[*]Investigate if Ubuntu have an installed driver for this wifi-card.
[*]Configure the Wireless Network connection, like SSID.
[*]Unplug wire connection and reboot.
[/LIST]

Is this a good plan?

---

### Post by dineshs on 2010-08-07
first you need to post the output of ```
sudo lshw -C network
```Some cards will work via NM but some cards need ndiswrapper to be installed
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jlunse on 2010-08-07
I managed to identify the adapter and a also managed to install the Windows driver for it.
Refer to this thread: ["sudo lshw -C network" Can't find my wireless device (card)]("http://ubuntuforums.org/showthread.php?p=9691499#post9691499")

Secondly, configured my Network Manager and Wireless connection by just adding SSID and with no wireless encryption. Also with these settings:
- **Connect automatically** (enabled)
- **Mode**: Infrastructure
- **BSSID**:
- **Mac address**:
- **MTU**: automatic

Unplugged wired connection and re-started the computer.
No success, wireless network (SSID) is not found.

Then I had to reboot again a few times for some other reasons and **[COLOR="Red"]suddenly it finds the wireless netwok and it works just fine[/COLOR]** :) :)

**Summary**: Wireless PCI Card: WN4201B with Windows XP driver works fine in lubuntu 10.04!

I will also test the same in Ubuntu 10.04 and post the result here, later on.

---

