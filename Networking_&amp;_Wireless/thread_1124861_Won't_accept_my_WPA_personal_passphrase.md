---
title: "Won't accept my WPA personal passphrase"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by konf300 on 2009-04-13
A big hello from a recent convert to all fellow linuxers.

It's been 2 days since I've abandoned the ranks of windoes now and I had managed so far without resorting to your kind help, but now I think I've given up and here I am. Also please bear with me as I'm not yet totally familiar with the linux jargon but I'm doing my best here.

Long story short, here's my issue. I have rtfm to install ndiswrapper and my wireless adapter driver is working just fine - at least I'm seeing "enable wireless" option when I right-click the network manager and I can see a list of available routers when I left click on the tray icon.

I even managed to connect to my router the first time I had toyed around with network manager and had internet connection for about 5 minutes (cue victory cry here). But then I lost connection and I've been in the dark ever since.

Now when I try to connect, I get a small popup window asking for WPA(personal) key. I type my passphrase (I'm sure it is correct), the two dots on the systray get moving but it won't connect and about 1 minute later, I get the same popup window asking for WPA but this time when I click show my passphrase, I'll get what looks like an encrypted string. I have tried manually replacing it with my regular passphrase to no avail.

My wireless modem/router is a USR9110. My wireless adapter is AirTies WUS-300 (usb stick). Ubuntu version 8.10.

Here is some info I've gathered after trying what seemed like an endless list of terminal commands:

```
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:3c:bd:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tusb1150 driverversion=1.53
+Airties,06/01/2005,7.2.2.42 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:3c:5b:af:b2:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```


Also here's something from 192.168.2.1's Wireless Security settings:
```
Cypher suite: TKIP
Authentication: Pre-shared Key
Pre-shared key type: Passphrase	
Group Key Re-keying: disabled

```


inb4 rtfm - it's the only thing I've been doing forever. I'm almost convinced that Linux is not for everyone, so maybe you guys should change your motto to "... for *ultrasmart* Human beings".

---

### Post by SOSv2 on 2009-09-25
Hi,

did you get a solution for this? I havve the exact same problem and starting to get "disgusted" with Linux on this point as I already spoiled several hours trying to search for a solution.

Thanks,

SOSv2

---

### Post by billconan on 2009-10-14
i have the same problem, but haven't found any solution.

---

### Post by _sluimers_ on 2009-11-02
Same here, grrrrr.... and I ordered the USB network stick from linux emporium. I'm downloading the latest the latest driver, but doubt it'll work.

---

### Post by ArcaVex on 2009-11-02
Personally i removed Network-manager and installed WICD (using a wired connection)

I was previously using network-manager and WEP encryption to test,  and it would ask for the key, say "validating authentication",  hang for a minute, then ask for the wep key again.

Some others, including myself have also found that entering the key/passphrase using iwconfig (from terminal) has helped it connect. I currently run a script to connect to wireless along the lines of

[I]sudo iwconfig wlan0 essid networkssid
        iwconfig wlan0 key wepkey
        dhclient wlan0[/I]

---

### Post by MrDead on 2009-11-02
I am currently having the same problem that ArcaVex described and I posted on the forums ([http://ubuntuforums.org/showthread.php?t=1308780](http://ubuntuforums.org/showthread.php?t=1308780), but I didn't get any reponse. I'm gonna boot into 9.10 now and see if it works.

---

