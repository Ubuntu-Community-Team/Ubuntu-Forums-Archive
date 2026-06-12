---
title: "[64 bit] Intel Advanced-N 620says connected but can't get to any website"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by slow2anger on 2012-06-03
Hi,

I did a clean install of 64-bit Ubuntu 12.04 alternative and internet was working fine for a while.  Then, it just stopped working.  More specifically, both wireless and wired (when I plugged in the cable) say connected  according to the Network Manager.  However, there is no internet  whatsoever when visiting any website.  Curiously, I can connect to my  wireless router through the web browser interface fine.  I don't think  it's the problem of my modem or router, as internet works fine with them  on another computer.  Here are the requested output.  Please help.   Thanks!

The laptop is Lenovo T420s.

---

### Post by slow2anger on 2012-06-03
Here is some diagnostic output.

##################################################  #########
hshu@magician:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)

##################################################  #########
hshu@magician:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Spirit] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        10:0B:A9:BE:89:AC

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-0D72:       Infra, 00:1D:CF:9E:0D:70, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    ingenic:         Infra, 74:44:01:3F:4C:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Haridlink:       Infra, 5C:grin:9:98:63:02:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    totalnaporazka:  Infra, 00:26:F2:94:B3:grin:5, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    2WIRE823:        Infra, 3C:EA:4F:grin:2:6F:09, Freq 2432 MHz, Rate 54 Mb/s, Strength 52 WPA
    Semaphore:       Infra, 00:25:4B:06:AB:grin:F, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Fabricio Sousa's Guest Network: Infra, 72:73:CB:BC:9E:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    fb3:             Infra, B8:C7:5D:06:08:6C, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2
    fb3:             Infra, B8:C7:5D:06:08:6B, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    *Spirit:         Infra, 00:16:01:grin:6:1A:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 76 WPA2
    cocobread:       Infra, 70:73:CB:BC:9E:65, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    QuesoGrande:     Infra, 00:22:75:9F:71:88, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    attwifi:         Infra, F0:7D:68:16:B9:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 24

  IPv4 Settings:
    Address:         192.168.11.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:grin:E:F1:grin:8:7C:27

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##################################################  #########
hshu@magician:~$ dmesg | grep wlan
[   19.429389] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.429598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.944642] wlan0: authenticate with b8:c7:5d:06:08:6b (try 1)
[   26.947233] wlan0: authenticated
[   26.947444] wlan0: associate with b8:c7:5d:06:08:6b (try 1)
[   26.955779] wlan0: RX AssocResp from b8:c7:5d:06:08:6b (capab=0x431 status=0 aid=1)
[   26.955782] wlan0: associated
[   26.966040] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.677115] wlan0: deauthenticating from b8:c7:5d:06:08:6b by local choice (reason=3)
[   32.494352] wlan0: authenticate with 00:16:01:d6:1a:51 (try 1)
[   32.527743] wlan0: authenticated
[   32.579979] wlan0: associate with 00:16:01:d6:1a:51 (try 1)
[   32.739536] wlan0: RX AssocResp from 00:16:01:d6:1a:51 (capab=0x411 status=0 aid=3)
[   32.739546] wlan0: associated
[   43.345521] wlan0: no IPv6 routers present

---

### Post by praseodym on 2012-06-03
Hi,

deactivate the N-mode of the driver (Bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by chili555 on 2012-06-03
Let's create a file:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Use kate, nano or leafpad if you don't have the text editor gedit. Add a single line:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. Now let's unload and reload the driver so it picks up the new module parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Any improvement?

EDIT: Our solutions crossed. They are functionally the same, so either is effective.

---

### Post by slow2anger on 2012-06-03
No, the problem still persists.  Please let me know if you want more diagnostic outputs from me.

---

### Post by slow2anger on 2012-06-04
Hi,

I have finally decided to do a clean install of 11.10 alternate amd64 instead.  It now seems to work.  (During the installation, it didn't prompt me with the attached anymore.)  Thanks for your help anyway.

---

### Post by gmh on 2012-06-05
I got exactly the same bug. Same warning on install. Wifi worked as advertised right out of a fresh install, then stopped although my wired stayed working. Does anyone know how the fix for this is coming along?

---

### Post by chili555 on 2012-06-05
> **gmh said:**
> I got exactly the same bug. Same warning on install. Wifi worked as advertised right out of a fresh install, then stopped although my wired stayed working. Does anyone know how the fix for this is coming along?Please run:```
sudo modprobe iwlwifi
dmesg | grep iwl
```What is the firmware it needs but can't find?

---

### Post by gmh on 2012-06-05
Nothing for the first command.> garry@ubuntu:~$ sudo modprobe iwlwifi
garry@ubuntu:~$ dmesg | grep iwl
[    3.531444] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.531500] iwlwifi 0000:03:00.0: setting latency timer to 64
[    3.531562] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    3.531564] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900057bc000
[    3.531567] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[    3.531689] iwlwifi 0000:03:00.0: irq 43 for MSI/MSI-X
[    3.531767] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.531891] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.541485] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[    3.541488] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[    3.541489] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[    3.541885] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.871023] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[    3.873683] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.831481] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    4.831671] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.115726] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.115918] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   96.073598] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 72:96:a0:de:27:0c tid = 0


