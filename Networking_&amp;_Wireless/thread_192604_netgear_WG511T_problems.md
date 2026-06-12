---
title: "netgear WG511T problems"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by NaOH on 2006-06-08
I'm curious if anyone has encountered problems with the WG511T on Dapper. It seems the general consensus is that this cardbus wireless adapter is good to go out of box. I've tried connecting on Breezy and Dapper but with no success. The card is seen under network as ath0, the network monitor show it is at least detecting my wireless network, but beyond that no internet (through browser or synaptic or update manager, nil). I have tried both DHCP and manually entering my network info, still nothing. I should also note under Network Tools the card is shown as "unkown device," and the LED's flash a simple unchanging pattern, although i doubt that is very pertinent. Any thoughts? Is this a job for ndiswrapper?

---

### Post by tombs on 2006-07-21
No man, I have the same pcmcia, and was working on Breezy, and now is working on Dapper.
Very easy:
[http://www.ubuntuforums.org/showthread.php?t=38972]("http://www.ubuntuforums.org/showthread.php?t=38972")
Try it, and say something...

---

### Post by Thasaidon on 2006-07-27
I have the same card and when Dapper starts up, the pcmcia card starts with  both lights blinking one at a time (meaning the card is active, but is not connected).

I seem to have the good drivers for this card
```
thasaidon@MOBILE:~$ dmesg |grep ath_hal
[17179597.884000] ath_hal: module license 'Proprietary' taints kernel.
[17179597.884000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
```
an **ifconfig** and **iwconfig** shows the card as present.
```
thasaidon@MOBILE:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:5D:32:F3
          inet addr:172.16.0.111  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe5d:32f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:196 dropped:0 overruns:0 frame:196
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:dcba0000-dcbb0000

thasaidon@MOBILE:~$ iwconfig ath0
ath0      IEEE 802.11  ESSID:"N3TwAr"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thasaidon@MOBILE:~$
```

Also, an **iwlist scan** does show my AP.
```
thasaidon@MOBILE:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:AB:D3:A4
                    ESSID:"N3TwAr"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

thasaidon@MOBILE:~$
```

I am using WPA instead of WEP, so I installed **networkmanager applet 0.6.2** because I thought this would allow me to enable (setup) WPA,
this applet however tells me there is no network device found...

So why can't I get this card working with WPA in Dapper?
I also searched this forum and found several things about getting WPA to work, but none om them seem to get me to where I want to be...

any help would e appreciated.

---

