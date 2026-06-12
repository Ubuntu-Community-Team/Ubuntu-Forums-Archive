---
title: "Bluetooth on Ubuntu13.04 not functioning!"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by Ravi Singh on 2013-08-21
**Bluetooth on Ubuntu13.04 not functioning!**[HR][/HR]Today I upgraded my OS from Ubuntu12.10 to Ubuntu13.04.
Though  I never tried the feature of 'bluetooth' earlier in any distribution,  but today when I tried I got as the screenshot (attachment) reveals.

It says"no bluetooth adapter found".
To  resolve this I googled. Let me tell you 1st what my goal was. I had  been connecting internet on my laptop from NokiaN73 via a cable. Now I  wanted to do the same via bluetooth and get rid of cable.

I followed what the below link says
Quote:
[TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"][http://askubuntu.com/questions/28683...n-ubuntu-13-04]("http://askubuntu.com/questions/286834/bluetooth-not-working-in-ubuntu-13-04")
[/TD]
[/TR]
[/TABLE]

And hence I ran the below commands as mentioned in the above link.
```
sudo apt-get install \
  bluetooth blueman \
  bluez-hcidump bluewho python-bluez  bluez-tools \
  brcm-patchram-plus-nexus7
```


But still the problem remains!

Then I followd the link as below:
Quote:
[TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"][http://askubuntu.com/questions/15894...-via-bluetooth]("http://askubuntu.com/questions/158942/connect-my-mobile-phone-as-modem-via-bluetooth")
[/TD]
[/TR]
[/TABLE]

This says "Click on Bluetooth icon on the panel, and Set up New Device"
I  hope the panel it mentions is the same as when I click system settings  on ubuntu13.04. Now when I click on the bluetooth icon under "hardware",  I get what I showed in the screen shot attached.

Please say how to go ahead and also let me know if I have to undo what I did by running the above commands.


Please have the output of two commands below. I am not familiar with  these commands but while looking at other threads in google, it seems  that it may be of use.
```
ravbholua@ravbholua-Aspire-5315:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
ravbholua@ravbholua-Aspire-5315:~$
```

The other command:

```
ravbholua@ravbholua-Aspire-5315:~$ sudo lsusb
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 007 Device 003: ID 0421:0486 Nokia Mobile Phones 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ravbholua@ravbholua-Aspire-5315:~$
```

---

### Post by Ravi Singh on 2013-08-26
dumb!!
Any reply please from anybody on this forum!!!

---

### Post by Ravi Singh on 2013-09-06
Anyone can reply please!!!
Thanks!!

---

### Post by tgalati4 on 2013-09-06
What is the model of the laptop?  I don't see any bluetooth.  You have loaded all of the necessary software, but you don't have a bluetooth radio on your machine.

---

