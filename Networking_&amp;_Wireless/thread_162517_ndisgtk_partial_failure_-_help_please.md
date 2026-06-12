---
title: "ndisgtk partial failure - help please"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by alastair lewis on 2006-04-19
I tried  installing wireless on my new laptop this week, and thought I'd give ndisgtk (from automatrix) a go. The driver install went fine (no errors) but when I tried to configure the network the lights failed to come on.
Back to the command line. (the sudo's have been omited for brevity)
```
Ndiswrapper -l
WG511.inf driver present, hardward present
```
So far so good,
```
depmod -a
modeprobe ndiswrapper
dmesg | grep ndiswrapper
```
No errors, all apparently well.
```
iwlist wlan0 scan
```
My router appears in the list, so
```
iwconfig wlan0 essid <*Myessid*> restricted-key <*Mysecretkey*>
``` (copying and pasting the ESSID and wep key from the network settings window, where they were all along) and bingo, the lights come on the card. While the network config window is open, I switched off eth0 and activated wlan0 and surfed happilly.

My problem is that despite modprobing ndiswapper before shutting down, it will not work on subsequent reboots.
Now at boottime I have to Ctrl-C past network config and look at the "Synchronizing clock to ntp.ubuntulinux.org [COLOR="Red"]fail[/COLOR]" as a glowing testimony to the wireless failure.

Once up and running```
iwconfig wlan0 essid <*Myessid*> restricted-key <*Mysecretkey*>
``` and a manual activation of wlan0 and I'm back online.

How can I make this happen automatically at boottime, just like the old lappy, when I just did it from the command line the first time?

(New machine Acer Aspire 5002, 32-bit breezy, Netgear WG511v2 card)


SOLVED: The System>>Administration>>Networking WEP key was hexadecimal, but ASCII was chosen from the drop-down list.

---

