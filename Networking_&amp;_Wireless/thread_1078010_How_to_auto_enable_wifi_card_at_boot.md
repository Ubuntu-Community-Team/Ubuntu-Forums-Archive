---
title: "How to auto enable wifi card at boot"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by iyepb0 on 2009-02-22
Hello everyone,

I would like to ask.
How to auto enable my wifi card at boot?
In Ubuntu 8.10 i have to remove, insert then restart the nerworking before i can use my wifi card on my notebook.
My wifi card is Intel 3945.
I believe there was an init script that i might need to edit, but which one and what to write?

Thank you all

Regard,
Iyepb0
Open Source Your Mind

---

### Post by pytheas22 on 2009-02-23
Try running this command once:
```

echo iwl3945 | sudo tee -a /etc/modules
```

If it's just a matter of forcing the iwl3945 module to be inserted, this should take care of it.  If not, please post the output of:
```

lshw -C Network
dmesg | grep -e wlan -e iwl
```

---

### Post by iyepb0 on 2009-02-23
This is the output for the command:
lshw -C Network

>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:c1:7d:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=202.46.5.109 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:7e:4c:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:be:f1:a5:1b:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


This is for:
dmesg | grep -e wlan -e iwl

> [   13.171631] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.171635] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   13.171759] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.171773] iwl3945 0000:07:00.0: setting latency timer to 64
[   13.171795] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   13.234424] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.236629] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.896626] iwl3945 0000:07:00.0: PCI INT A disabled
[   28.149229] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   28.149373] iwl3945 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   28.149632] firmware: requesting iwlwifi-3945-1.ucode
[   29.080697] iwl3945: Radio disabled by HW RF Kill switch
[   29.080789] iwl3945 0000:07:00.0: PCI INT A disabled
[   29.095420] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.095568] iwl3945 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   29.095839] iwl3945: Radio disabled by HW RF Kill switch
[   29.095933] iwl3945 0000:07:00.0: PCI INT A disabled


Thank you and i'll try you way.

---

### Post by iyepb0 on 2009-02-23
I'm sorry but your solution is not working.
My wifi card still disable after boot / login.

Is there otherway?

Thanks

---

### Post by pytheas22 on 2009-02-23
According to the output of dmesg, the reason your card is not working is that it's turned off:
```

[ 29.080697] **iwl3945: Radio disabled by HW RF Kill switch**
[ 29.080789] iwl3945 0000:07:00.0: PCI INT A disabled
[ 29.095420] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 29.095568] iwl3945 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 29.095839] **iwl3945: Radio disabled by HW RF Kill switch**
[ 29.095933] iwl3945 0000:07:00.0: PCI INT A disabled 
```

There should be a switch that you use to turn the wireless card on--either a physical button on your computer, or a software switch, like function+F2.  Does toggling this turn your wireless card on?

There may also be an option in your BIOS where you can force the wireless to be always on (although this can waste some energy if you run on battery a lot and don't always need the wireless); take a look there.

---

### Post by iyepb0 on 2009-02-24
Actually the HW switch is turned ON.

Now, i found some cases for my card.

1. If I switched ON the HW switch before i boot Intrepid Ibex (login to X). Then the my wifi card work normally. It scan for any AP and can connect them. But if I switched OFF the HW switch then switched it ON again, the card doesnt work anymore.

2. If I switched OFF the HW switch before i boot Intrepid Ibex. Then switched ON the HW switch after enter X, the card wont work also.

Why is it happening in Intrepid Ibex?
Cause in Hardy Heron I dont have this issue.

Please share your knowledge with me :)
Thanks You.

Regard,
iyepb0
Open Source Your Mind

---

### Post by pytheas22 on 2009-02-24
I think this [bug report]("http://bugs.gentoo.org/show_bug.cgi?id=232043") (for Gentoo) describes the same issue.  According to the people there, a solution would be to run this command:
```

echo 'options iwl3945 disable_hw_scan=1' | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Does the problem still occur?

---

### Post by iyepb0 on 2009-02-24
I'm sorry, but the problem still occur.
Can you explain me what is the matter with the module or perhaps the card?

Thanks

---

### Post by pytheas22 on 2009-02-24
Sorry that didn't work.  I don't really know what's wrong myself--I'm just reading stuff from Google--but I think there's just some bug in the iwl3945 driver, or in its firmware.

What happens if you boot to Ubuntu, then remove the driver by typing:
```

sudo rmmod iwl3945
```

and then insert it with the special option by typing:
```

