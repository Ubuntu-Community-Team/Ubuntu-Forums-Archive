---
title: "once working wireless, now iwconfig doesn't work"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by chrsjav on 2006-03-05
Hi all,

I'm so happy with ubuntu as a whole, so first off let me thank you guys for helping me use my favourite OS.

When I first installed ubuntu, I used ndiswrapper and got my broadcom up and running.  I could connect to any network, encrypted or not.  Then one day I had trouble connecting to my school's encrypted network, but I thought maybe I didn't give it much time / thought, because I could still connect to a friend's unencrypted network.

So, now I cannot connect to my school's network at all.  At some points I get dhcpclient to work, everything seems normal, but then when I launch firefox to "register" using a web-based form, firefox never receives the redirect header, so no pages are found.  My sequence of code is something like:

```
sudo modprobe ndiswrapper
sudo modprobe wlan0 #why not?
#me pushes the wireless button on my laptop, it lights up (even tho I never had to push it before -- it always lit up magically after a command iirc
sudo iwconfig wlan0 essid {blah} #tried with and without quotes
sudo iwconfig wlan0 mode Managed
```

However, when i run 'iwconfig', i don't see any of my changes made.  The essid is NOT changed by my command; it still says "off, any"

```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-80 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:39  Invalid misc:40026   Missed beacon:0
```

The command line fails? Yes. So... the only possibility I'm thinking is that the encryption key is off.  I can't turn it on b/c I don't know the key; but it may be stuck using some old key that I told it to use when I was using another network.  

Does anyone know how to edit the keys, or to roam w/out specifying keys?

Thanks, C

---

### Post by chrsjav on 2006-03-19
Issue should be resolved in Dapper with its built-in broadcom support.  Thank you developers!

---

