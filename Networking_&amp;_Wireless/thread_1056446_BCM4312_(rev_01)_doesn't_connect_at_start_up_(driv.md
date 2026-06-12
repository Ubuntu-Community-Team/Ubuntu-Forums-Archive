---
title: "BCM4312 (rev 01) doesn't connect at start up (drivers installed)"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by SlingerXL on 2009-01-31
I have a BCM4312 rev 01 on a Dell Inspiron 1525. I used this thread: [http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4312](http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4312) to set it up and it works, but only if I go to System>Administration>Hardware Drivers and click to enable the BCM driver. However, it never actually says that the driver is enabled in the GUI it actually still says it's not enabled and NM just starts connecting. Also, I get the "System Restart Required" message when I click to enable the driver. 

How do I make the GUI recognize that I clicked to enable the driver? I think the answer to this is the same as the answer my next question which is how do I not get that system restart required message.

Also, how do I get the driver to be used at startup?


Here's my lshw -C network after I enable the driver:

dan@dan-laptop:~$ sudo lshw -C network
[sudo] password for dan: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:f6:f9:1a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:3f:db:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.27.12 ip=192.168.1.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by pytheas22 on 2009-01-31
If you run this command once:
```

echo wl | sudo tee -a /etc/modules
```

then reboot, does your wireless work automatically?  I suspect that the problem is that the driver for your card is not being auto-loaded for some reason and you have to load it explicitly using Hardware Drivers, but this should solve that problem.

---

### Post by SlingerXL on 2009-02-02
> **pytheas22 said:**
> If you run this command once:
```

echo wl | sudo tee -a /etc/modules
```

then reboot, does your wireless work automatically?  I suspect that the problem is that the driver for your card is not being auto-loaded for some reason and you have to load it explicitly using Hardware Drivers, but this should solve that problem.

What does that code mean? Like echo and all that. I only really understand the sudo and I assume /etc/modules is where the driver is?

---

### Post by Ayuthia on 2009-02-02
> **SlingerXL said:**
> What does that code mean? Like echo and all that. I only really understand the sudo and I assume /etc/modules is where the driver is?

echo just prints out what shows up after the echo command.  In this case it is wl.

The tee command takes the input and places it into the file listed after the tee.  The -a appends instead of overwrites.  So in this case the wl will get appended to /etc/modules.

/etc/modules is a file that contains kernel modules that aren't loaded by the kernel automatically.  The system will look at this file after it loads the kernel modules and checks to see if there are any additional modules to load.  So having the wl module in this file will allow the wl module to load when the system starts up.

Hope that helps.

---

### Post by smothpocket on 2009-02-02
I've always had better luck with this guide as opposed to using ndiswrapper with my bcm wifi

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

---

### Post by kevdog on 2009-02-02
The best way to help you is for you to re-boot, and then take a look at lshw -C network and post what is said in the driver statement under your card.  It could be some other modules, like b43, ssb, etc need to be unloaded and then wl loaded, and then b44, ssb reloaded.

---

### Post by Ericj1186 on 2009-05-17
All right, same card, but different issue.  I installed the FWcutter per this site: [http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation), and my wireless card can see my router.  When I type in my router's password, it says connected to the router, but then it asks me for the password again.  If I click out, it will disconnect.  I cannot view any websites.

Any ideas?

---