sudo modprobe iwl3945 disable_hw_scan=1
```

Can you turn the wireless card on and off now multiple times without losing the connection?  If so, we could write a script to apply this workaround automatically.

Also, someone suggests that it may help to power down your computer completely, unplug the power cord (and remove the battery if it's a laptop), then hold the power button in for thirty seconds.  This will force your wireless card to reset, which will clear out some misconfigurations that may be responsible for the issue you're experiencing.  I would give this a try as well.

---

### Post by iyepb0 on 2009-02-25
Nope, still not working... What a pitty on me :(
Should i switch back to Hardy Heron?
Absolutely HH and II has different Kernel version.

Let me try the last one...

Best Regards,
iyepb0

---

### Post by pytheas22 on 2009-02-25
Sorry that didn't work either.  At this point, I'm afraid I'm out of ideas.  The only other suggestion I can make is to check BIOS to see if there's an option for forcing the wireless to be always on--but that might not be an acceptable solution for you.

You could go back to Hardy if this is a big enough problem, or you could just stick it out with Intrepid for two more months, and hope this is fixed when Jaunty comes out in April.

---

### Post by iyepb0 on 2009-02-26
Thank you so much for your assist phyteas22.
Perhaps i should get myself remember to switch on my wifi card before booting.

Regards,
iyepb0

---

### Post by mwhite1206 on 2009-03-11
I'm having a similar problem, I'm on an Asus F3L with an Atheros 242x wireless card. I've managed to get Ubuntu to recognise the card exists (thanks to [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)), but the card comes up as being turned off:

marc@juju:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My laptop has two switches for wireless - a 'master' hard switch at the front, and a software key that (in Windows, at least) lets you toggle between wlan only, Bluetooth only, or wlan and Bluetooth. The hard switch is on, but the software switch doesn't work under Ubuntu. Is there someway I can turn the card on through the terminal, or get it to turn on automatically at startup?

---

### Post by pytheas22 on 2009-03-11
mwhite1206: please try toggling the software switch a few times, then post the output of:
```

dmesg | grep -i -e radio -e wlan -e ath
```

Also, are you positive that the card can't see networks (using the 'sudo iwlist scan' command) after you toggle the software switch?  In some cases, the wireless light might not come on, but the card still works, so please give this a try.

---

### Post by mwhite1206 on 2009-03-11
As requested:
marc@juju:~$ dmesg | grep -i -e radio -e wlan -e ath
[   15.037419] wlan0: ethernet device 00:15:af:7e:3a:a0 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   15.042947] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
marc@juju:~$ dmesg | grep -i -e radio -e wlan -e ath
[   15.037419] wlan0: ethernet device 00:15:af:7e:3a:a0 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   15.042947] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

I've tried the software switch a few times, and it doesn't change the output of the following two commands:
marc@juju:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

marc@juju:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm reasonably confident it's the software switch that isn't working, as it also controls Bluetooth on/off under Windows, and does no such thing under Ubuntu (I need to turn it on and off manually through the System menu.)

---

### Post by mwhite1206 on 2009-03-11
New information: following the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros), I found that "ath5k" had been blacklisted in /etc/modprobe.d/madwifi, so I commented out that line. Now, when i run sudo iwscan list, i get:

marc@juju:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:1E:97:68:E0
                    ESSID:"ANU-Access"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:16:01:AF:6B:0C
                    ESSID:"moomintroll-at-work"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

However, no wireless networks show up in the Wicd Manager, and iwconfig says the card is still off:
marc@juju:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So the card obviously works, just Ubuntu doesn't want to let me turn the damn thing on...

---

### Post by pytheas22 on 2009-03-12
Yes, ath5k is a better choice for this card than ndiswrapper, and obviously ath5k allows you to see networks, since 'iwlist scan' returned something.

The reason that wicd doesn't list your networks with ath5k enabled is probably because you have the wrong interface name specified--wicd is not good about auto-detecting these things.  Click the 'Preferences' button in wicd and make sure that 'wlan0' is specified as the interface name, and see if that makes a difference.  Please let us know.

---

### Post by mwhite1206 on 2009-03-12
You're right, wicd didn't have a wireless interface specified, so I added wlan0. Unfortunately, it didn't help, wicd still can't see wireless networks, and iwconfig still states the wireless card if off. Could the setting of that thing above the interfaces, WPA supplicant driver, have anything to do with it?

---

### Post by pytheas22 on 2009-03-12
The WPA supplicant driver shouldn't affect wicd, but it's possible that something else is misconfigured.  Could you post a screenshot of the Preferences window?

You could also try getting a connection manually.  These commands would connect you to the "ANU-Access" network, provided it allows you to join (i.e., no MAC filtering) and serves dynamic IP addresses:
```

sudo iwconfig wlan0 mode managed essid "ANU-Access" channel 1
sudo dhclient wlan0
```

If that works, at least you know that your card itself is working, and that it's just a matter of fixing wicd.

Another thing to consider would be uninstalling wicd and switching back to Network Manager, the default connection manager in Ubuntu.  You can install NM by typing:
```

sudo apt-get install network-manager-gnome
```
> 
iwconfig still states the wireless card if off

Just to be clear, none of the iwconfig outputs that you've posted say the card is "turned off" in the sense that its radio is not on.  They say that it's not associated, but that's always what iwconfig says before you connect to a network, whether there's a problem or not.  If you want to make sure the radio is on, run the command 'lshw -C Network'.  If the radio is off, that command will give output similar to this:

```
  *-network:0 **DISABLED**    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wmaster0
       version: 01
       serial: 00:19:e0:67:8a:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

The 'DISABLED' bit means that the radio is turned off.

---

### Post by mwhite1206 on 2009-03-12
> **mwhite1206 said:**
> You're right, wicd didn't have a wireless interface specified, so I added wlan0. Unfortunately, it didn't help, wicd still can't see wireless networks, and iwconfig still states the wireless card if off. Could the setting of that thing above the interfaces, WPA supplicant driver, have anything to do with it?

Hold the phone, turns out that adding wlan0 to wicd DID actually work, I can now scan for & connect to wireless networks - for some reason, it wanted a couple of system restarts before it decided to play along. Thanks for the help!

---

### Post by pytheas22 on 2009-03-13
Strange that the change in wicd didn't take effect immediately, but I'm glad this is cleared up :)

---

