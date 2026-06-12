---
title: "Can't connect to wireless network."
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Ncshipman on 2010-03-31
Hi everyone,

This is baffling me but I am easily baffled/baffeld?  I carefully followed these instructions to install a a working driver [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568).  It all went fine, my wireless light came on and it detected my wireless network.

I know my WPA2 code (I can connect on the same computer in windows 7) and my keyring code.  but I still can't connect it whirs away for quite a while before giving up and saying not connected.

Any ideas?

I have a Dell Inspiron 1520 and the router is Thomson Bebox.

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

************
lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by chili555 on 2010-03-31
Does it connect easily if you remove encryption for a few moments? Does it connect if you use WPA and, while it is trying to connect, do in a terminal?```
sudo renice +19 $(pidof wpa_supplicant)
```

---

### Post by Ncshipman on 2010-04-01
Hey thanks for reply,
Unfortunately I can't disable the WAP as I don't know the Username or Password for the Router (the default doesn't work).  And the code printed this:
923: old priority 0, new priority 19

but didn't let me connect :-(

---

### Post by Ncshipman on 2010-04-01
Ok I'm now connected.  After having typed in that code you told me to it connected on about the 4th attempt.  I had also changed mode from infrastructure to ad hoc but looking at it again after connecting its definitely on infrastructure again?  Anyway in short I think you fixed it thanks!

---

### Post by Ncshipman on 2010-04-01
Ok I still have issues.  It is only connecting once every 20 times or so?

---

### Post by chili555 on 2010-04-01
I was afraid you'd say that you ***did*** connect with that code. There is evidently a quirk in the way ndiswrapper, Broadcom Windows drivers and wpa_supplicant work. I worked with another poster here for a week until we finally worked out the solution. Here is the thread:  [http://ubuntuforums.org/showthread.php?t=1432436](http://ubuntuforums.org/showthread.php?t=1432436)

The fix starts at about post #44 and continues to about #56 - 60. Are you ready to begin?

If your card's pci.id is 14e4:4311, I believe you can get it going with the STA driver and bypass ndiswrapper. Have you tried that? Find out with:```
lspci -nn
```

---

