---
title: "TL-WN422G not working in 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by soulseek on 2009-11-01
I just bought a TL-WN422G but its not working out of the box on ubuntu. It works alright in windows.

```
sudoeste@sudo:~$ lsusb
Bus 002 Device 005: ID 0cf3:1006 Atheros Communications, Inc. 

```

Dmesg output when inserting usb:
```

[ 1959.704069] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 1959.853819] usb 2-1: configuration #1 chosen from 1 choice

```

Can somebody help me getting this to work ? Tried 9.04, 9.10 both x86 and x64

---

### Post by eldoraado on 2009-11-10
Same problem under Ubuntu 9.10 x86.

---

### Post by soulseek on 2009-11-27
no one has this card ?

---

### Post by wolfen3 on 2009-11-28
I have this card. We have to wait until Luis R. Rodriguez write drivers for us :)

Project is still in development

[http://git.kernel.org/?p=linux/kernel/git/mcgrof/ath9k_htc.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/mcgrof/ath9k_htc.git;a=summary)
[http://wireless.kernel.org/en/users/Drivers/Atheros](http://wireless.kernel.org/en/users/Drivers/Atheros)

---

### Post by Ozzypt on 2009-12-03
Any news yet?? im getting a bit desperate cant get this to work ](*,)](*,)](*,)

---

### Post by kniwor on 2010-03-04
I have the same wireless adapter and I installed x64 version of Ubuntu 9.10 yesterday. It shows the adapter out of the box, I can connect to networks just fine (all encryptions mechanisms working), and when I ping it can sucessfully resolve the hostname, but the ping itself is not sucessful. So in effect the internet connection is useless, nothing works.

---

### Post by algo_pt on 2010-03-20
Hi, cant use it either. I just bought this to use it on linux, if there is no support for it on ubuntu, then Ill return it to the shop. Its a shame because it has great sensitivity and works very very well under windows.

---

