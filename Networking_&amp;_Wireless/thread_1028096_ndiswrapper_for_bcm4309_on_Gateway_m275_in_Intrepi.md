---
title: "ndiswrapper for bcm4309 on Gateway m275 in Intrepid"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by summersab on 2009-01-02
At the risk of being annoying, I'm trying to get my wireless card working in Intrepid by using ndiswrapper. I was using the fwcutter driver, but it is slow as hell, and I'm sick of not having native speeds. I don't care if these drivers aren't open source - they're at least free.

Basically, I have tried darned near every guide and wiki on the web and had to reinstall a few times as a result. Ndisgtk shows that everything is good, and $ndiswrapper -l shows the following:

bcmwl5 : driver installed
	device (14E4:4324) present (alternate driver: ssb)

My $lspci -l shows that I have the following device:

02:04.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)

Not very many people have the 09 version of the card - most are 03, 06, 11, or 18's. Mine seems to be the odd one out, and I don't know if that is specific.

I want to be able to connect to a standard D-link router with WPA2. That's all. I'm an intermediate Linux user and a computer science major, so I can handle myself, but I wouldn't mind having this spelled out for me since at this point I've read enough How-To's that don't work.

Thanks!

---

### Post by Kobalt on 2009-01-02
Did you completely unloaded and blacklisted the drivers you used before (both *bcm43xx* and *b43*) installing and setting up ndiswrapper ?

---

### Post by summersab on 2009-01-02
Sure did. I never even installed the drivers, but they are blacklisted anyway.

Perhaps the readout from my iwconfig would be of use:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have NO idea what pan0 is. No, ifconfig does not list a wlan0, but it does list wlan1 again (seems to be standard). Despite the fact that it registers, the network config applet in Gnome doesn't register that the card is there and finds no networks. Thus, it appears that everything is in place - one little thing must be blocking it. I tried the ssb trick, but to no avail (unless that has to be done pre-X; I reloaded the modules from within a working X).

Ideas? This is annoying.

---

### Post by Kobalt on 2009-01-02
The ssb trick ? I think this must be done when you compile ndiswrapper from source : is that how you installed ndiswrapper? With my BCM94311 I also had to compile ndiswraper in order to get the card working, I did it this way : ```
echo -e 'install ndiswrapper modprobe -r ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb\n' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

### Post by ieee488 on 2009-01-02
same chipset, different laptop
[http://ubuntuforums.org/showthread.php?t=405552](http://ubuntuforums.org/showthread.php?t=405552)

---

### Post by summersab on 2009-01-02
IEEE, they are using the native driver. It sucks. I don't want to do that.

Kobalt, is that one line of code? I'm having trouble decyphering what it is trying to do . . .

If you need more detail, I'm more than willing.

---

### Post by Ayuthia on 2009-01-02
> **summersab said:**
> IEEE, they are using the native driver. It sucks. I don't want to do that.

Kobalt, is that one line of code? I'm having trouble decyphering what it is trying to do . . .

If you need more detail, I'm more than willing.

It is one line of code and all it is doing is removing the ndiswrapper and ssb modules, loading the ndiswrapper module back, and then finally loading the ssb module.  This command will get called every time the ndiswrapper module is loaded.  You can also do the following commands (it will be just only for this session:
```
sudo modprobe -r ndiswrapper ssb
sudo modprobe ndiswrapper
sudo modprobe ssb
```If this set of commands work, then you can add the one line command in the Terminal.

Have you checked to see if ndiswrapper is loaded or if there are any error messages for ndiswrapper:
```
lsmod|grep ndiswrapper
dmesg | grep ndiswrapper
```

---

### Post by ieee488 on 2009-01-02
> **summersab said:**
> IEEE, they are using the native driver. It sucks. 
In what way does it "suck"?

I am using it on my Dell laptop. Granted I don't use wireless that much on it and only on an open network. Works fine enough for me.

---

### Post by summersab on 2009-01-02
IEEE, it "sucks" because it is slow, limited, and doesn't work at full speed and full potential. I use wireless too much for fwcutter to be useful.

Ayuthia, I ran those commands (and have before) to no avail. iwconfig doesn't change and the Network Manager doesn't detect anything. Here is the readout from my lsmod and dmesg:

```
arthur@arthur-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           196380  0 
usbcore               148848  6 wacom,ohci_hcd,ndiswrapper,uhci_hcd,ehci_hcd

arthur@arthur-laptop:~$ dmesg | grep ndiswrapper
[   17.074772] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.457244] usbcore: registered new interface driver ndiswrapper
[  663.241603] usbcore: deregistering interface driver ndiswrapper
[  663.363563] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  663.479513] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[  663.481752] ndiswrapper 0000:02:04.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[  663.486685] ndiswrapper: using IRQ 10
[  663.888837] usbcore: registered new interface driver ndiswrapper
[  664.197332] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
```

Any ideas? Need more info? Everything SEEMS to be loaded just fine - it just won't do anything USEFUL.

---

