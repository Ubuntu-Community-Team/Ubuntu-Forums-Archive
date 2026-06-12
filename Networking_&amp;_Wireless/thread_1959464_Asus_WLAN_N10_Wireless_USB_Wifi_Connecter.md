---
title: "Asus WLAN N10 Wireless USB Wifi Connecter"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by Cr1scoD1sco on 2012-04-15
I am aware that there have been a few threads about this, but when I tried to follow the instructions, I had no luck.   I have only been using Ubuntu for about a week so I know very little about anything other than writing commands in the terminal and extracting files.  PLEASE keep your answers as easily understandable as possible.  Assume I know nothing (which is pretty much true). I'm running Ubuntu Studio 11.04.  The desktop I'm installing on is not connected to the internet.

So, here's my issue.  I went to my local computer store today and asked them for a Wireless USB Connecter that I could use to connect my Ubuntu desktop to the internet.  They gave me an Asus WLAN N10 which came with an Installation Disc and Instruction Manual which said to just put the disc in and it would install automatically, which it did not.  I have tried methods that other people have posted but always reached an error.

If you need to know any contents of any of the folders or details please just ask and I will edit this with that information.

Any and all help is greatly appreciated :)

---

### Post by nothingspecial on 2012-04-16
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2012-04-16
Please plug in your adapter and open a terminal and run this command:```
lsusb
```Find the line that is your Asus and post it here. Once we have the exact identity of your device, we'll be in a better position to proceed.

It may, or may not look something like this:> Bus 001 Device 002: ID 0b05:1786 ASUSTek Computer, Inc. What have you tried that reached an error?

---

