---
title: "Cant get wireless to work"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Sexraider on 2008-12-02
I'm using an Linsys box v.2.8 2.4 Ghz wireless B box. I'm following the guide Ubuntu gives and i need a program called nidskwrapper, i looked all over for this program i even did i search in ubuntu files and ubuntu did not find this and so i downloaded ndisk-0.6-0ubuntu3_all.deb. dont know if it was the right thing i needed but it was worth a shot. and i got this error when i tried to install the ndisk-0.6-0ubuntu3_all.deb "Error: Dependency is not satisfiable: ndiswrapper-utils-1.9. hope this helps me to get this ndis thing and me to get wireless intnernet.

---

### Post by spcwingo on 2008-12-02
If you can hook it up to the internet via cat5 open synaptic and install ndisgtk.  If the computer is not able to connect via a hard line check out my previous post on installing ndisgtk without internet connection.

[http://ubuntuforums.org/showthread.php?t=991714](http://ubuntuforums.org/showthread.php?t=991714)

If you need more help just post back.

---

### Post by Sexraider on 2008-12-02
I put all 3 files for 8.10 on ubuntu and ran all 3. all installed.

what's next? =/

---

### Post by spcwingo on 2008-12-02
Open system>administration>install windows wireless drivers.  Choose add new driver and point to your windows driver .inf file.  If all goes well your wireless should be working.  If for some reason it doesn't post back and I'll see what else we can do to get it going.

---

### Post by Sexraider on 2008-12-02
I got the INF, installed all that jazz. It said netUSB - Hardware present - yes.

But then another popped up called auto run or something similar and I hit remove driver because it said driver invalid i believe.

Although, now, I cannot get ubuntu to put up the linksys network again.

Do i set that up through VPN?

---

### Post by spcwingo on 2008-12-02
Something ain't jiving like it should.  Try running lspci from a terminal (Applications>Accessories>Terminal) if it's an internal card or lsusb if it's a USB card and post results.

---

### Post by Sexraider on 2008-12-02
Here ya go

```
Bus 002 Device 003: ID 1915:2233 Linksys WUSB11 V2.8 802.11b adapter
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 hub
Bus 002 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
Bus 001 Device 002: ID 045e:00b0 Microsoft Corp Digital Media Pro Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by spcwingo on 2008-12-02
That card has the at76 chipset which the driver is closed source.  I have a USB card with the same chipset that I have been trying to get going for a while now to no avail.  Hopefully someone else will chime in on how to get this thing going (ndiswrapper won't do it)...I did some searching and found this how-to that I have not tried either.  Might as well give it a shot.

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)

---

### Post by spcwingo on 2008-12-02
I tried the above listed how-to and it's a no go for my card.  Maybe you'll have better luck with yours.  I honestly don't know what else to try.  Hopefully someone more knowledgeable will chime in soon.

---

### Post by S-Fraz on 2008-12-03
I used the ndiswrapper deb files from pool/n/ of the ubuntu install cd.
See if this fixes your problem:
[http://ubuntuforums.org/showpost.php?p=6285670&postcount=3](http://ubuntuforums.org/showpost.php?p=6285670&postcount=3)

The code that adds blacklist; Do not execute it more than once, because it writes to a file in append mode. Theirs no need to double write!

---

