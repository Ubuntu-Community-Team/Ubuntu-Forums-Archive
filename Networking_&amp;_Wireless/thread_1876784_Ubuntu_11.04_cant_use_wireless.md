---
title: "Ubuntu 11.04 cant use wireless"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by Peter Parkorr on 2011-11-06
Hi, my wireless connection is very shaky, when I first boot my laptop I can use wireless for a minute or two before pages take too long to load and I get 'taking too long to respond' messages from firefox.

I've read other threads but haven't managed to fix it. Using 'sudo modprobe ath9k' seems to give it a jolt for all of ten seconds but then it fails again. I also removed network-manager and installed wicd but that is worse.

How can I fix it?

Thanks

---

### Post by carverj on 2011-11-07
Do you get a good signal where the computer is located? And no metal obstructions messing with your connections?
If not, take a look at handy troubleshooting guide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Peter Parkorr on 2011-11-07
> **carverj said:**
> Do you get a good signal where the computer is located? And no metal obstructions messing with your connections?
If not, take a look at handy troubleshooting guide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)


Thanks. The signal varies, it's good (and browsing is fast) when I first connect but then the signal reduces quickly and usually stops working. When booting into win7 I don't have any problems with wireless.

I remembered that in another location changing encryption to WPA2 helped so I have done that, doesn't seem to have helped much. (from a similar thread about the ath9k driver)

Shane

---

### Post by Peter Parkorr on 2011-11-09
Bump.

Any ideas out there? I hate having to revert to windows for net access...

Shane

---

### Post by carverj on 2011-11-22
What is the wifi card you are using and have you checked if it is fully supported in Ubuntu 11.04?

---

### Post by Peter Parkorr on 2011-11-30
> **carverj said:**
> What is the wifi card you are using and have you checked if it is fully supported in Ubuntu 11.04?

Hi carverj,

Thanks for the suggestion, I havent checked it specifically til you mentioned.

It is the Atheros AR5B97 but I can't find a reference to it on the community WifiDocs/WirelessCardsSupported page.

Anywhere else I can look?   (Its not on the free software foundation list either).

It is an Atheros chip with 802.11n support so wikipedia says it should be supported. 
When I run "sudo modprobe ath9k" it livens up for a minute or 2 but quickly drops off again.

Peter

---

### Post by carverj on 2011-12-01
Perhaps Ubuntu doesn't support that as I read a post from person with acer aspire 1830T at [http://ubuntuforums.org/showthread.php?t=1751134](http://ubuntuforums.org/showthread.php?t=1751134)
and they didn't seem to have a lot of luck getting it going.

I would test with live CD, Ubuntu and also other flavours also and see if works.

---

### Post by 3rdalbum on 2011-12-01
There's something else you could try doing.

Usually a wireless card will try to connect at the fastest speed possible, and then drop down to a lower speed if the conditions are bad and too much data is being lost.

It's possible that the "drop down" is not happening as it should, or even just that the connection is not reliable enough at the higher speed to even negotiate a lower speed of transfer.

As **soon** as you connect, try running this command:

```
sudo iwconfig wlan0 rate 5.5M
```

(assuming your wireless card is 'wlan0' - it might be 'ath0' or 'wlan1'. And that's a zero, not a capital o).

This command will lock your wireless card to 5.5 megabits per second until reboot; fast enough for decent internet browsing but also fairly reliable.

If 5.5M works, try some bigger values such as 11M or 25M and see if they help.

As mentioned before, rebooting will put this setting back to its default "auto".

---

### Post by mörgæs on 2011-12-01
Moved to Networking and Wireless.

---

### Post by praseodym on 2011-12-01
Try to deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Peter Parkorr on 2011-12-01
Thanks for the suggestions 3rdalbum and praseodym.

Actually my  housemate had a new broadband service installed yesterday (50Mb/s  service) and my card is now much more happily connected, at 300Mb/s  using 802.11n. If it starts playing up I will try your suggestion 3rdalbum.

The  problem may have been partly with the previous router (only 802.11g  capability) which connected better using WPA2 encryption, but then the  Macs and Win computers had more issues so had to revert to standard WPA.

praseodym - I am not sure what deactivating the hardware encryption of the driver actually does? can you give more details?

Wireless  is much better now but still not quite as good as in win7. Maybe I will  see less of windows now I can get online properly in ubuntu tho!
Thanks,
Peter

---

### Post by praseodym on 2011-12-01
The driver is able to encrypt the connection **additionally** to the router encryption via the device. This can be buggy. Software encryption from the router (WPA2-AES) is **not** affected by this.

---