---

### Post by gmh on 2012-06-05
As a follow up. I am connected to wireless now but I have turned "N" of at the router. Connected via B & G only.

---

### Post by chili555 on 2012-06-05
> **gmh said:**
> As a follow up. I am connected to wireless now but I have turned "N" of at the router. Connected via B & G only.Until a bug is resolved in iwlwifi, I'm afraid that disabling N at either the card or the router is the only way.

---

### Post by gmh on 2012-06-05
What's got me puzzled is why it worked then stopped. Odd and mildly annoying.
Can I temporarily turn off N on my laptop? I don't mind rerunning the commands after a restart... just means its easy to reset if a fix comes out.

---

### Post by chili555 on 2012-06-05
> just means its easy to reset if a fix comes out.We've been waiting for...well, years. I suggest this fix. Let's create a file:

```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```

Use kate, nano or leafpad if you don't have the text editor gedit. Add a single line:
```
options iwlwifi 11n_disable=1
```
Proofread carefully, save and close gedit. Now let's unload and reload the driver so it picks up the new module parameter:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

If it's ever fixed, simply delete the file and reboot:```
sudo rm /etc/modprobe.d/iwlwifi.conf
```

---

### Post by gmh on 2012-06-05
Thanks so much Chili. Your help is much appreciated. Quite disappointing that a fix is not forthcoming as it seems to effect quite a number of people.

* File added and N turned back on at the router and ops normal. Thanks again.

---

### Post by gmh on 2012-06-12
I stumbled across a solution to my not being able to connect to a wireless N router. I was suffering random hard locks... mainly seemed to be triggered by scrolling pages in a browser. The problem and solution are as per [http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html)
The good news is the kernel update not only fixed my hard-locks but I can now connect to a wireless N router. Double victory.
I have seen nor experienced any issues since the kernel upgrade.

Cheers

---

### Post by chili555 on 2012-06-12
> **gmh said:**
> I stumbled across a solution to my not being able to connect to a wireless N router. I was suffering random hard locks... mainly seemed to be triggered by scrolling pages in a browser. The problem and solution are as per [http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html)
The good news is the kernel update not only fixed my hard-locks but I can now connect to a wireless N router. Double victory.
I have seen nor experienced any issues since the kernel upgrade.

CheersThe link you posted doesn't mention iwlwifi or Intel Centrino wireless, so there is no evidence the later kernel is a fix. We appreciate your update, nonetheless.

---

### Post by gmh on 2012-06-12
Understood it doesn't mention a fix for the Intel card and iwlwifi but it seems to be a side effect of the Kernel upgrade. Before I had no N connection.... now I do. Whatever was in that Kernel package seems to have cured my ills for now. Fingers crossed it stays that way.

---

### Post by chili555 on 2012-06-12
> **gmh said:**
> Understood it doesn't mention a fix for the Intel card and iwlwifi but it seems to be a side effect of the Kernel upgrade. Before I had no N connection.... now I do. Whatever was in that Kernel package seems to have cured my ills for now. Fingers crossed it stays that way.We need a test pilot with an Intel card and N issues. Any volunteers??

---

### Post by gmh on 2012-06-19
The joys. Now I have the random drop out of wireless bug. Aye carumba! Seems to happen as soon as the data requirement ramps up but its not uniform. Disabled IPV6 and no improvement. Turning off and turning on the Wireless with the hardware switch would bring it back. My Nm-applet was randomly locking up as well. Uninstalled Network Manager and replaced it with Wicd. A few hours in and things seem to have improved with no drop outs. Never had as many issues with wireless as I have had in 12.04.

Note this is all on a fresh install on a Lenovo T420.

*Dropped out - not a fix*

---

### Post by gmh on 2012-06-20
Finally a stable wireless Connection.

Kernel 3.2.0.25.27 and WICD seem to have done the job. I wish I had further insight but it seems kernel related as per this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/911059]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/911059"). It maybe that its fine with Network Manager now as well, however I will stick with Wicd for the time being because a) its working well and; b)the Nm-applet has been giving me grief in Ubuntu for awhile.

---

