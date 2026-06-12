---
title: "iwlagn (Intel Wi-Fi 5100) wireless driver AP MAC is &quot;stuck&quot;"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by wirawan0 on 2009-02-09
I have a laptop with Intel Wi-Fi 5100 wireless card which is working Ok with iwlagn driver (system: Ubuntu 8.10, 64-bit, Core2 duo CPUs). I had this laptop connecting to a WPA2 Enterprise network at work. And when I went home, I simply suspended the laptop and brought it up again at home. Now at home I have the lame WEP encryption. 

I am currently using the good ol' Debian-style /etc/network/interfaces file to configure my network, by the way.

Now here's the problem: when I turned on the laptop, it would try to reconnect to the work network (because that was the setting before I suspended this laptop down at work). Of course it would not find it, so I would "ifdown wlan0". All is fine, but when I tried to "ifup wlan0=wlan0-home" to bring it up with home network configuration, it would not do so. I set up the network with static IP; so "ifconfig wlan0" shows the correct configuration. But the "iwconfig wlan0" shows:

wlan0     IEEE 802.11abgn  ESSID:"merrimac#402"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:XXXXXXXXXXXXXXXXXXXXXX   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Fishy here. why would it not associate? I peeked at dmesg, here's the relevant portion:

```

[28196.128866] Registered led device: iwl-phy0:radio
[28196.130620] Registered led device: iwl-phy0:assoc
[28196.132289] Registered led device: iwl-phy0:RX
[28196.135359] Registered led device: iwl-phy0:TX
[28196.136208] wlan0: authenticate with AP 00:0b:85:53:64:2f
[28196.163737] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Here's what's wrong: that AP MAC ID is my work's MAC ID, not my home's wireless router MAC. So certainly there is something wrong in iwlagn's setting; somehow the card "refuses" to receive the new MAC ID. Or the old MAC ID would not go away. Why is this?

I encountered similar problem with my older laptop which has ipw2200 card. Somehow it would not connect to my home wireless for the same reason: the old MAC ID would not go away.

My typical workaround is to "rmmod iwlagn" and then "modprobe iwlagn". But this is a dumb solution; and it sometimes did not work. Just now, it dit NOT work. The next solution, even more rude, is to turn it off via the hardware switch (this is a Thinkpad, and it has the "old style" sliding switch to disable/enable wireless!) then on again. But again this is so dumb.

Anybody experiencing this kind of problem? Any solution?

Wirawan

---