### Post by pytheas22 on 2009-05-17
> All right, same card, but different issue. I installed the FWcutter per this site: [http://linuxwireless.org/en/users/Dr...reinstallation](http://linuxwireless.org/en/users/Dr...reinstallation), and my wireless card can see my router. When I type in my router's password, it says connected to the router, but then it asks me for the password again. If I click out, it will disconnect. I cannot view any websites.

Any ideas?

That sounds most likely like a problem with NetworkManager.  You may want to try installing wicd instead.  You can install wicd by typing these commands (you will need to be connected to the Internet via the wire first; if that's impossible, let me know):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu and try connecting.

---

### Post by Ericj1186 on 2009-05-17
All right, I got the wicd manager, but when I try to connect, I type in the router password and press connect.  It works fine, then it gets stuck on "Obtaining IP address"  Any idea why?  I know the wireless works because I am on it now.  Maybe there is a manual way I can do this?

I tried to do a static IP, but it stopped at "Validating Authenticity."  I thought that may have solved it, but no go.

---

### Post by pytheas22 on 2009-05-17
All right, I got the wicd manager, but when I try to connect, I type in the router password and press connect. It works fine, then it gets stuck on "Obtaining IP address" Any idea why? I know the wireless works because I am on it now. Maybe there is a manual way I can do this?

I tried to do a static IP, but it stopped at "Validating Authenticity." I thought that may have solved it, but no go.

Please post the output of these commands so I know exactly which kind of hardware you have:
```

lspci -nn | grep -i broadcom
lshw -C Network
ls -l /lib/firmware
sudo iwlist scan
```

Please also let me know the name of your wireless network.  It may be useful to try connecting to it from the command line.

Also, can you connect if you disable encryption on your router?
> 
I know the wireless works because I am on it now.

To be clear: you mean you're connected under a different operating system?  Or are you connected and using the wireless Internet under Ubuntu somehow, and I'm misunderstanding your problem?

---

### Post by Ericj1186 on 2009-05-18
To clarify:  I have another laptop, and I was on the wireless network. 

My router name is 2Wire598.  I'm not really sure how to disable encryption, and here is what my output was for those commands.

**lspci -nn | grep -i broadcom**:```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```
[B]
lshw -C Network[/B]:```
  *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:d9:5f:32:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a8:50:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:80:6f:4a:be:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
[B]
ls -l /lib/firmware[/B]:```
total 6524
drwxr-xr-x 14 root root   4096 2009-04-20 09:31 2.6.28-11-generic
drwxr-xr-x 13 root root   4096 2009-04-20 09:34 acx
-rw-r--r--  1 root root  22622 2009-04-02 16:46 aic94xx-seq.fw
-rw-r--r--  1 root root  30348 2009-04-02 16:46 atmel_at76c502_3com.bin
-rw-r--r--  1 root root  35184 2009-04-02 16:46 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root  31764 2009-04-02 16:46 atmel_at76c502.bin
-rw-r--r--  1 root root  31764 2009-04-02 16:46 atmel_at76c502d.bin
-rw-r--r--  1 root root  35276 2009-04-02 16:46 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root  31776 2009-04-02 16:46 atmel_at76c502e.bin
-rw-r--r--  1 root root  35272 2009-04-02 16:46 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root  35276 2009-04-02 16:46 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root  28156 2009-04-02 16:46 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root  28032 2009-04-02 16:46 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root  35372 2009-04-02 16:46 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root  37800 2009-04-02 16:46 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root  37956 2009-04-02 16:46 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root  35180 2009-04-02 16:46 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root  39928 2009-04-02 16:46 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root  31748 2009-04-02 16:46 atmel_at76c504.bin
-rw-r--r--  1 root root  35196 2009-04-02 16:46 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root  37005 2009-04-02 16:46 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root  36992 2009-04-02 16:46 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root  35528 2009-04-02 16:46 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root  31824 2009-04-02 16:46 atmel_at76c506.bin
-rw-r--r--  1 root root  35228 2009-04-02 16:46 atmel_at76c506-wpa.bin
drwxr-xr-x  2 root root   4096 2009-05-17 00:36 b43
drwxr-xr-x  2 root root   4096 2009-05-17 00:36 b43legacy
-rw-r--r--  1 root root 114688 2009-04-02 16:46 BCM2033-FW.BIN
-rw-r--r--  1 root root   3245 2009-04-02 16:46 BCM2033-MD.BIN
-rw-r--r--  1 root root  32522 2009-04-02 16:46 dvb-fe-cx24116.fw
-rw-r--r--  1 root root  12772 2009-04-02 16:46 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root  17532 2009-04-02 16:46 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root   8518 2009-04-02 16:46 dvb-fe-or51211.fw
-rw-r--r--  1 root root  24478 2009-04-02 16:46 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 239956 2009-04-02 16:46 dvb-ttpci-01.fw
-rw-r--r--  1 root root  12700 2009-04-02 16:46 dvb-usb-af9015.fw
-rw-r--r--  1 root root  10757 2009-04-02 16:46 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root   9025 2009-04-02 16:46 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root  34306 2009-04-02 16:46 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root  33768 2009-04-02 16:46 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   9180 2009-04-02 16:46 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   7558 2009-04-02 16:46 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root   7431 2009-04-02 16:46 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   3360 2009-04-02 16:46 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root   4286 2009-04-02 16:46 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root  10752 2009-04-02 16:46 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root  10752 2009-04-02 16:46 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root   8480 2009-04-02 16:46 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root  12902 2009-04-02 16:46 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root   8518 2009-04-02 16:46 dvb-usb-wt220u-zl0353-01.fw
-rw-r--r--  1 root root 209190 2009-04-02 16:46 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2009-04-02 16:46 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2009-04-02 16:46 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2009-04-02 16:46 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2009-04-02 16:46 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2009-04-02 16:46 ipw2200-sniffer.fw
-rw-r--r--  1 root root 112128 2009-04-02 16:46 isl3877
-rw-r--r--  1 root root  29024 2009-04-02 16:46 isl3886
-rw-r--r--  1 root root  30060 2009-04-02 16:46 isl3887usb_bare
-rw-r--r--  1 root root  93996 2009-04-02 16:46 isl3890
-rw-r--r--  1 root root  29468 2009-04-02 16:46 isl3890usb
-rw-r--r--  1 root root 149652 2009-04-02 16:46 iwlwifi-3945-1.ucode
-rw-r--r--  1 root root 149816 2009-04-02 16:46 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root 187608 2009-04-02 16:46 iwlwifi-4965-1.ucode
-rw-r--r--  1 root root 187764 2009-04-02 16:46 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root 345008 2009-04-02 16:46 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root 118884 2009-04-02 16:46 lbtf_usb.bin
lrwxrwxrwx  1 root root     14 2009-05-15 01:50 NPE-B -> NPE-B.01020201
-rw-r--r--  1 root root  15664 2009-02-13 15:30 NPE-B.01020201
lrwxrwxrwx  1 root root     14 2009-05-15 01:50 NPE-C -> NPE-C.02020201
-rw-r--r--  1 root root  15664 2009-02-13 15:30 NPE-C.02020201
-rw-r--r--  1 root root  76802 2009-04-02 16:46 ql2100_fw.bin
-rw-r--r--  1 root root  84566 2009-04-02 16:46 ql2200_fw.bin
-rw-r--r--  1 root root 123170 2009-04-02 16:46 ql2300_fw.bin
-rw-r--r--  1 root root 132978 2009-04-02 16:46 ql2322_fw.bin
-rw-r--r--  1 root root 206500 2009-04-02 16:46 ql2400_fw.bin
-rw-r--r--  1 root root   8192 2009-04-02 16:46 rt2561.bin
-rw-r--r--  1 root root   8192 2009-04-02 16:46 rt2561s.bin
-rw-r--r--  1 root root   8192 2009-04-02 16:46 rt2661.bin
-rw-r--r--  1 root root   8192 2009-04-02 16:46 rt2860.bin
-rw-r--r--  1 root root   4096 2009-04-02 16:46 rt2870.bin
-rw-r--r--  1 root root   2048 2009-04-02 16:46 rt73.bin
-rw-r--r--  1 root root 141200 2009-04-02 16:46 v4l-cx23418-apu.fw
-rw-r--r--  1 root root 158332 2009-04-02 16:46 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root  16382 2009-04-02 16:46 v4l-cx23418-dig.fw
-rw-r--r--  1 root root 262144 2009-04-02 16:46 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root 376836 2009-04-02 16:46 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2009-04-02 16:46 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root  16382 2009-04-02 16:46 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root 376836 2009-04-02 16:46 v4l-cx23885-enc.fw
-rw-r--r--  1 root root  16382 2009-04-02 16:46 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2009-04-02 16:46 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2009-04-02 16:46 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root  62484 2009-04-02 16:46 zd1201-ap.fw
-rw-r--r--  1 root root  70612 2009-04-02 16:46 zd1201.fw
drwxr-xr-x  2 root root   4096 2009-04-20 09:34 zd1211

```
[B]
sudo iwlist scan[/B]:```
eth1      Scan completed :
          Cell 01 - Address: 00:1F:45:22:8E:80
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1F:45:22:8E:A0
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-54 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1F:45:22:8E:D0
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-52 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:11:88:DD:62:80
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:1F:45:22:8E:D1
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency=5.18 GHz (Channel 36)
                    Quality:5/5  Signal level:-52 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:11:88:DD:62:81
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency=5.2 GHz (Channel 40)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-86 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:1F:45:22:8E:A1
                    ESSID:"NSUnwired"
                    Mode:Managed
                    Frequency=5.22 GHz (Channel 44)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s


```

I scanned the iwlist while at school, so their networks came up.  I cannot connect to them anyway (same error as before).  Thanks for any help with this.

---

### Post by pytheas22 on 2009-05-18
I don't know why it's not working, as your driver looks good.  But please run these commands, which will install a different driver that may work better.  You will need to plug into the Internet before running these commands (if you have no way to do that, let me know and we can work around it):
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 cabextract
echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist.conf
mkdir wifi
cd wifi
wget http://ftp.us.dell.com/network/R140747.EXE
unzip R140747.EXE
sudo ndiswrapper -i DRIVER/bcmwl5.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot, and try connecting again.  If it still doesn't work, please post the output of:
```

ndiswrapper -l
sudo iwlist scan
uname -rm
dmesg | grep -e ndis -e wlan
lshw -C Network
```

---

### Post by Ericj1186 on 2009-05-18
pytheas, that worked perfectly except for the second to last code: **sudo ndiswrapper -i DRIVER/bcmw15.inf**.  The terminal returned that it couldn't find the directory.

I rebooted, and now, I am connected.  Thanks so much.

---

### Post by pytheas22 on 2009-05-18
> pytheas, that worked perfectly except for the second to last code: sudo ndiswrapper -i DRIVER/bcmw15.inf. The terminal returned that it couldn't find the directory.

I rebooted, and now, I am connected. Thanks so much.

It looks like you typed 'bcmw15' instead of 'bcmwl5' (the character between the 'w' and the '5' is a lowercase L, not a number 1), hence the error message.  I'm a bit surprised that it worked because it shouldn't have without that command succeeding.  But I guess we should leave well-enough alone; I'm glad you're online now.

---

### Post by A_Fiachra on 2009-09-28
> **pytheas22 said:**
> That sounds most likely like a problem with NetworkManager.  You may want to try installing wicd instead.  You can install wicd by typing these commands (you will need to be connected to the Internet via the wire first; if that's impossible, let me know):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```Then launch it from the Applications>Internet menu and try connecting.



Thank You!


This worked for me -- though I did not have to add [http://apt.wicd.net](http://apt.wicd.net) hardyto my source list.  I got rid of that pain in the tuchus NetworkManager applet (which has caused me more headaches than I care to comment about) and am now using Wicd Manager.

My advice to ANYONE having networking issues -- first -- GET RID OF NetworkManager!!!!!!!!

---

### Post by pytheas22 on 2009-09-28
> 
This worked for me -- though I did not have to add [http://apt.wicd.net](http://apt.wicd.net) hardyto my source list. I got rid of that pain in the tuchus NetworkManager applet (which has caused me more headaches than I care to comment about) and am now using Wicd Manager.

My advice to ANYONE having networking issues -- first -- GET RID OF NetworkManager!!!!!!!!

Glad it helped, and thanks for letting us know.  You're right that as of Ubuntu 9.04, wicd is included in the default Ubuntu repositories, so you can just type "sudo apt-get install wicd" without having to edit your sources list first (older versions of Ubuntu still require manually editing the sources list).

---

### Post by bonnmac on 2009-11-03
I am having a similar problem.  I have followed all the instructions in this thread to no avail.  My laptop is a Dell Inspiron 1526 and I installed ubuntu using wubi. I have Windows Vista Home Premium installed also.  Any help would be greatly appreciated.  Thanks!


I have done the following:
```
echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```I rebooted still doesn't connect

Below you will find the results of the following commands

```
lspci -nn | grep -i broadcom
lshw -C Network
ls -l /lib/firmware
sudo iwlist scan
```0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:09:4a:84:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:ce00(size=256) memory:fe5ff400-fe5ff4ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:fc:71:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg



ls -l /lib/firmware
total 9800
drwxr-xr-x 29 root root    4096 2009-10-27 11:00 2.6.31-14-generic
drwxr-xr-x 13 root root    4096 2009-10-27 11:05 acx
-rw-r--r--  1 root root   22622 2009-10-17 15:55 aic94xx-seq.fw
-rw-r--r--  1 root root   83968 2009-10-17 15:55 ar9170-1.fw
-rw-r--r--  1 root root    3508 2009-10-17 15:55 ar9170-2.fw
-rw-r--r--  1 root root   15960 2009-10-17 15:55 ar9170.fw
-rw-r--r--  1 root root   30348 2009-10-17 15:55 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   35184 2009-10-17 15:55 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root   31764 2009-10-17 15:55 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 2009-10-17 15:55 atmel_at76c502d.bin
-rw-r--r--  1 root root   35276 2009-10-17 15:55 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root   31776 2009-10-17 15:55 atmel_at76c502e.bin
-rw-r--r--  1 root root   35272 2009-10-17 15:55 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root   35276 2009-10-17 15:55 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root   28156 2009-10-17 15:55 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root   28032 2009-10-17 15:55 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root   35372 2009-10-17 15:55 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root   37800 2009-10-17 15:55 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root   37956 2009-10-17 15:55 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root   35180 2009-10-17 15:55 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root   39928 2009-10-17 15:55 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root   31748 2009-10-17 15:55 atmel_at76c504.bin
-rw-r--r--  1 root root   35196 2009-10-17 15:55 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root   37005 2009-10-17 15:55 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root   36992 2009-10-17 15:55 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root   35528 2009-10-17 15:55 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root   31824 2009-10-17 15:55 atmel_at76c506.bin
-rw-r--r--  1 root root   35228 2009-10-17 15:55 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root  114688 2009-10-17 15:55 BCM2033-FW.BIN
-rw-r--r--  1 root root    3245 2009-10-17 15:55 BCM2033-MD.BIN
-rw-r--r--  1 root root   12401 2009-10-17 15:55 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 2009-10-17 15:55 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root 1142480 2009-10-17 15:55 i2400m-fw-usb-1.3.sbcf
-rw-r--r--  1 root root 1251036 2009-10-17 15:55 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root  209190 2009-10-17 15:55 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2009-10-17 15:55 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2009-10-17 15:55 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2009-10-17 15:55 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2009-10-17 15:55 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2009-10-17 15:55 ipw2200-sniffer.fw
-rw-r--r--  1 root root  112128 2009-10-17 15:55 isl3877
-rw-r--r--  1 root root   29036 2009-10-17 15:55 isl3886pci
-rw-r--r--  1 root root   29500 2009-10-17 15:55 isl3886usb
-rw-r--r--  1 root root   29736 2009-10-17 15:55 isl3887usb
-rw-r--r--  1 root root   93996 2009-10-17 15:55 isl3890
-rw-r--r--  1 root root  335056 2009-10-17 15:55 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  149652 2009-10-17 15:55 iwlwifi-3945-1.ucode
-rwxr-xr-x  1 root root  150100 2009-10-17 15:55 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187608 2009-10-17 15:55 iwlwifi-4965-1.ucode
-rwxr-xr-x  1 root root  187972 2009-10-17 15:55 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2009-10-17 15:55 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2009-10-17 15:55 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2009-10-17 15:55 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  459992 2009-10-17 15:55 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  118884 2009-10-17 15:55 lbtf_usb.bin
lrwxrwxrwx  1 root root      14 2009-11-02 23:30 NPE-B -> NPE-B.01020201
-rw-r--r--  1 root root   15664 2009-10-13 12:41 NPE-B.01020201
lrwxrwxrwx  1 root root      14 2009-11-02 23:30 NPE-C -> NPE-C.02020201
-rw-r--r--  1 root root   15664 2009-10-13 12:41 NPE-C.02020201
-rw-r--r--  1 root root   76802 2009-10-17 15:55 ql2100_fw.bin
-rw-r--r--  1 root root   84566 2009-10-17 15:55 ql2200_fw.bin
-rw-r--r--  1 root root  123170 2009-10-17 15:55 ql2300_fw.bin
-rw-r--r--  1 root root  132978 2009-10-17 15:55 ql2322_fw.bin
-rw-r--r--  1 root root  206500 2009-10-17 15:55 ql2400_fw.bin
-rw-r--r--  1 root root    8192 2009-10-17 15:55 rt2561.bin
-rw-r--r--  1 root root    8192 2009-10-17 15:55 rt2561s.bin
-rw-r--r--  1 root root    8192 2009-10-17 15:55 rt2661.bin
-rw-r--r--  1 root root    8192 2009-10-17 15:55 rt2860.bin
-rw-r--r--  1 root root    4096 2009-10-17 15:55 rt2870.bin
-rw-r--r--  1 root root    2048 2009-10-17 15:55 rt73.bin
-rw-r--r--  1 root root  141200 2009-10-17 15:55 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 2009-10-17 15:55 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 2009-10-17 15:55 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 2009-10-17 15:55 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 2009-10-17 15:55 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 2009-10-17 15:55 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 2009-10-17 15:55 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root  376836 2009-10-17 15:55 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 2009-10-17 15:55 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 2009-10-17 15:55 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 2009-10-17 15:55 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root   62484 2009-10-17 15:55 zd1201-ap.fw
-rw-r--r--  1 root root   70612 2009-10-17 15:55 zd1201.fw
drwxr-xr-x  2 root root    4096 2009-10-27 11:05 zd1211



sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:03:CE:95
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/100  Signal level=20/100  
                    Encryption key:off
                    ESSID:"macvog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d852e6d9d
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00066D6163766F67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000


I followed the following commands

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 cabextract
echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist.conf
mkdir wifi
cd wifi
wget http://ftp.us.dell.com/network/R140747.EXE
unzip R140747.EXE
sudo ndiswrapper -i DRIVER/bcmwl5.inf
echo ndiswrapper | sudo tee -a /etc/modules
```Below you will find the results of the following commands:

```
ndiswrapper -l
sudo iwlist scan
uname -rm
dmesg | grep -e ndis -e wlan
lshw -C Network
```bcmwl5 : driver installed


sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:03:CE:95
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/100  Signal level=20/100  
                    Encryption key:off
                    ESSID:"macvog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d8fc89b1f
                    Extra: Last beacon: 50ms ago
                    IE: Unknown: 00066D6163766F67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000



2.6.31-14-generic x86_64


dmesg | grep -e ndis -e wlan
[    9.034390] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.390214] usbcore: registered new interface driver ndiswrapper
[   34.617618] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.917660] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.014007] wlan0: authenticate with AP 00:1c:10:03:ce:95
[   43.014033] wlan0: authenticate with AP 00:1c:10:03:ce:95
[   43.015754] wlan0: authenticated
[   43.015757] wlan0: associate with AP 00:1c:10:03:ce:95
[   43.019508] wlan0: RX AssocResp from 00:1c:10:03:ce:95 (capab=0x401 status=0 aid=1)
[   43.019511] wlan0: associated
[   43.020491] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.020020] wlan0: no IPv6 routers present



lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:09:4a:84:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:ce00(size=256) memory:fe5ff400-fe5ff4ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:fc:71:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg

---

### Post by pytheas22 on 2009-11-03
bonnmac: from the output you posted, everything looks like it should be working.  What is the name of the network you want to connect to?  Are you actually telling wicd to try to connect?

Ubuntu doesn't connect to wireless networks automatically (unless you configure it that way); you need to open wicd from the Applications>Internet menu, select the network you want, fill in the password settings if applicable, then tell it to connect.  What happens when you do this?

---

### Post by lol197282 on 2009-11-22
BCM4312 802.11b/g (rev 1)
Ubuntu Karmic Koala

Short answer use wl driver.

this worked for me

s43 & wl drivers were kicking lumps out of each other. removed possibilty of driver clash (restricted drvers thing didn't work).
(opened terminal input the following)
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r wl

sudo apt-get remove b43-fwcutter
sudo apt-get remove bcmwl-modaliases
sudo apt-get remove bcmwl-kernel-source



blacklisted a few things just to be sure
sudo gedit /etc/modprobe.d/blacklist.conf
(add the following lines)
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist wl

and

sudo gedit /etc/modprobe.d/blacklist-ssb.conf

blacklist ssb

restart

sudo apt-get install bcmwl-modaliases
sudo apt-get install bcmwl-kernel-source

restart

commment out wl module from the blacklist

sudo gedit /etc/modprobe.d/blacklist.conf

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
#blacklist wl

sudo modprobe wl


sudo gedit /etc/modules
(add theline below)
wl


(strange thing I'm lleft with a wireless device called eth2 instead of wlan0 still functions fine with wpa & wep encryption)

The Short way may work. just use wl driver

sudo modprobe -r b43 ssb wl
sudo apt-get install bcmwl-modaliases
sudo apt-get install bcmwl-kernel-source

sudo gedit /etc/modprobe.d/blacklist.conf
blacklist b43

reboot.

---

### Post by Ocyberbum on 2009-12-19
I just wanted to say that this command worked for me also
sudo apt-get install wicd
I have a Dell Mini9 Broadcom 4312 and i couldn't connect with my WPA-TSK key but this worked great, i just hope i can tether my HTC touch pro still

---

