---
title: "WPA authenticated once, but never again"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by lucasjung on 2011-08-29
I'm setting up an HTPC using xubuntu with XBMC.  I've been using various flavors of Linux since the late '90s, but this is my first time using any flavor of ubuntu.

I installed xubuntu this afternoon and experienced absolutely no problems during installation.  After booting the first time, the little networkmanager icon in the upper-right corner of the screen popped up a message stating that networks were available.  I clicked on it, selected the SSID for my home network, and then a screen popped up asking for my key.  I entered my WPA2 passphrase, and it connected immediately without a hitch.  I was able to browse the web, etc., with no problem.

I then turned my attention to some issues with my screen resolution, and restarted the computer as part of the troubleshooting process.  After rebooting, I could see that networkmanager was trying to automatically connect to my home network, but after a few minutes of trying it popped up the authentication window and asked me for my key again.  I checked "show password," and the correct passphrase was already in there.  I clicked "Connect," and it went back to trying, only to pop up the authentication window again after a few minutes.  I tried re-entering the passphrase, but it just kept doing the same thing over and over again.

I deleted the connection from networkmanager, shut down the computer, shut down every other computer on my wireless network, and rebooted the wireless router.  After rebooting the router I turned the HTPC back on.  I got the "wireless connections are available" popup again, and ended up going through the same routine where it keeps asking for my key even though it already has the correct passphrase.  Everything else on my wireless network continues to connect just fine, even if I delete the stored passphrase and re-enter it manually.

My router is a D-Link DIR-825 running the factory firmware.

I'm running Xubuntu 10.04.2 LTS on:
CPU: Intel Core i3-2100T
Motherboard: Intel DH67GD
RAM: 16GB
Swap: 20GB on an Intel 320-series SSD
Wifi Card: Linksys WMP600N (RaLink RT 2860 chipset)
EDIT: Interestingly, lspci lists it as an RT2800 even though I know for a fact it's a 2860.  However, lsmod shows that the correct module is being used (rt2860sta).
Forgot to mention my kernel version is 2.6.32-28-generic x86_64.  My understanding is that the module for this chipset (rt2860) is no longer in staging as of kernel 3.0.

I built a wpa_supplicant.conf and tried connecting manually, but I don't have dhcpcd installed so I couldn't finish making the connection.

---

### Post by wildmanne39 on 2011-08-29
Hi, please run these commands in the terminal and post the results here:
```
lsusb
```
```
sudo lshw -C network 
```
```
lspci -nn | grep 0280
```
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
Thank you

---

### Post by lucasjung on 2011-08-29
I think that I must have been editing at the same time that you were posting, because a lot of the info you asked for is in my edit.

Unfortunately, the HTPC doesn't have a wired network connection, so the only way for me to post the full results of those commands would be to transpose them by hand.  If there was something that was truly relevant I would do so, but most of it isn't.  I'll give you a summary of the important parts:

lspci & rmmod: see the edit to my original post

nm-tool & iwlist scan: yes, my home wifi network is showing up, with plenty of signal/noise.  That was never in doubt, because even networkmanager is seeing it.

iwconfig & lshw -C network: In general, the hardware and drivers all look correct.  If there's something in particular you want from this, let me know what field(s) you want and I'll write it down and copy it over.  Frankly, I don't think the issue is here.  I'm pretty confident that this is an issue with whatever piece of software is handling WPA2 authentication (I'm not super familiar with the inner workings of networkmanager).

rfkill list all:
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```

(This surprised me, because the only bluetooth device I have is the USB dongle for my logitech keyboard, and I was of the understanding that it didn't share it's bluetooth functionality with the system.)

---

### Post by wildmanne39 on 2011-08-29
Hi, you can copy and paste the results to a flash drive then post them here.

I am pretty good at this but I am not an expert and there is a lot of information that you might think is not important but most of it is and with out seeing everything that I asked for I am not able to help you.

This is just the first step there may be more that I will need to figure this out.
Thank you.

---

### Post by lucasjung on 2011-08-30
> **wildmanne39 said:**
> Hi, you can copy and paste the results to a flash drive then post them here.

This actually made me laugh, initially.  I haven't used a flash drive in years: my work doesn't allow them, and I don't need them at home because I have a fileserver that all of my computers connect to.  If I need to share files with others, I use my fileserver, dropbox, or email (depending on how well I know them).  I'm just so out of the habit of using a flash drive that it never even occurred to me, which is why I laughed.  I actually *did* try burning a CD before posting earlier, but I couldn't find any CD-burning software on the HTPC (another thing I would have installed eventually, if I hadn't lost wifi).

I dug around the house for about an hour and finally found an old flash drive in back of a drawer in the office, fortunately.  Otherwise I might have had to go out and buy one tomorrow.  So, here's all of the stuff you asked for.  I tried to run these while networkmanager was in the process of trying to connect, on the off chance that it might show something of value.  I also sanitized everything by deleting all of the wireless networks other than my own from the outputs, changing the SSID of my network to "SSID," and changing all HW addresses to "XX:XX:XX:XX:XX:XX."

lsusb:
```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 17f6:0802 Unicomp, Inc 
Bus 002 Device 005: ID 1241:e000 Belkin 
Bus 002 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw:
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fe700000-fe71ffff memory:fe728000-fe728fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe600000-fe60ffff

```

lspci:
```
02:00.0 Network controller: RaLink RT2800 802.11n PCI
```

nm-tool:
```
NetworkManager Tool

State: connecting

- Device: wlan0  [Auto SSID] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             connecting (configuring)
  Default:           no
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SSID:            Infra, XX:XX:XX:XX:XX:XX, Freq 2462 MHz, Rate 18 Mb/s, Strength 81 WPA WPA2

```

iwconfig:
```
lo        no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=82/100  Signal level:-64 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
*Note: the HW address listed for the access point in the wlan0 entry above, is the HW address for my wireless router.*

rfkill:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

iwlist:
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 04 - Address: XX:XX:XX:XX:XX:XX
                    Protocol:802.11b/g/n
                    ESSID:"SSID"
                    Mode:Managed
                    Channel:11
                    Quality:65/100  Signal level:-64 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2011-08-30
Hi, we are making progress.
Please run these commands just copy and paste then so no information is missing. I am trying to make sure you are using the right driver but I only got part of the information from this command.
```
lspci -nn | grep 0280
```
also please post the results of these commands.
```
lsmod | grep rt2
```
```
dmesg | grep wlan0
```
```
dmesg | grep rt2
```
I am trying to keep what you have to post to a small amount.

Also you should change your router encryption to wpa2 only and see if that helps, a lot of times mixed mode does not work well.
Thank you

---

### Post by lucasjung on 2011-08-30
lspci:
```
02:00.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
```

lsmod:
```
rt2860sta             542482  1
```

dmesg:
```
[    2.809720] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    2.833649] rt2860 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
```
*Note: No output from grep | wlan0 *

> **wildmanne39 said:**
> Also you should change your router encryption to wpa2 only and see if that helps, a lot of times mixed mode does not work well.
This seems to have fixed it.  Thank you!  After making this change, I turned the HTPC back on and it connected immediately.  I rebooted a few times and got the same results.  Now I'm going to upgrade all of my packages and hope it doesn't break again.

---

### Post by wildmanne39 on 2011-08-30
Hi, that is great if it continues to work would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by lucasjung on 2011-08-30
It kept working after an upgrade and a few reboots, so I think it's good to go.  Thank you very much for your excellent help!

---

### Post by wildmanne39 on 2011-08-30
Hi, your welcome! Glad I could help.

---

