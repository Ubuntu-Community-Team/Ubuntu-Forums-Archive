---
title: "wireless card got uninstalled"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by jepperstone on 2009-02-26
I have a Dell XPS M1530 and I was following these directions to be able to use 4gb ram: [http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)

It worked just fine, however my wireless card was uninstalled. ndiswrapper -l doesn't return anything. Here's the output of lspci -vv -nn|less -i:

> 0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
        Subsystem: Dell Device [1028:000a]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 7
        Region 0: Memory at f1efc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel modules: ssb

~
~
~
~
~
~
~
~
~

unem -m returns i686. I think this has something to do with it but I can't connect the information I have. Can anyone help me to install the best wireless driver?

---

### Post by Crafty Kisses on 2009-02-26
You probably need to load the ndiswrapper module, what are the results for this command?
```
lsmod | grep ndis
```

---

### Post by jepperstone on 2009-02-26
lsmod | grep ndis returned:

> ndiswrapper           196124  0 
usbcore               149872  7 ndiswrapper,usbhid,btusb,uvcvideo,ehci_hcd,uhci_hcd


---

### Post by Crafty Kisses on 2009-02-26
I mean the next logical question would probably be have you tried installing the driver again via ndiswrapper?

---

### Post by jepperstone on 2009-02-26
What is the easiest way for this to be done?

---

### Post by Crafty Kisses on 2009-02-26
There's a couple of directions I can point you in here. I'll give you the most basic one though since it sounds like you want simplicity. You can install a package called "ndisgtk" which is a graphical front end for ndiswrapper, which you can install by running the following:
```
sudo apt-get install ndisgtk
```
So once you have that installed, you need to grab your driver, I'm not sure if you have the driver already, but you need to Google your wireless card and fetch the XP drivers, and then once you have done that extract the drivers to your desktop or wherever you want. Find the .inf file that's located in the extracted folder, it should be in there somewhere. Now what you can do is open up ndisgtk by running the following command:
```
sudo ndisgtk
```
Once it's open, browse for the .inf file, and click "Install new driver" once you have done that you should see the screen say "Hardware present" then you should probably reboot by running the following command in the Terminal:
```
sudo shutdown -r now
```
Alternatively you can just reboot from the GUI, but it's really your choice, once your back into Ubuntu your wireless card should be working fairly well, if not perfect. If you have any problems with this post back and I or someone else can assist you further on your problem.

---

### Post by jepperstone on 2009-02-26
I did some research and couldn't find a driver. My wireless card is Broadcom 4328.

---

### Post by Crafty Kisses on 2009-02-26
Check out this [thread.]("http://ubuntuforums.org/showthread.php?t=336654&page=2") Then look for the reply by "kayvortex" that reply seemed to be pretty useful for a bunch of people, I'd suggest you follow his guide and see if that doesn't give you any success.

---

### Post by Ayuthia on 2009-02-27
Can you also check:
```
lsmod|grep -e b43 -e wl -e ssb
```

They are other wireless modules that work with Broadcom cards.  The b43 module does not work for your card, but we should verify that it is not there.  

Another thing to check is dmesg:
```
dmesg|grep ndis
```It might have some helpful information.

---

### Post by jepperstone on 2009-02-27
thank you for your wisdom!

---

