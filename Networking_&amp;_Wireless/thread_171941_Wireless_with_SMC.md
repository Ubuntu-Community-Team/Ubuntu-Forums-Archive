---
title: "Wireless with SMC"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by akaSlack on 2006-05-07
Hey I cant get my wireless to be activeted! Can anyone help me?

Iwconfig says : 
akaslack@akaslack:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

When I use NetworkManager it does not have any signal, and when I actived it in network options ubuntu just think for awile and nothing happens... Its like ubuntu knows the card is there but do not active it!:-x

---

### Post by Durito on 2006-05-07
I just got an SMC2635W card running under 5.1. If, like my SMC card, yours has a Radio On/Off function, your radio could be off. I don't know how to fix this, but see the WirelessTroubleShooting guide at wiki.ubuntu.com, for a couple of suggestions. If you've also got it running on a Windows system, you could just use the firmware that came with the card to turn it on.

---

