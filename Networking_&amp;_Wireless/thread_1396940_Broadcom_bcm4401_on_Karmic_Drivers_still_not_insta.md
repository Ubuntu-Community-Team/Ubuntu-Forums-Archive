---
title: "Broadcom bcm4401 on Karmic: Drivers still not installing"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by JoJerome on 2010-02-02
For one, I must be the only person on earth with a bcm4401, because every search turns up only bcm43xx cards/drivers. Grrrrr....

Tried downloading drivers from broadcom. Get to step 2 in their ReadMe instructions and start getting errors. I filled out a trouble ticket and so far all they've sent me is instructions for Windows, not Linux. Grrrrrr.....

Tried instructions in 
[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4401](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4401)
Got to the wget bit in Step 2, wouldn't work. Grrrrr......

Did Step 7 troubleshooting/reinstall ndiswrapper in
[http://ubuntuforums.org/showthread.php?t=885847&highlight=b44+install](http://ubuntuforums.org/showthread.php?t=885847&highlight=b44+install)
Next step is to "Reinstall Windows Drivers into ndiswrapper." No idea how to do that and not finding the instructions. Grrrrrr.......

Tried ndiswrapper again from scratch using
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#No%20Luck%20Yet?%20Compile%20ndiswrapper%20from%20Source](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#No%20Luck%20Yet?%20Compile%20ndiswrapper%20from%20Source)
Since bcm44xx doesn't exist in the instructions, I followed directions for bcm43xx as they seem as close as anything. I get as far as Step 3: 
```
 ~$ sudo ndiswrapper -i bcmw15.inf
No such file or directory at /usr/sbin/ndiswrapper line 219

```

Help?

---

### Post by chili555 on 2010-02-02
Doesn't this work with the built-in module *b44*? Let's modprobe it and see what happens:```
sudo modprobe b44
ifconfig
```Do you now have an interface, eth0, perhaps? If not, please post:```
dmesg | grep b44
```Thanks.

---

### Post by chili555 on 2010-02-02
[http://74.125.47.132/linux?q=cache:x4eAdoFseHMJ:www.fsf.org/resources/hw/net/wired-ethernet+bcm4401&cd=7&hl=en&ct=clnk&gl=us](http://74.125.47.132/linux?q=cache:x4eAdoFseHMJ:www.fsf.org/resources/hw/net/wired-ethernet+bcm4401&cd=7&hl=en&ct=clnk&gl=us)

---

### Post by JoJerome on 2010-02-02
I was about to post something like this, really I was!

```

~$ dmesg | grep b44
[           1.746882] b44 0000:02:00.0 PCI INIT A -> GSI-17 (level low) -> IRQ 17
{           1.973037} b44.c:v2.0

```

lspci lists only this bcm4401 as Ethernet controller and bcm4311 as network controller. Based on our last conversation, is it the Network controller I'm concerned with? If so, dmesg | grep b43 gives me a whole boatload of info which I'll have to post a little later. Gotta run to a dr appointment at the moment and then find a wired connection.

---

### Post by chili555 on 2010-02-02
> is it the Network controller I'm concerned with? You tell me. Do you want to get the wired ethernet connection going or the wireless? The wired probably works fine right now, assuming you can plug it in.

The wireless needs firmware: ```
sudo apt-get install bcmwl-kernel-source
```Now reboot, and go to System, Administration, Hardware Drivers, and you should be able to select the STA driver.

---

### Post by JoJerome on 2010-02-02
```

  
~$ dmesg | grep b43
[    1.490590] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.490623] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   11.862646] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   12.880316] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   12.970126] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   13.012705] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   13.012766] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   13.012817] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.               
[   13.130176] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   13.140874] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   13.161653] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   13.161659] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   13.161662] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.               
[  478.670294] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  479.723528] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  479.723608] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdfc000)
[  479.723624] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  479.723646] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  480.085271] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  483.019624] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  483.027923] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  483.071886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  483.071892] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  483.071896] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.               
[  483.120264] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  483.127748] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  483.152496] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  483.152502] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  483.152506] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and downlad the correct firmware for this driver version. Please carefully read all instructions on this website.
[  510.460295] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  511.492775] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  511.492855] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdfc000)
[  511.492871] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  511.492893] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  511.851790] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  514.110108] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  514.121994] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  514.132349] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  514.132355] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  514.132359] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and downlad the correct firmware for this driver version. Please carefully read all instructions on this website.
[  514.181098] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  514.190420] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  514.208645] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  514.208651] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  514.208654] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and downlad the correct firmware for this driver version. Please carefully read all instructions on this website.

```

I went to the website it recommends, get to;
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
but again, it seems to assume I know far more commands than I do. I get as far as the section titled;
**Recommended**
*We recommend the following userspace applications to be installed...*
I download the three tar packages to my desktop, but no luck finding the right commands to open and install them.
Next several steps appear to tell me what to do without telling me how to do it.

Moving right along...

[http://74.125.47.132/linux?q=cache:mad:4eAdoFseHMJ:www.fsf.org/resources/hw/net/wired-ethernet+bcm4401&cd=7&hl=en&ct=clnk&gl=us](http://74.125.47.132/linux?q=cache:mad:4eAdoFseHMJ:www.fsf.org/resources/hw/net/wired-ethernet+bcm4401&cd=7&hl=en&ct=clnk&gl=us)
takes me to a Google splash page saying no such page exists.

```

~$ sudo modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a2:59:55
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea2:5955/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47616454 (47.6 MB)  TX bytes:1505519 (1.5 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

```

sudo modprobe b43 gives me the same response.

---

### Post by chili555 on 2010-02-02
```
sudo apt-get install b43-fwcutter
```You will be asked to automatically fetch and install the firmware into the right location. 

This assumes you have a wired ethernet connection. Do you?

---

### Post by JoJerome on 2010-02-12
> This assumes you have a wired ethernet connection. Do you?

I do now!

Amazing how everything comes together and works so smooth once I find the right drivers. You rock Chilli!


:KS

---

### Post by chili555 on 2010-02-13
I'm glad it's working for you! Have fun and , if you can, please come back and help another Broadcom fan some time.

---

### Post by jdonbook86 on 2010-12-02
> **chili555 said:**
> Doesn't this work with the built-in module *b44*? Let's modprobe it and see what happens:```
sudo modprobe b44
ifconfig
```Do you now have an interface, eth0, perhaps? If not, please post:```
dmesg | grep b44
```Thanks.

This does get my wired connection up and running, but I have to execute this command every time I start the machine. Why is it not automatically switching to the wired connection?

---

