---
title: "Problem with wireless network - Texas acx111 wireless card"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by iffy9 on 2006-02-25
I have a network set up with one ubuntu and one WinXP box.  I have tried to connect another desktop pc, with a Texas Instruments acx111 wireless card in it.  I believe everything is set up correctly, but I cannot even get it to connect to the router.

Here is the output from *iwconfig*

admin@tinysam:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"MEONCLOSE"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


TIA

Ian

---

### Post by gmalac on 2006-02-25
Hi, this chipset is not supported by Linux and difficult to make it work (I know, I have it on a Trendnet wireless card).
Anyway, here is a link to a superb how-to [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)
Best wishes
Guy

---

### Post by iffy9 on 2006-02-25
I tried using the instructions at the link you provided, and also at the acx project website.  Both of them have parts which do not 'quite' work right.  There is no instructions as to what to do, if certain commands do not work as expected.  

Looks like I may have to buy another card then.  What is the latest recommended one for ubuntu?

TIA

Ian

---

### Post by iffy9 on 2006-02-25
While I was writing the last post, I was waiting for the ubuntu box to reboot. When it came up, I tried to open Firefox and woo hoo!!!   There was Google.  I can see the other pcs on the network.  Not sure what did it, but it seems to have worked!!  Thanks

---