### Post by kajong0007 on 2012-04-16
I am only a marginally more experienced ubuntu user. I have the same wireless adapter, and it worked out of box. I could not get the drivers on the CD to compile; I always reached some error (I'll paste it below).


```
$ make
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-17-generic'
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8180_93cx6.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_wx.o
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_wx.c: In function ‘r8192_wx_set_countrycode’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_wx.c:237:16: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_phy.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_rtl6052.o
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_rtl6052.c: In function ‘setAntennaDiff’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_rtl6052.c:355:23: warning: array subscript is above array bounds [-Warray-bounds]
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_rtl8225.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r819xU_cmdpkt.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_dm.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192SU_HWImg.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_firmware.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192S_Efuse.o
  CC [M]  /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.o
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_initiate’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:1607:35: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast [enabled by default]
include/linux/usb.h:1269:20: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_isr’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:2064:4: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast [enabled by default]
include/linux/usb.h:1269:20: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:2071:30: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192SU_MacConfigAfterFwDownload’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:7847:24: warning: comparison between ‘rtl819xUsb_loopback_e’ and ‘enum _RTL8192SUSB_LOOPBACK’ [-Wenum-compare]
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:7849:30: warning: comparison between ‘rtl819xUsb_loopback_e’ and ‘enum _RTL8192SUSB_LOOPBACK’ [-Wenum-compare]
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12325:5: error: ‘struct net_device’ has no member named ‘open’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12326:5: error: ‘struct net_device’ has no member named ‘stop’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12327:5: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12328:5: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12329:5: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12330:5: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12331:5: error: ‘struct net_device’ has no member named ‘get_stats’
/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.c:12332:6: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.0301.2010/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [all] Error 2
```

Here's the relevant bit of "lshw -C network":

```
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1.2
       logical name: wlan0
       serial: 54:04:a6:b9:cc:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=10.202.194.113 multicast=yes wireless=IEEE 802.11bg

```

My computer just started using the r8712u even though the proper driver is rtl8192su...

---

### Post by chili555 on 2012-04-16
> /home/jjo1/Desktop/Linux/rtl8192su_linux_2.4_2.6.0003.[COLOR="Red"]0301[/COLOR].[COLOR="Red"]2010[/COLOR]/You are not going to get this relative old-timer to compile in 3.0.0-xx.> even though the proper driver is rtl8192su.How so? Because SU is in the name of the device? That's fairly meaningless in Linux. However, if r8712u is working correctly, then it's obviously correct. Also:> $ modinfo rtl8192su
ERROR: modinfo: *could not find module rtl8192su*

---

### Post by kajong0007 on 2012-04-16
"Working correctly" may be going too far. I'm actually having a few issues staying connected to a network at my university that is encrypted with WPA-2 Enterprise. I don't know if this is the driver's fault or the network's. Every once in a while, my computer disconnects from the network then supposedly attempts to connect again. I am able to successfully reconnect if I just wait a while and try again (e.g. I randomly disconnected earlier, ate lunch, then connected again).

[edit]
Oh, and by "proper driver" I mean the one I thought I was trying to compile.

---

### Post by chili555 on 2012-04-16
Everyone suspects and wants to replace the driver. However, the issue could easily be wpa_supplicant or Network Manager. It might also be the interaction between some or all of them! Are there any clues here, right *exactly* after it disconnects?```
sudo cat /var/log/syslog | tail -n20
```

---

### Post by kajong0007 on 2012-04-16
```
Apr 16 14:25:50 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: Associated with 00:0b:85:77:25:dd
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: WPA: Failed to get master session key from EAPOL state machines
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: WPA: Key handshake aborted
Apr 16 14:25:50 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-STARTED EAP authentication started
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=13 -> NAK
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='/C=SE/O=AddTrust AB/OU=AddTrust External TTP Network/CN=AddTrust External CA Root'
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='/C=SE/O=AddTrust AB/OU=AddTrust External TTP Network/CN=AddTrust External CA Root'
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/C=US/O=Internet2/OU=InCommon/CN=InCommon Server CA'
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/C=US/postalCode=*Omitted stuff*'
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: EAP-MSCHAPV2: Authentication succeeded
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Apr 16 14:25:50 Dashy kernel: [93107.314298] r8712u: r871x_wx_set_pmkid: BSSID exists in the PMKList.
Apr 16 14:25:50 Dashy wpa_supplicant[1186]: CTRL-EVENT-DISCONNECTED bssid=00:0b:85:77:25:dd reason=0
Apr 16 14:25:50 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Apr 16 14:25:50 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```

It tried connecting for a bit. At that point, it asked me for my log-in information (which is still correct). I'll see what else I can procure...

When successful:


```
Apr 16 14:28:47 Dashy dhclient: DHCPACK of 10.106.194.103 from 1.1.1.1
Apr 16 14:28:47 Dashy dhclient: bound to 10.106.194.103 -- renewal in 705 seconds.
Apr 16 14:28:47 Dashy NetworkManager[885]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 16 14:28:47 Dashy NetworkManager[885]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 16 14:28:47 Dashy NetworkManager[885]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   address 10.106.194.103
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   prefix 25 (255.255.255.128)
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   gateway 10.106.194.1
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   nameserver '10.128.92.32'
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   nameserver '10.129.92.32'
Apr 16 14:28:47 Dashy NetworkManager[885]: <info>   domain name '*omitted*'
Apr 16 14:28:47 Dashy NetworkManager[885]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 16 14:28:47 Dashy avahi-daemon[883]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.106.194.103.
Apr 16 14:28:47 Dashy avahi-daemon[883]: New relevant interface wlan0.IPv4 for mDNS.
Apr 16 14:28:47 Dashy avahi-daemon[883]: Registering new address record for 10.106.194.103 on wlan0.IPv4.
Apr 16 14:28:48 Dashy NetworkManager[885]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 16 14:28:49 Dashy NetworkManager[885]: <info> Policy set '*network name*' (wlan0) as default for IPv4 routing and DNS.
Apr 16 14:28:49 Dashy NetworkManager[885]: <info> Activation (wlan0) successful, device activated.
Apr 16 14:28:49 Dashy NetworkManager[885]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 16 14:28:49 Dashy NetworkManager[885]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
```

---

### Post by chili555 on 2012-04-16
> WPA: Failed to get master session key from EAPOL state machines...Googling...

---

### Post by kajong0007 on 2012-04-16
It just had trouble connecting to the unsecured network for some odd reason:


```
Apr 16 15:59:51 Dashy wpa_supplicant[1186]: Trying to associate with 00:0b:85:77:1d:ee (SSID='*unsecured network*' freq=2462 MHz)
Apr 16 15:59:51 Dashy wpa_supplicant[1186]: Association request to the driver failed
Apr 16 15:59:51 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 16 15:59:56 Dashy wpa_supplicant[1186]: Authentication with 00:0b:85:77:1d:ee timed out.
Apr 16 15:59:56 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: associating -> scanning
Apr 16 16:00:01 Dashy wpa_supplicant[1186]: Trying to associate with 00:0b:85:77:1d:ee (SSID='*unsecured network name here*' freq=2462 MHz)
Apr 16 16:00:01 Dashy wpa_supplicant[1186]: Association request to the driver failed
Apr 16 16:00:01 Dashy NetworkManager[885]: <info> (wlan0): supplicant interface state: scanning -> associating
```

---

### Post by Cr1scoD1sco on 2012-04-16
> **chili555 said:**
> Please plug in your adapter and open a terminal and run this command:```
lsusb
```

Do you mean copying the CD or adapter to the terminal than then typing that?  I plugged in the adapter and typed '1susb' into it but it came back with this:```
No command '1susb' found, did you mean:
Command 'lsusb' from package 'usbutils' (main)
1susb: command not found
```

Scratch that. I got it to work.  heres what it came back with:```
Bus 003 Device 002: ID 15d9:0a4c Trust International B.V.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 0b05:1786 ASUSTek Computer, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0root hub
```

---

### Post by chili555 on 2012-04-16
Sorry, the fonts are a bit hard to read. It is not ONEsusb; it is ELsusb, as in **L**i**S**t all the **USB** devices.

---

### Post by Cr1scoD1sco on 2012-04-17
Do you have any idea on what I should do next?

---

### Post by chili555 on 2012-04-17
Sorry about that! You got swamped by all the others barging in. Your device is claimed by r8712u in 11.10. I don't know about 11.04 because I don't have it or the live CD anywhere. We'll have to depend on your findings. First, do you have r8712u? Find out with:```
modinfo r8712u | grep 1786
```If you don't have the driver, there will be a 'not found' error. If you have the driver and your device is not recognized, the command will just come back to a new line. If it is recognized, you'll get this:> $ modinfo r8712u | grep 1786
alias:          usb:v0B05p[COLOR="Red"]1786[/COLOR]d*dc*dsc*dp*ic*isc*ip*Please run the command and let's see what it returns.

---

### Post by Cr1scoD1sco on 2012-04-17
> **chili555 said:**
> Sorry about that! You got swamped by all the others barging in. Your device is claimed by r8712u in 11.10. I don't know about 11.04 because I don't have it or the live CD anywhere. We'll have to depend on your findings. First, do you have r8712u? Find out with:```
modinfo r8712u | grep 1786
```If you don't have the driver, there will be a 'not found' error. If you have the driver and your device is not recognized, the command will just come back to a new line. If it is recognized, you'll get this:Please run the command and let's see what it returns.
Ha it's no problem. Thank you for your continued responses. And I got that exact message back.

---

### Post by chili555 on 2012-04-17
> And I got that exact message back.Which? I gave you three possibilities:

#module not found; or

#module found but doesn't cover your device; or

#```
modinfo r8712u | grep 1786
alias: usb:v0B05p[COLOR="Red"]1786[/COLOR]d*dc*dsc*dp*ic*isc*ip* 
```Which was it?

---

### Post by Cr1scoD1sco on 2012-04-17
> **chili555 said:**
> Which? I gave you three possibilities:

#module not found; or

#module found but doesn't cover your device; or

#```
modinfo r8712u | grep 1786
alias: usb:v0B05p[COLOR="Red"]1786[/COLOR]d*dc*dsc*dp*ic*isc*ip* 
```Which was it?

The third one, my bad.

---

### Post by chili555 on 2012-04-17
OK! Let's see:```
sudo modprobe r8712u
dmesg | grep 8712
rfkill list all
```

---

### Post by Cr1scoD1sco on 2012-04-17
> **chili555 said:**
> ```
sudo modprobe r8712u
dmesg | grep 8712
rfkill list all
```

Assuming you wanted me to press enter each time you started a new line, I got a few lines of response after typing in 'dmesg | grep 8712' but nothing more after 'rfkill list all'

It's quite a bit of code.  Would you like me to post all of it?

---

### Post by chili555 on 2012-04-17
> It's quite a bit of code. Would you like me to post all of it?Yes, unless the 8712 is in the timestamp, like this:```
  [69382.[COLOR="Red"]8712[/COLOR]93] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
```I want to see the reason your driver doesn't drive your wireless card.

---

### Post by Cr1scoD1sco on 2012-04-18
> **chili555 said:**
> Yes, unless the 8712 is in the timestamp, like this:```
  [69382.[COLOR=Red]8712[/COLOR]93] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
```I want to see the reason your driver doesn't drive your wireless card.

Heres what I got. (I'm not exactly sure about the placement of the spaces.)

```
 [    21.294261] r[COLOR=Red]8712[COLOR=Black]u: module is from the staging directory, the quality is unknown, you have been warned.
[    22.052418] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u:[/COLOR][/COLOR] DriverVersion: v7_0.20100831
[    22.052459] r[COLOR=Red]8712[COLOR=Black]u: register rtl[/COLOR][/COLOR][COLOR=Red]8712[COLOR=Black]_netdev_ops to netdev_ops
[    22.052465] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u: USB_SPEED_HIGH with 4 endpoints
[    22.068290] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u: Boot from EFUSE: Autoload OK
[    24.056914] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u: CustomerID = 0x0010
[    24.056922] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u:[/COLOR][/COLOR] MAC Address from efuse = 54:04:a6:e0:28:cd
[    24.059772] usbcore: registered new interface driver r[COLOR=Red]8712[COLOR=Black]u
[    25.048522] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u:  1 RCR=0x153f00e
[    25.049266] [/COLOR][/COLOR]r[COLOR=Red]8712[COLOR=Black]u:[/COLOR][/COLOR]  2 RCR=0x553f003
```

I may have made one or two mistakes but I'm pretty sure this is right.

---

### Post by chili555 on 2012-04-19
How about this one?```
rfkill list all
```Frankly, it all looks quite good. I see no errors or warnings. Was a wireless interface created?```
iwconfig
```Are there any other clues?```
dmesg | grep wlan
```This is my favorite kind of problem; everything looks perfect except it doesn't work!

---

