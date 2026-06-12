---
title: "Adhoc wireless connection setup"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by jestinjoy on 2010-08-31
I tried setting up a adhoc wifi in my debian laptop, so that my other laptop running Ubuntu could connect to it. Though the access point made on Debian laptop is visible on Ubuntu laptop, I could not establish a connection. The steps followed are give below.

```
 ifconfig wlan0 down
iwconfig  wlan0 channel 4
iwconfig  wlan0 mode ad-hoc
iwconfig  wlan0 essid 'test1'
iwconfig  wlan0 key 1234567890
ifconfig  wlan0 192.168.1.1
```

```
ifconfig wlan0 down
iwconfig  wlan0 channel 4
iwconfig  wlan0 mode ad-hoc
iwconfig  wlan0 essid 'test1'
iwconfig  wlan0 key 1234567890
ifconfig  wlan0 192.168.1.2
```

Then I used create new wireless network tab to create a connection named test1. Though it shows up on Ubuntu box, i couldnt connect to it. Please help

---

### Post by MaindotC on 2010-09-01
Please try using the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  It will help you test connectivity between the two machines.  If you have any problems, or your problem is not resolved, please let us know at what point you are having difficulty.

---

### Post by jestinjoy on 2010-09-01
I didnt find anything help full regarding adhoc network in that. What i did is given in the first post.

---

### Post by AggravatedGestalt on 2010-12-30
I guess I will refresh the thread. I am having the same problem. Can a wireless file transfer occur between two wireless cards/lap-tops in Ubuntu?  If so, there is no obvious method of doing so. I see similar questions posed in various threads, and left unanswered.

---

### Post by PatchesTheCaveman on 2010-12-30
You can create a wireless ad-hoc network with NetworkManager by clicking on your wireless icon and clicking *Create New Wireless Network...*

To share files between Linux computers, use NFS:  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

To share files between Linux and Windows computers, use Samba:  [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

If both devices have Bluetooth, it's also possible to share files using that:  [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

