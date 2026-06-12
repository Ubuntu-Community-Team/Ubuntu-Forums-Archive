---
title: "Atheros AR5001 Issue"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by sandy4linux on 2009-12-11
hi,
 My laptop is on Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
I am able to use my wireless internet with out any problem. But I dont find my atheros network adapter anywhere.
So am I using a linux default wireless.
Can anyone help me to activate my ath5k? 
 # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"KLA  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:0A:BC:E8:55   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:4D9C-2A3D-3B
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  Noise level=-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

please help me to turn on my atheros network drive

Thanks

---

### Post by chili555 on 2009-12-11
I do not understand this:> I using a linux default wireless.Is this not your wireless interface all ready to go?> wlan0 IEEE 802.11bg ESSID:"KLA
Mode:Managed Frequency:2.437 GHz Access Point: 00:30:0A:BC:E8:55
Bit Rate=48 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Encryption key:4D9C-2A3D-3B
--- snip ---Please clarify.

---

### Post by sandy4linux on 2009-12-13
Yes thats right I am using my wireless , but I am suppose to see ath0  in the iwconfig.isn't it? When I first installed ubuntu 8.10, my wireless wasnt working and done ndswrapper to detect my atheros. since i have upgraded it, i dt see ath0. do u think its working fine.?

---

### Post by chili555 on 2009-12-13
Usually, *wlan0* is the interface that is created by ndiswrapper and *ath0* is created by the native, built-in driver. You said you installed ndiswrapper to get it going and it appears to be fine. Can you surf the web, email, instant message and bittorrent? If so, it's just fine.

As they say here in the woods, if it ain't broke. don't fix it.

---

### Post by doublefun on 2009-12-28
how about change the "managed mode" to "monitoring mode"??
i also have AR5001 on karmic

---

### Post by chili555 on 2009-12-28
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Please post back if this doesn't do it.

---

### Post by adam814 on 2009-12-28
I've never seen a Windows driver that would work in monitor mode.  So I doubt that will work if you're using ndiswrapper.  For help on getting it working natively see [http://madwifi-project.org/](http://madwifi-project.org/).  The madwifi drivers use their own utilities to create virtual interfaces in monitor modes.  You might also need the madwifi-tools package, it's been too long since I had my laptop with the Atheros card to remember.

I never got decent stability out of any of the combinations of ndiswrapper/windows drivers even for normal web browsing.  Then again I had an AR5008 that only worked with a random branch of madwifi-ng with a patched ath-hal that didn't get merged to trunk.

---

