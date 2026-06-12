---
title: "Wireless Trouble; Firmware Missing"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by jdavis45101 on 2012-05-01
I want to use the wireless on this laptop but the drivers for the chip are missing. Please Help!

---

### Post by chili555 on 2012-05-01
We need details: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by jdavis45101 on 2012-05-01
As in the type of WiFi card, laptop model, or what?

---

### Post by chili555 on 2012-05-01
Did you click on the link? It suggests several details we'd lie to see.

---

### Post by jdavis45101 on 2012-05-01
Sorry...

Brand: HP Compaq
Model: nx9010

I posted the results for the lspci -nn and ifconfig commands in odt attachments.

---

### Post by jdavis45101 on 2012-05-01
Sorry...

Brand: HP Compaq
Model: nx9010

I posted the results for the lspci -nn and ifconfig commands in odt attachments.

These odt files will work.

---

### Post by chili555 on 2012-05-01
> Broadcom Corporation BCM4301 802.11b Wireless LAN Controller [[COLOR="Red"]14e4:4301[/COLOR]] (rev 02)In order to know the best solution, please run and post:```
lsb_release -a
```Do you have a temporary ethernet connection available? Thanks.

---

### Post by jdavis45101 on 2012-05-01
> **chili555 said:**
> In order to know the best solution, please run and post:```
lsb_release -a
```Do you have a temporary ethernet connection available? Thanks.

I put that into the terminal and it says:
No LSB modules are available.
ID: Ubuntu
Description: Ubuntu 12.04 LTS
Release: 12.04
Codename: precise

And Yes, I have it plugged into Ethernet now

---

### Post by chili555 on 2012-05-01
Please run:```
sudo modprobe -r b43
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```Is it working now?

---

### Post by jdavis45101 on 2012-05-01
No, it still says firmware missing.

---

### Post by chili555 on 2012-05-01
Please show me:```
dmesg | grep b43
```

---

### Post by jdavis45101 on 2012-05-01
dmesg | grep b43
[    2.239309] b43-pci-bridge 0000:00:09.0: enabling device (0000 -> 0002)
[    2.239333] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
[   26.030921] b43legacy-phy0: Broadcom 4301 WLAN found (core revision 2)
[   26.052289] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   26.052314] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   26.077837] b43legacy-phy0 debug: Radio initialized
[  514.600298] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.
[  514.600311] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

---

### Post by chili555 on 2012-05-01
Ahhh! b43*legacy*. Sorry about that. Please do:```
sudo apt-get install firmware-b43legacy-installer b43-fwcutter
sudo modprobe -r b43
sudo modprobe b43
```

---

### Post by jdavis45101 on 2012-05-01
That got the "missing firmware" message to go away but now it keeps asking for network authentication. I am 100% sure I have the correct password for my network, but it won't stay logged into the network.

---

### Post by chili555 on 2012-05-01
Is your router set up for B, G and N speeds? Is it set for mixed mode WPA and WPA2? Many drivers have much better luck with WPA2 only and B and G speeds. I'm not very experienced with b43lgacy; it's fairly rare.

---

### Post by jdavis45101 on 2012-05-01
I have a Netgear N150 and it is set to use WPA2-PSK [AES]. I just changed the speed to 54Mbps or "Legacy Mode."

---

### Post by jdavis45101 on 2012-05-01
That didn't work either. Could it be that the option in Ubuntu is WPA & WPA2?

---

