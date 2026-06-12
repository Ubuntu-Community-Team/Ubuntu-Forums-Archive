---
title: "Edimax EW-7128G problem"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by peterx14 on 2009-12-30
Hi all,

I've just installed a new Edimax EW-7128G PCI card and have run a fresh install of Ubuntu 9.10 -- everything works perfectly except that after 1 minute of no network activity, the "link" LED switches off and there after, any *inbound* traffic suffers heavy packet loss.

The odd thing is, on the machine with the EW-7128G card, everything is fine. I can run a web browser, ping other machines, SSH where-ever, and it all works perfectly. The "link" and the "Tx/Rx" lights never come back on once they've switched off, but that does not affect the machine itself.

It is only that pinging this card from another computer results in packet loss, and SSHing into this machine is pretty unusable... it takes longer than it should to connect (this is all on a [W]LAN) and whilst sometimes keystrokes echo immediately, other times they take a good few seconds before they appear!

So... I don't think the card is defective. It looks to me like maybe it's going into power save mode? Although I could be barking up the wrong tree.

The EW-7128G is connecting to a Netgear DG834G router and the other computer that I'm pinging/sshing from, is wired directly to that. The EW-7128G is currently about half a metre away from the router and is unsurprisingly reporting a 100% signal!

iwconfig says:
```
$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"PETER"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:09:5B:CB:2F:38   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

NOTE: Power Management is "on".

I don't know what's causing this problem, and I'm struggling to understand why it doesn't seem to affect any traffic originating from the machine in question!

Any ideas welcome... but right now I guess the question is how can I disable the Power Management option.

TIA

---

### Post by peterx14 on 2009-12-30
Bad form me replying to my own post.... but anyway! I discovered [this thread](http://ubuntuforums.org/showthread.php?t=1324863) which also features a problem that occurs after 1 minute, and indirectly I found the command to disable power management:
```
$ sudo iwconfig wlan0 power off
```

This _appears_ thus far to have solved the problem!

So my next problem is -- is there a startup script I can modify to make this happen automatically?

---

### Post by peterx14 on 2010-01-29
Bumpity bump!

---

### Post by peterx14 on 2010-02-04
Got it all working!! All the [details are in this thread.](http://www.linuxquestions.org/questions/linux-wireless-networking-41/where-should-i-add-iwconfig-options-to-make-them-permanent-786904/)

---

