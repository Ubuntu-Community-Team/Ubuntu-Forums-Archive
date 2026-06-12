---
title: "Ralink RT2070: Internet speed slow?"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by Darkened35 on 2011-08-05
I'm running 11.04. I have brought a new WiFi adapter, ralink rt2070. When I browse the internet, it takes a long time to load a webpage. When I download updates, it goes at 3,060 BYTES a second. Is there any solution? I'm using the default rt2800usb driver.

---

### Post by chili555 on 2011-08-05
> Is there any solution? I'm using the default rt2800usb driver.Yes, there is a solution. *Don't* use the default rt2800usb driver. Please open a terminal and run:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

If you find that both rt2800usb and rt2870sta are loaded and conflicting, let's blacklist rt2800usb. In a terminal:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

If those are not the loaded and conflicting driver modules, post the result and we'll dig deeper.

---

### Post by Darkened35 on 2011-08-05
I have blacklisted rt2800 and the pci one that was there. It works great now, thanks! the only thing is that is shows up as simply "usb" in connection proprieties , is this normal? thanks!

---

### Post by chili555 on 2011-08-05
If you got this:> It works great nowThen I wouldn't worry about a thing; except, would you please use thread tools at the top an Mark Solved?

---

### Post by Darkened35 on 2011-08-07
OK. It WAS working fine, but now it's slow again. It's still using the "USB" driver. When I move the pc it's still slow. Doing a grep on rt2 only returns RT2870STA driver. Any other suggestions?

---

### Post by chili555 on 2011-08-07
Let's double-check a few things. Please run and post:```
lsusb
lsmod | grep rt2
dmesg | grep rt2
```Maybe we still have a conflict.

---

### Post by Darkened35 on 2011-08-07
Sorry, had to copy it into a file, and transfer it to my netbook.

saryth@saryth-K7VT2:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
saryth@saryth-K7VT2:~$ lsmod | grep rt2
rt2500pci              18668  0 
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  2 rt2500pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
rt2870sta             410104  1 
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pci
crc_ccitt              12595  2 rt2870sta,irda
saryth@saryth-K7VT2:~$ dmesg | grep rt2
[   10.875441] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.743987] usbcore: registered new interface driver rt2870
[   13.613730] rt2500pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.745482] Registered led device: rt2500pci-phy0::radio
[   13.745518] Registered led device: rt2500pci-phy0::quality
[   26.995916] <==== rt28xx_init, Status=0
[   28.123888] <==== rt28xx_init, Status=0
[  135.585143] <==== rt28xx_init, Status=0
[  145.914814] <==== rt28xx_init, Status=0
[  146.962461] <==== rt28xx_init, Status=0
[ 1395.186376] <==== rt28xx_init, Status=0
saryth@saryth-K7VT2:~$

---

### Post by chili555 on 2011-08-07
> $ lsmod | grep rt2
[COLOR="Red"]rt2500pci[/COLOR] 18668 0
rt2x00pci 13986 1 rt2500pci
rt2x00lib 39075 2 rt2500pci,rt2x00pci
mac80211 257001 2 rt2x00pci,rt2x00lib
rt2870sta 410104 1
cfg80211 156212 2 rt2x00lib,mac80211
eeprom_93cx6 12653 1 rt2500pci
crc_ccitt 12595 2 rt2870sta,irdaIt looks like you have a PCI wireless device. I assume it doesn't work well and so you got the USB device. I also strongly suspect that some modules which depend on rt2500pci are conflicting with the USB wireless driver rt2870sta. Let's get the PCI modules out of the way. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```There is already a line blacklisting rt2800usb. Add more lines below it:```
blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by Darkened35 on 2011-08-07
The thing is, when I disable the PCI, the libs no longer show up in lsmod | grep rt2. I'll try this though.

---

### Post by Darkened35 on 2011-08-07
Nope, still browsing at around 4.6 KB/s. Sorry for this :(

---

### Post by Darkened35 on 2011-08-07
But what's strange is that I don't have a PCI device.

---

### Post by chili555 on 2011-08-07
Let me see:```
lsmod | grep rt2
iwconfig
dmesg | grep rt2
modinfo rt2870sta | grep filename
```> The thing is, when I disable the PCI, the libs no longer show up in lsmod | grep rt2.As you can see, rt2870sta doesn't depend on the libs:```
$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93C0C58E1A016FE5BD4DC9F
<snip>
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
[COLOR="Red"]depends:        crc-ccitt[/COLOR]
staging:        Y
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```

---

### Post by Darkened35 on 2011-08-07
saryth@saryth-K7VT2:~$ lsmod | grep rt2
rt2870sta             410104  1 
crc_ccitt              12595  2 rt2870sta,irda
saryth@saryth-K7VT2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"The Awesomesauce Network"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: F0:7D:68:12:77:C3   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-41 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

saryth@saryth-K7VT2:~$ dmesg | grep rt2
[   10.945407] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.785805] usbcore: registered new interface driver rt2870
[   14.622203] <==== rt28xx_init, Status=0
[   15.612671] <==== rt28xx_init, Status=0
saryth@saryth-K7VT2:~$ modinfo rt2870sta | grep filename
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
saryth@saryth-K7VT2:~$ 
Thanks for going though this trouble :)

---

### Post by chili555 on 2011-08-07
> <==== rt28xx_init, Status=0I'm not quite I understand this. I wonder if Network Manager is operating correctly:```
sudo cat /var/log/syslog | grep etwork | tail -n25
```> wlan0 Ralink STA ESSID:"The Awesomesauce Network" Nickname:"RT2870STA"Some driver and Network Manager combinations are troubled by ESSIDs with spaces in the name; you have two spaces. If this is your network, I'd consider changing the name to Awesomesauce.

---

### Post by Darkened35 on 2011-08-07
Changed my network name, still 3.6 kb/s. Here's the output for that command.
```