### Post by chili555 on 2012-05-01
> Could it be that the option in Ubuntu is WPA & WPA2?That's what the fill-in box shows. That's where you enter either. Let's have a look at:```
sudo nm-tool
```I wonder if 'legacy' means that the card and driver combination do WPA but not WPA2.

---

### Post by jdavis45101 on 2012-05-01
NetworkManager Tool 

State: connected (global) 

- Device: eth2  [Auto Ethernet] ------------------------------------------------ 
  Type:              Wired 
  Driver:            natsemi 
  State:             connected 
  Default:           yes 
  HW Address:        ************

  Capabilities: 
    Carrier Detect:  yes 
    Speed:           100 Mb/s 

  Wired Properties 
    Carrier:         on 

  IPv4 Settings: 
    Address:         192.168.1.6 
    Prefix:          ************
    Gateway:         192.168.1.1 

    DNS:             192.168.1.1 


- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            b43legacy 
  State:             unavailable 
  Default:           no 
  HW Address:        ****************

  Capabilities: 

  [B][SIZE="4"][SIZE="2"]Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes [/SIZE][/SIZE][/B]

  Wireless Access Points

---

### Post by chili555 on 2012-05-02
Excellent!

It it showing as 'unavailable' because Network Manager has it on hold because the ethernet is connected or because the hardware switch is off?```
rfkill list all
```

---

### Post by jdavis45101 on 2012-05-02
rfkill list all
0: phy0: Wireless LAN
       Soft blocked: no
       Hard blocked: no

Hope this helps!

---

### Post by chili555 on 2012-05-02
Please detach the ethernet cable and then reboot so we have a clean slate. Try to connect with wireless. Now we're going to see what Network Manager is doing all this time. We're going to pipe the terminal output into a text document so you can reconnect the ethernet and not have the output corrupted with ethernet rather than wireless.```
sudo cat /var/log/syslog | grep -e ethernet -e b43 | tail -n20 > jdavis.txt
```Now hook up the ethernet and go into your user directory and find the file jdavis.txt and copy and paste the entire thing here. Thanks.

---

### Post by jdavis45101 on 2012-05-02
May  2 21:27:13 jared-ubuntu-lptop kernel: [   37.229739] b43legacy-phy0 debug: Radio initialized
May  2 21:27:14 jared-ubuntu-lptop NetworkManager[666]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43legacy' ifindex: 3)
May  2 21:36:29 jared-ubuntu-lptop kernel: [    4.454953] b43-pci-bridge 0000:00:09.0: enabling device (0000 -> 0002)
May  2 21:36:29 jared-ubuntu-lptop kernel: [    4.455007] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNK3] -> GSI 10 (level, low) -> IRQ 10
May  2 21:36:35 jared-ubuntu-lptop kernel: [   35.715635] b43legacy-phy0: Broadcom 4301 WLAN found (core revision 2)
May  2 21:36:35 jared-ubuntu-lptop kernel: [   35.786106] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
May  2 21:36:35 jared-ubuntu-lptop kernel: [   35.786146] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
May  2 21:36:35 jared-ubuntu-lptop kernel: [   35.824425] b43legacy-phy0 debug: Radio initialized
May  2 21:36:37 jared-ubuntu-lptop NetworkManager[653]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43legacy' ifindex: 3)
May  2 21:42:06 jared-ubuntu-lptop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/8c536c507edb43cb8bd0a27c3844afde
May  2 21:42:06 jared-ubuntu-lptop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/8c536c507edb43cb8bd0a27c3844afde
May  2 21:42:32 jared-ubuntu-lptop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/8c536c507edb43cb8bd0a27c3844afde
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.656434] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.792650] b43legacy-phy0 debug: Chip initialized
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.793769] b43legacy-phy0 debug: 30-bit DMA initialized
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.800746] Registered led device: b43legacy-phy0::tx
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.801045] Registered led device: b43legacy-phy0::rx
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.801302] Registered led device: b43legacy-phy0::radio
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.801488] b43legacy-phy0 debug: Wireless interface started
May  2 21:42:42 jared-ubuntu-lptop kernel: [  402.816808] b43legacy-phy0 debug: Adding Interface type 2

---

### Post by chili555 on 2012-05-04
Looks remarkably perfect. That's my favorite kind of problem. It looks perfect except it doesn't work! I wonder what network Manager is doing all this time. Please detach the ethernet cable, try to connect with wireless and run:```
sudo cat /var/log/syslog | grep -i network | tail -n20
```Please post the result here.

---

### Post by zakuan96x on 2012-07-26
i also have same problem

---

### Post by zakuan96x on 2012-07-26
my Ubuntu 12.04 is firmware missing ...

what should i do :( :KS

---

### Post by zakuan96x on 2012-07-26
[CENTER]why the discussion end here ..... 
should we continue fix these problem seriously ^_^[/CENTER]

---

### Post by chili555 on 2012-07-26
Please open a terminal and run and post:```
lspci -nn | grep 0280
lsb_release -d
```Thanks.

---

### Post by MBlapTOP on 2012-08-08
I followed this path to get wireless working.
 
Ubuntu software centre-firmware b43 installer(might be in "system" sub menu)- install-restart-make sure "wireless" switch is on. (My older HP has a separate switch to turn on wireless) Upon rebooting Ubunto notified me that a wireless network was available . Go to system settings and open network.  choose the wireless network you want to connect to.

---

### Post by mummak on 2012-10-12
Hi all.

I got it working by doing the steps below at the end.

Before you follow my steps, I strongly advise you to... be sure of what you are doing, and check posts which might criticize mine.

I am a beginner in the ubuntu stuff..and what my one year ubuntu experience has taught me is:

BE CAREFUL WHEN TYPING SUDO COMMANDS POSTED AROUND! sh*t can happens if you dont really know what you re doing.

By typing the lines below I had a very slight idea of what I wasdoing...but it worked b4 so I decided to try once again.

I have a hp pavillion with a broadcom 802.1 (I guess thats the name of the thing) network adapter. When I first installed ubuntu 11.04 these were the following commands:

sudo apt-get purge bcml-kernel-source > ( apparently ubuntu installed smth in kernel that prevented the wireless from working and it had to be removed. This was not necessary in 12.04)
sudo apt-get install firmware-b43-installer
sudo apt-get install b43-fwcutter (this was not necessary either at 12.04)

then restart networking services:

sudo /etc/init.d/networking restart

emphasizing chili555's advice:
other usefull wireless commands
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

that did it. hope it helps and once again: BE CAREFUL

---

### Post by Skatespeare on 2012-12-24
> **chili555 said:**
> Please run:```
sudo modprobe -r b43
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```Is it working now?

Your're a hero! I would have never come up with that myself! Thanks a lot :)

---