### Post by UkiUki on 2010-04-20
I have this adapter as well, i got it going with ndiswrapper but it wont connect to the available networks. The driver i used can be found here (win2k_xp): [http://www.tp-link.com/support/download.asp?a=1&m=TL-WN422G&h=V2](http://www.tp-link.com/support/download.asp?a=1&m=TL-WN422G&h=V2) , Driver version for 2K/XP 32Bit/64Bit changed to 7.7.0.51,Driver version for Vista 32Bit changed to 8.0.0.43.

I have no idea why it just don't connect, any hints?

Here some extra info:
my kernel: 2.6.31-20

```
diswrapper -l
netathuwx : driver installed
        device (0CF3:1006) present

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

dmesg
[   11.231285] usb 1-6: reset high speed USB device using ehci_hcd and address 3

[   11.451191] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver  
[   11.455478] ndiswrapper: driver netathuwx (,07/08/2009,7.7.0.51) loaded 

[   13.449875] wlan0: ethernet device 00:25:86:e6:25:12 using NDIS driver: netathuwx, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:1006.F.conf
[   13.874794] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

[   13.874860] usbcore: registered new interface driver ndiswrapper
[   14.293984] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by meatron on 2010-04-25
I bought this two days ago and made it work with compat-wireless kernel driver. What I understood is: there is 2 versions of the same type-name. If you have v2 like I do, you will need [[COLOR="DarkRed"]this driver[/COLOR]]("http://wireless.kernel.org/en/users/Drivers/ath9k_htc"). Go [[COLOR="#8b0000"]here[/COLOR]]("http://wireless.kernel.org/en/users/Download") and follow the instructions. Towards the end of the page there is an ubuntu package mentioned, it did not work for me, I had to compile it. If you have it installed, make sure to remove it before compiling the newer version.
Get the latest version from [ compat-wireless download directory ]("http://wireless.kernel.org/download/compat-wireless-2.6/"), untar it and cd into the dir ```
tar xjvf compat-wireless-$(date -I).tar.bz2
cd compat-wireless-$(date -I)

```
Select the driver for shorter build time
```
./scripts/driver-select ath9k_htc
```
Build and install
```
 make && sudo make install 
```
Now download the firmware ar9271.fw from [[COLOR="DarkRed"]kernel.org[/COLOR]]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree") and copy it to /lib/firmware. 
Reboot and voila, it works, at least here ;)

---

### Post by spehlivan on 2010-04-28
Thank you so much Meatron. It's just worked for me. Your instruction is perfect.

---

### Post by riaanjvr on 2010-05-01
Thank you; this also worked for Chinese Mercury MW54U USB wireless adapter

---

### Post by riaanjvr on 2010-05-02
Update - it does load the driver; but seems I have to unplug and re-plug the USB device every time after a reboot.

---

### Post by samhall555 on 2010-06-10
[http://dinthsblog.blogspot.com/2010/04/i-was-fighting-to-run-tp-link-wn422g-v2.html](http://dinthsblog.blogspot.com/2010/04/i-was-fighting-to-run-tp-link-wn422g-v2.html)

this works for me

---

### Post by bayvista on 2010-10-28
Hi - Anyone got this working with Lucid 10.04? I keep getting a message that 'netathuw.inf' from the CD is invalid.

---

### Post by flash63 on 2010-10-28
Hello,
a device with Atheros ath9k_htc Chipset. A Linux driver modul is available.

Info here:
[http://www.linuxwireless.org/en/users/Drivers/ath9k_htc](http://www.linuxwireless.org/en/users/Drivers/ath9k_htc)

Firmware here:
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)
(klick on "snapshot" at the upper left corner, download, unpack and copy the new files to /lib/firmware)

Driver install:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2         
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2010-*
./scripts/driver-select ath9k
make
sudo make install

```
Errors? No, test it:
```
sudo modprobe ath9k_htc
iwconfig
sudo iwlist scan
iwlist chan
```
try to connect.

---

### Post by Marcelo01 on 2012-04-02
> **flash63 said:**
> Hello,
a device with Atheros ath9k_htc Chipset. A Linux driver modul is available.

Info here:
[http://www.linuxwireless.org/en/users/Drivers/ath9k_htc](http://www.linuxwireless.org/en/users/Drivers/ath9k_htc)

Firmware here:
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)
(klick on "snapshot" at the upper left corner, download, unpack and copy the new files to /lib/firmware)

Driver install:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2         
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2010-*
./scripts/driver-select ath9k
make
sudo make install

```Errors? No, test it:
```
sudo modprobe ath9k_htc
iwconfig
sudo iwlist scan
iwlist chan
```try to connect.

I've did all steps but can get it working yet...
DMESG shows:

```
[   18.688416] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
[   18.688416] Failed to initialize the device
[   19.283504] usb 1-2: ath9k_htc: USB layer deinitialized

```And then I'm lost...:lolflag:

What else could I check ?

---

### Post by Marcelo01 on 2012-04-03
Any thoughts ?

---

### Post by cabronsaim on 2012-06-03
Hi, Linux Newbie here.

I had a hard time with this TL-WN422G (Version 2) Wireless USB and this thread solved my issues.

But the good news is I figured out how to make this easier. At least for newbies like me.

I am using Lubuntu 12.04 but this intructions are also for Ubuntu 12.04 Precise Pangolin 

I went straight to the Synaptic Package Manager in my System tools menu.

Then searched for linux-backport-modules
The searched return about a dozen files.

I selected the following:
linux-backports-modules-net-precise-server
linux-backports-modules-net-precise-generic-pae
linux-backports-modules-net-precise-generic

The following 2 installed automatically after selecting the previous 3:
linux-backports-modules-net-3.2.0-24-generic
linux-backports-modules-net-3.2.0-24-generic-pae

Then, after the installation finished,
I restarted.

Done :)

---

