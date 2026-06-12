---
title: "Madwifi original: can only associate if i'm very close to ap"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by Eversmann on 2006-06-28
Hi!

I'm having a very weird issue with madwifi. I can only use the madwifi compiled drivers because they are the only one that makes me enable the radio power on the laptop.

Actually it's working (i'm writing right now from it) but i can only associate if i'm very very close to the AP.

I've tried 3 different aps (3com, linksys, conceptronic) and still the same. Moving just half a metre from it lost the association. Tested the today svn shot but still the same. It's not a problem with password, wep and things like that, tested with them opened.
I'm running a Fujitsu Amilo L1310G with Ubuntu dapper 6.06 (running
 kernel 2.6.15-25-386). The restricted modules aren't installed, and
 have latests madwifi drivers 0.9.1 compiled and installed with no
 problems. I have to modprobe it with rfkill=0 switch to make the
 laptop power on the wifi radio (the button that comes with it enables
 the radio by software on windows only).
 
 I'm having a weird issue with this that it's driving me crazy: I can
 only associate with the aps if i'm very close to it. And very close to
 it i mean having the ap half a metre. If I move from it 1 metre away
 (in line of sight, no obstacles) i can't associate anymore. But i can
 always see the link quality, and i can scan it with iwlist, even the
 link quality and the signal is great. This is an example:
all
I can see the aps perfectly using iwlist, signal, link quality... even when i use iwconfig, not being associate, i can see the signal and link quality. Here's an example

When i am associated i have this:
 
 ath0      IEEE 802.11g  ESSID:"Ethereal"
           Mode:Managed  Frequency:2.447 GHz  Access Point: 00:12:A9:0A:E0:0E
           Bit Rate:5 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3
           Retry:off   RTS thr:off   Fragment thr:off
           Encryption key:(encription key removed by me)   Security
 mode:restricted
           Power Management:off
           Link Quality=61/94  Signal level=-34 dBm  Noise level=-95 dBm
           Rx invalid nwid:917  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
 Now i move 3 steps away:
 
 ath0      IEEE 802.11g  ESSID:"Ethereal"
            Mode:Managed  Frequency:2.447 GHz  Access Point: Not-associated
            Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3
            Retry:off   RTS thr:off   Fragment thr:off
            Encryption key:(encripted key erased by me)   Security
 mode:restricted
            Power Management:off
            Link Quality=61/94  Signal level=-34 dBm  Noise level=-95 dBm
            Rx invalid nwid:917  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
 I just notice the bit rate goes to 1 Mb/s, everything is ok.
 
Tried using iwconfig ath0 ap [mac], but nothing, just moving close to the ap re-associate and works again. When i'm away, typing iwconfig in a loop i can see it search between the channels with no luck.

 My dmesg is:
 
 [17179589.016000] ath_hal: module license 'Proprietary' taints kernel.
 [17179589.016000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111,
 RF5112, RF2413, RF5413)
 [17179589.060000] wlan: 0.8.4.2 (0.9.1)
 [17179589.084000] ath_rate_sample: 1.2 (0.9.1)
 [17179589.096000] ath_pci: 0.9.4.5 (0.9.1)
 [17179589.096000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 23
 (level, low) -> IRQ 217
 [17179589.680000] ath_pci: switching rfkill capability off
 [17179589.684000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
 [17179589.684000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps
 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
 [17179589.684000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
 [17179589.684000] wifi0: mac 7.8 phy 4.5 radio 5.6
 [17179589.684000] wifi0: Use hw queue 1 for WME_AC_BE traffic
 [17179589.684000] wifi0: Use hw queue 0 for WME_AC_BK traffic
 [17179589.684000] wifi0: Use hw queue 2 for WME_AC_VI traffic
 [17179589.684000] wifi0: Use hw queue 3 for WME_AC_VO traffic
 [17179589.684000] wifi0: Use hw queue 8 for CAB traffic
 [17179589.684000] wifi0: Use hw queue 9 for beacons
 [17179589.704000] wifi0: Atheros 5212: mem=0xc0200000, irq=217
 
 Do you know what can i do?
 
I've asked at  #madwifi channel on irc, at madwifi mailing list, no answers. I don't know what to do.

Thanks a lot guys for your replies.

---

### Post by queenorych on 2006-06-28
Has this worked before.  Does it work with windows?  I had a similar situation with my dell, when I put in a new rt2500.  The antenna and aux connections are backwards on the dell, so the antenna and aux connections were backwards.  Once I reran the antenna cable, plugged in the cable correctly, I was able to associate.  You network should not be 1Mb with 61 quality with you only a meter away!

---

### Post by Eversmann on 2006-06-28
Thanks for your reply ;-)

Yes, in windows, everything works perfectly with no problem at all.

I've tried different channels, different aps, madwifi 0.9.0, 0.9.1, latests svn snapshot, tweaking txpower, diversity, kernel versions (2.5.15-25 386 and 686)....

I don't know what to do really, this is really really really weird.

---

### Post by leguenm on 2007-02-02
Hi Eversmann,

Was your problem connecting further than half a meter from the AP solved now?

I encountered exactly the same problem last time I tried to use wifi with my L1310G (OK with windows, KO with linux), so if you found a workaround, please let us know!

Mael.

---

### Post by damir_1105 on 2007-06-04
I have to modprobe it with rfkill=0 switch 
.
.
.
[17179589.680000] ath_pci: switching rfkill capability off

I think that is the problem rfkill=0, Try reverse logic. :)

---

### Post by Eversmann on 2008-05-23
This is an old thread, sorry for missing it, but i'll reply here in case someone find it trying to resolve his problem:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G)

The problem was resolved and posted in another thread (that one that says l1310g atheros wifi fully working or something like that). Anyway, in the wiki page, i've posted what it's needed to do to make this laptop work on ubuntu (actually, it's just a fix for the bios and the wifi stuff, everything else is working out of the box.... yeah yeah, i know, the hibernate/sleep thingy... but that problem is spread out on most of the laptops).

---