Aug  7 21:42:20 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info>   address 192.168.0.3
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info>   prefix 24 (255.255.255.0)
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info>   gateway 192.168.0.1
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info>   nameserver '192.168.0.1'
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info>   domain name 'Home'
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Scheduling stage 5
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Done scheduling stage 5
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  7 21:42:36 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  7 21:42:37 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug  7 21:42:37 saryth-K7VT2 NetworkManager[405]: <info> Policy set 'Auto Awesomesauce' (wlan0) as default for IPv4 routing and DNS.
Aug  7 21:42:37 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) successful, device activated.
Aug  7 21:42:37 saryth-K7VT2 NetworkManager[405]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  7 21:44:09 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Aug  7 21:44:09 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug  7 21:44:14 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug  7 21:44:14 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug  7 21:44:15 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  7 21:44:15 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  7 21:44:15 saryth-K7VT2 NetworkManager[405]: <info> (wlan0): supplicant connection state:  group handshake -> completed

```

---

### Post by Darkened35 on 2011-08-08
Bump.
It may be the driver? I don't know if it's an old version.

---

### Post by chili555 on 2011-08-08
> $ lsmod | grep rt2
rt2870sta 410104 1
crc_ccitt 12595 2 rt2870sta,[COLOR="Red"]irda[/COLOR]Do you have an infrared device connected? I am very concerned about rt2500pci loading when you do not have a PCI device!

---

### Post by Darkened35 on 2011-08-08
No, but I do believe that I DO have a PCI device. I had a PC with a PCI antenna and I think I moved it to the current one, but the antenna snapped. I just took it out now.

---

### Post by chili555 on 2011-08-08
Do you mean, I hope, that you took it out of the computer physically? If so, please reboot so that we have a clean slate and run and post:```
dmesg | grep rt2
lsmod | grep -e rt2 -e irda
```Is your speed improved or unchanged?

---

### Post by Darkened35 on 2011-08-08
Ever so slight increase. I'm starting to wonder if it's the wi-fi adapter itself? Here's the output.```
saryth@saryth-K7VT2:~$ dmesg | grep rt2
[   10.979837] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.604888] usbcore: registered new interface driver rt2870
[   14.823434] <==== rt28xx_init, Status=0
[   15.862768] <==== rt28xx_init, Status=0
[  252.117596] <==== rt28xx_init, Status=0
[  319.580974] <==== rt28xx_init, Status=0
saryth@saryth-K7VT2:~$ lsmod | grep -e rt2 -e irda
rt2870sta             410104  1 
irda                  185091  1 via_ircc
crc_ccitt              12595  2 rt2870sta,irda
saryth@saryth-K7VT2:~$ 

```

---

### Post by chili555 on 2011-08-08
Please try an experiment. We will temporarily remove *irda* and see what, if anything, it improves:```
sudo rmmod -f irda
```Now tell us if there is any change.

---

### Post by Darkened35 on 2011-08-09
It says error removing irda: resource temporarily unavailable.

---

### Post by chili555 on 2011-08-09
May I please see your entire *dmesg*? Please do:```
dmesg > dark.txt
lsmod >> dark.txt
zip dark.zip dark.txt
```You will find the file dark.zip in your user directory. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by Darkened35 on 2011-08-09
The internet speed is fluctuating between 10 to 30kb/s while the speed on the netbook is 300. Here's the file

---

### Post by Darkened35 on 2011-08-10
For some reason, it's now working at a decent speed for web browsing. Whether or not this USB needs some sort of "breaking in period" is beyond me. Sorry for using more of your time that I probably didn't need. Thank you so much for the effort.

---

