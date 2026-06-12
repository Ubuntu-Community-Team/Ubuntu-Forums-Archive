---
title: "bcm4318 woes"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by Lunar_Lamp on 2006-06-24
I have an acer aspire 5024 laptop, with a bcm4318 wirless card.  I tried getting it to work under linux by pretty much every way I could see on the forums, and no doubt screwed something up badly, because it didn't work, and it's now not even recognised in windows.

Can anyone point me in the right direction.

---

### Post by LazyBoy on 2006-06-24
Are there references to "bcm43xx" in the log?  I was seeing this:

> Jun 24 09:08:55 spaceghost kernel: [17181002.644000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
Jun 24 09:11:00 spaceghost firmware_helper[6360]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:03:00.0' with driver 'bcm43xx'

This means that the OS found a driver, but it doesn't have the firmware.  You do not need ndiswrapper!!  Also, I was already running knetworkmanager, which said it saw my card but I couldn't connect to my network.

I did the extraction [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8")  (***just*** section 1.2.2.1) and it came right up!  knetworkmanager was trying every two minutes and generating those log messages.  Next time around, it worked.

LB

---

### Post by Lunar_Lamp on 2006-06-24
The output from iwconfig eth1 is:

```
eth1      IEEE 802.11b/g  ESSID:"No24"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:A9CB-09FE-C0BE-B2E4-E58C-1ECF-EE   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have tried "sudo iwconfig eth1 ap any" - but it still returns the same.  My network is set up with no security whilst I try and work this out.

---

### Post by firetux on 2006-06-24
Try the [howto]("http://http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318") on these forums for the 4318, with ndiswrapper. you will also need [acer-acpi]("http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html")

---

### Post by ssaidwho on 2006-06-30
howto link above is [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=4318)

---

