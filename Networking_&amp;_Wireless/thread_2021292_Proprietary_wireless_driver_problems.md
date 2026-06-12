---
title: "Proprietary wireless driver problems"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by Peripetilja on 2012-07-09
I'm trying to install Ubuntu 12.04 on a HP Pavilion dm1 from usb.
While connecting to my wireless modem the proprietary drivers warning showed up. I went to System Settings->Additional Drivers and what every site I read told me to do next is to click the "Activate button" which I can't see because the green light is on and "This driver is activated and currently in use" is on the buttons place. I can see he's trying to connect, but failed every time. It is a Broadcom STA wireless driver.

---

### Post by chili555 on 2012-07-09
Perhaps you don't really need the STA driver, despite what 'Additional Drivers' says. Let's see more information about your device. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Peripetilja on 2012-07-09
After typing the code in terminal:```
 Network controller [0280] Broadcom Corporation BCM 4313 802.11b/g/n Wireless LAN Controller [14e4:4727]
```

Additional information: 
1)The name of the warning mentioned in the first post is called "restricted drivers available"
2) From time to time he connects to my wireless connection, but dissconets a minute later and stays dc-ed for most of the time
3) I still haven't installed ubuntu on my netbook, I'm running ubuntu via BIOS USB boot
4) When I turn my netbook on in win7 I get the warning " A network cable is not properly plugged in or may be broken" althought he connects normally and the connection is stable (I read it is normal for some laptops to do so after being in BIOS, don't know if it is relevant to my connection problem in ubuntu)

Ty for your reply.

---

### Post by chili555 on 2012-07-09
The STA driver is indeed correct for your device. Let's see if any conflicting drivers are loaded:```
lsmod | grep -e bcma -e brcmsmac -e b43 -e wl
```Thanks.

---

### Post by Peripetilja on 2012-07-09
```
bcma         25651   0
brcmsmac     540875  0
mac80211     436455  1 brcmsmac
brcmutil     14675   1 brcmsmac
cfg80211     178679  2 brcmsmac,mac80211
crc8         12781   1 brcmsmac
cordic       12487   1 brcmsmac
```

---

### Post by Dirkzobb on 2012-07-09
Hi, I'm having the same problem. Pasting these codes into my system give
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ lspci -nn | grep 0280
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ lsmod | grep -e bcma -e brcmsmac -e b43 -e wl
wl                   2646601  0 
lib80211               14040  1 wl

System settings says STA driver is installed and running. No wireless action .... connected via ethernet. My laptop has a wifi switch that lights up blue when running xp. Been trying to get this to work for days and it's driving me crazy

---

### Post by chili555 on 2012-07-09
> **Peripetilja said:**
> ```
bcma         25651   0
brcmsmac     540875  0
mac80211     436455  1 brcmsmac
brcmutil     14675   1 brcmsmac
cfg80211     178679  2 brcmsmac,mac80211
crc8         12781   1 brcmsmac
cordic       12487   1 brcmsmac
```Please pardon me, I mis-spoke when I said:> The STA driver is indeed correct for your device. In fact, brcmsmac is correct. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Afterwards, let's do some diagnostics:```
dmesg | grep wlan
rfkill list all
```Thanks.

---

### Post by chili555 on 2012-07-09
> **Dirkzobb said:**
> Hi, I'm having the same problem. Pasting these codes into my system give
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ lspci -nn | grep 0280
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ lsmod | grep -e bcma -e brcmsmac -e b43 -e wl
wl                   2646601  0 
lib80211               14040  1 wl

System settings says STA driver is installed and running. No wireless action .... connected via ethernet. My laptop has a wifi switch that lights up blue when running xp. Been trying to get this to work for days and it's driving me crazyYours is a whole different case. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

---

### Post by Dirkzobb on 2012-07-09
Hi,
This is what I've got:
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

What next?

---

### Post by Dirkzobb on 2012-07-09
Hi, Pasted in the stuff, rebooted and this is what I get now:
[sudo] password for dirkzobb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Then tried the auto remove and got this:
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by chili555 on 2012-07-09
> $ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), [COLOR="Red"]are you root?[/COLOR]Please try:```
[COLOR="Red"]sudo[/COLOR] apt-get autoremove
```Then go on to the firmware part.

---

### Post by Peripetilja on 2012-07-09
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Gave me this
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package bcmwl-kernel-source is not installed,so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

After typing this
```
dmesg | grep wlan
rfkill list all
```
I got
```
[31.563886] ADDRCONF(NETDEV_UP):wlan0: link is not ready
[31.565928] ADDRCONF(NETDEV_UP):wlan0: link is not ready
```

and
```
0: hci0:Bluetooth
Soft blocked: no
Hard blocked: no
1: hp-wifi:Wireless LAN
Soft blocked: no
Hard blocked: no
2: hp-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

```

---

### Post by chili555 on 2012-07-09
Are those readings *after* you did:> Reboot and let us have your report.??

---

### Post by Dirkzobb on 2012-07-09
Hi,
Done that and this is where we're at:
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms fakeroot patch
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
After this operation, 890 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167868 files and directories currently installed.)
Removing dkms ...
Removing fakeroot ...
update-alternatives: using /usr/bin/fakeroot-tcp to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Removing patch ...
Processing triggers for man-db ...

What next?

---

### Post by chili555 on 2012-07-09
> **Dirkzobb said:**
> Hi,
Done that and this is where we're at:

What next?Please confirm you *did* do the firmware part.```
dmesg | grep -e wlan -e b43
ls /lib/firmware/b43

```Thanks.

---

### Post by Peripetilja on 2012-07-09
> **chili555 said:**
> Are those readings *after* you did:
> Reboot and let us have your report.

??

Was this meant for me?
The same thing comes up after rebooting

---

### Post by chili555 on 2012-07-09
> **Peripetilja said:**
> Was this meant for me?
The same thing comes up after rebootingThat's the price I pay for trying to juggle two different cases in one thread. Sorry. 

Peri, your case is brcmsmac. Please let me see:```
sudo iwlist wlan0 scan
```

---

### Post by Peripetilja on 2012-07-09
Nah, it's not your fault, Dirkzobb invaded my thread ;)
What does "brcmsmac" stand for?

```
sudo iwlist wlan0 scan
```
Gave me this
```
wlan0        Scan completed:
             Cell 01-Adress:00:1D:68:FB:FE:18
             Channel:1
             Frequency:2.412 GHz (Channel:1)
             Quality=36/70 Signal level=-74 dBm
             Encryption key:on
             ESSID:"/*censured(name of my network)*/"
             Bit Rates:1Mb/s; 2Mb/s;5.5Mb/s; 11 Mb/s; 18Mb/s
                       24Mb/s; 36Mb/s; 54 Mb/s
             Bit Rates:6Mb/s; 9Mb/s;12Mb/s; 48Mb/s
             Mode:Master
             Extra:tsf=000000ef2b4ae376
             Extra: Last beacon: 784ms ago
             IE:Unknown:0007666C656B696361
             IE:Unknown:010882848B962430486C
             IE:Unknown:030101
             IE:Unknown:2A0100
             IE:Unknown:2F0100
             IE:Unknown:32040C121860
             IE:Unknown:DD060010180200F0
              IE:Unknown:DD180050F2020101880003A400042435E0062322F00
```

---

### Post by chili555 on 2012-07-09
> What does "brcmsmac" stand for?It's just the next name in the long line of Broadcom drivers. I'm not aware that it stands for anything in particular aside from the *brcm* part that seems to refer to Broadcom.

Your signal strength is a bit low:> Quality=[COLOR="Red"]36[/COLOR]/70However, if the driver and hardware can scan it, Network Manager ought to list it as an available network. Does it? Does it try to connect?

---

### Post by Peripetilja on 2012-07-09
It is quite silly that the signal is so low because the modem is right next to my laptop..
The manager can see my network, tries to connect and succeeds 1 out of 100 tries and lasts about 1/2 minutes

---

### Post by Dirkzobb on 2012-07-10
Hi Peripetilja,

Apologies for hijacking your thread and causing confusion. I'm new to this game....Hope you got/get your wireless prob sorted.

---

### Post by Peripetilja on 2012-07-10
> **Dirkzobb said:**
> Hi Peripetilja,

Apologies for hijacking your thread and causing confusion. I'm new to this game....Hope you got/get your wireless prob sorted.

I don't mind, I'm sure you're desperate as I am to get this thing working :)
Good luck to you too, unfortunately I'm still offline

---

### Post by chili555 on 2012-07-10
@Peripetilja--

Let's see what's going on under the hood. Please run and post:```
dmesg | grep -e brcm -e wlan
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```We are trying to capture what wireless is doing, so, for the second command, please be sure the ethernet is disconnected.

---

### Post by chili555 on 2012-07-10
@Dirkzobb--

What was the result from post #15, please?

---

### Post by Dirkzobb on 2012-07-10
Hi,

Seemed to have caused some confusion yesterday - sorry. I've got as far as the firmware part and here's the result so far: All assistance appreciated.
  	 	 	 	 	 	   Following reboot this is what I have:
 

 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ sudo apt-get remove --purge bcmwl-kernel-source 
 [sudo] password for dirkzobb:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package bcmwl-kernel-source is not installed, so not removed 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ sudo apt-get install linux-firmware-nonfree 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 linux-firmware-nonfree is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 

 On to the next including firmware
 

 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ sudo apt-get install linux-firmware-nonfree 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 linux-firmware-nonfree is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ sudo apt-get autoremove 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ dmesg | grep -e wlan -e b43 
 [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=1d0c6019-b430-4c36-8912-d6e0ef1f7067 ro quiet splash vt.handoff=7 
 [    1.362557] b43-pci-bridge 0000:30:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
 [    1.362570] b43-pci-bridge 0000:30:00.0: setting latency timer to 64 
 [   22.132479] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
 [   22.267141] Registered led device: b43-phy0::tx 
 [   22.267205] Registered led device: b43-phy0::rx 
 [   22.267268] Registered led device: b43-phy0::radio 
 [   23.889635] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07) 
 [   24.066778] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   24.069995] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   24.080091] b43-phy0: Radio hardware status changed to DISABLED 
 dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ ls /lib/firmware/b43 
 a0g0bsinitvals5.fw     lcn400initvals33.fw    sslpn1bsinitvals20.fw 
 a0g0bsinitvals9.fw     lp0bsinitvals13.fw     sslpn1bsinitvals27.fw 
 a0g0initvals5.fw       lp0bsinitvals14.fw     sslpn1initvals20.fw 
 a0g0initvals9.fw       lp0bsinitvals15.fw     sslpn1initvals27.fw 
 a0g1bsinitvals13.fw    lp0bsinitvals16.fw     sslpn2bsinitvals19.fw 
 a0g1bsinitvals5.fw     lp0initvals13.fw       sslpn2initvals19.fw 
 a0g1bsinitvals9.fw     lp0initvals14.fw       sslpn3bsinitvals21.fw 
 a0g1initvals13.fw      lp0initvals15.fw       sslpn3initvals21.fw 
 a0g1initvals5.fw       lp0initvals16.fw       sslpn4bsinitvals22.fw 
 a0g1initvals9.fw       lp1bsinitvals20.fw     sslpn4initvals22.fw 
 b0g0bsinitvals13.fw    lp1bsinitvals22.fw     ucode11.fw 
 b0g0bsinitvals5.fw     lp1initvals20.fw       ucode13.fw 
 b0g0bsinitvals9.fw     lp1initvals22.fw       ucode14.fw 
 b0g0initvals13.fw      lp2bsinitvals19.fw     ucode15.fw 
 b0g0initvals5.fw       lp2initvals19.fw       ucode16_lp.fw 
 b0g0initvals9.fw       n0absinitvals11.fw     ucode16_mimo.fw 
 ht0bsinitvals26.fw     n0bsinitvals11.fw      ucode16_sslpn.fw 
 ht0bsinitvals29.fw     n0bsinitvals16.fw      ucode16_sslpn_nobt.fw 
 ht0initvals26.fw       n0bsinitvals17.fw      ucode17_mimo.fw 
 ht0initvals29.fw       n0bsinitvals22.fw      ucode19_sslpn.fw 
 lcn0bsinitvals24.fw    n0bsinitvals24.fw      ucode19_sslpn_nobt.fw 
 lcn0bsinitvals25.fw    n0bsinitvals25.fw      ucode20_sslpn.fw 
 lcn0bsinitvals26.fw    n0initvals11.fw        ucode20_sslpn_nobt.fw 
 lcn0initvals24.fw      n0initvals16.fw        ucode21_sslpn.fw 
 lcn0initvals25.fw      n0initvals17.fw        ucode21_sslpn_nobt.fw 
 lcn0initvals26.fw      n0initvals22.fw        ucode22_mimo.fw 
 lcn1bsinitvals24.fw    n0initvals24.fw        ucode22_sslpn.fw 
 lcn1bsinitvals25.fw    n0initvals25.fw        ucode24_lcn.fw 
 lcn1bsinitvals26.fw    n16bsinitvals30.fw     ucode24_mimo.fw 
 lcn1initvals24.fw      n16initvals30.fw       ucode25_lcn.fw 
 lcn1initvals25.fw      n18bsinitvals32.fw     ucode25_mimo.fw 
 lcn1initvals26.fw      n18initvals32.fw       ucode26_mimo.fw 
 lcn2bsinitvals24.fw    n1bsinitvals20.fw      ucode27_sslpn.fw 
 lcn2bsinitvals25.fw    n1initvals20.fw        ucode29_mimo.fw 
 lcn2bsinitvals26.fw    n2bsinitvals19.fw      ucode30_mimo.fw 
 lcn2initvals24.fw      n2initvals19.fw        ucode32_mimo.fw 
 lcn2initvals25.fw      pcm5.fw                ucode33_lcn40.fw 
 lcn2initvals26.fw      sslpn0bsinitvals16.fw  ucode5.fw 
 lcn400bsinitvals33.fw  sslpn0initvals16.fw    ucode9.fw

---

### Post by Peripetilja on 2012-07-10
First command 
```
[   29.585557] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 3
[   29.585587] brcmsmac 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.585598] brcmsmac 0000:03:00.0: setting latency timer to 64
[   32.430177] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   32.430188] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   32.431159] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   32.431544] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.432885] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  124.115223] wlan0: authenticate with 00:1d:68:fb:fe:18 (try 1)
[  124.117819] wlan0: authenticated
[  124.118998] wlan0: associate with 00:1d:68:fb:fe:18 (try 1)
[  124.123291] wlan0: RX AssocResp from 00:1d:68:fb:fe:18 (capab=0x411 status=0 aid=1)
[  124.123304] wlan0: associated
[  124.124727] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  124.124742] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  124.124766] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  124.125402] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  134.356020] wlan0: no IPv6 routers present
[  169.208632] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  169.208649] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  169.208659] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  169.208667] wlan0: deauthenticating from 00:1d:68:fb:fe:18 by local choice (reason=3)
[  172.935715] wlan0: authenticate with 00:1d:68:fb:fe:18 (try 1)
[  172.937333] wlan0: authenticated
[  172.938023] wlan0: associate with 00:1d:68:fb:fe:18 (try 1)
[  172.945127] wlan0: RX ReassocResp from 00:1d:68:fb:fe:18 (capab=0x411 status=0 aid=1)
[  172.945136] wlan0: associated
[  172.945968] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  172.945977] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  172.945989] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  178.138834] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  178.138857] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  178.138871] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  178.138883] wlan0: deauthenticating from 00:1d:68:fb:fe:18 by local choice (reason=3)
```

Second one
```
Jul 10 16:29:22 ubuntu kernel: [  178.138883] wlan0: deauthenticating from 00:1d:68:fb:fe:18 by local choice (reason=3)
Jul 10 16:29:22 ubuntu NetworkManager[1469]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jul 10 16:29:23 ubuntu avahi-daemon[1355]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c218:85ff:fe94:427f.
Jul 10 16:29:23 ubuntu avahi-daemon[1355]: New relevant interface wlan0.IPv6 for mDNS.
Jul 10 16:29:23 ubuntu avahi-daemon[1355]: Registering new address record for fe80::c218:85ff:fe94:427f on wlan0.*.
Jul 10 16:43:41 ubuntu NetworkManager[1469]: <info> WiFi now disabled by radio killswitch
Jul 10 16:43:41 ubuntu NetworkManager[1469]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jul 10 16:43:41 ubuntu NetworkManager[1469]: <info> (wlan0): deactivating device (reason 'none') [0]
Jul 10 16:43:41 ubuntu avahi-daemon[1355]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 10 16:43:41 ubuntu avahi-daemon[1355]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c218:85ff:fe94:427f.
Jul 10 16:43:41 ubuntu avahi-daemon[1355]: Withdrawing address record for fe80::c218:85ff:fe94:427f on wlan0.
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> disable requested (sleeping: no  enabled: yes)
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> sleeping or disabling...
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (eth0): now unmanaged
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (eth0): cleaning up...
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (eth0): taking down device.
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (wlan0): now unmanaged
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jul 10 16:54:35 ubuntu NetworkManager[1469]: <info> (wlan0): cleaning up...
```

---

### Post by chili555 on 2012-07-10
@Dirkzobb--> Following reboot this is what I have:


dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ [COLOR="Red"]sudo apt-get remove --purge bcmwl-kernel-source[/COLOR]
[sudo] password for dirkzobb:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
dirkzobb@dirkzobb-HP-Compaq-nx6325-RU594ES-ABU:~$ [COLOR="Red"]sudo apt-get install linux-firmware-nonfree[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-firmware-nonfree is already the newest version. You don't have to re-run these commands each time. If it's installed or uninstalled, it does nothing to try to install or uninstall again except wear out your keyboard.> b43-phy0: Radio hardware status changed to DISABLED Say what?? Please let us see:```
rfkill list all
```Did you switch the switch or what?

---

### Post by Dirkzobb on 2012-07-10
Hi,
You're a genius! Wifi now working. Many thanks.

---

### Post by chili555 on 2012-07-10
@Peripetilja--> WiFi now disabled by radio killswitchI know I sound like a stuck record, but did you switch the switch or what?

---

### Post by Dirkzobb on 2012-07-10
Hi, I switched the switch. Tried before but nothing happened. What was the problem? Conflicting drivers?

---

### Post by chili555 on 2012-07-10
> **Dirkzobb said:**
> Hi, I switched the switch. Tried before but nothing happened. What was the problem? Conflicting drivers?Exactly. For your device 14e4:4311, you had the STA driver wl; you wanted b43 and it's required firmware package; after which you needed to turn the radio on with the switch.

Glad it's working.

---

### Post by Peripetilja on 2012-07-10
> **chili555 said:**
> @Peripetilja--I know I sound like a stuck record, but did you switch the switch or what?
When I switch the switch I can see/hide my network connection, but the light stays orange all the time and is still unable to connect.
Could it be that WiFi is disabled in BIOS?

---

### Post by chili555 on 2012-07-10
> Could it be that WiFi is disabled in BIOS?Not if you can see your network. The light is relatively unimportant; some drivers handle the light or LED correctly and some not at all.

Studying...

---

### Post by Peripetilja on 2012-07-10
> **chili555 said:**
> Not if you can see your network. The light is relatively unimportant; some drivers handle the light or LED correctly and some not at all.

Studying...
I was decived by the light at first and almost wrote there's no difference although there is one.
Waiting for your instructions.

---

### Post by chili555 on 2012-07-11
I have read a very few cases where the STA driver works for your device 14e4:4727 where brcmsmac does not. Even more puzzling, one case where only the latest compiled version from Broadcom works. Let's try first the default Ubuntu version:```
sudo su
apt-get install brcmwl-kernel-source
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe -r brcmsmac
modprobe wl
exit
```How about now? Will it connect and stay connected?

It may take a reboot.

---

### Post by Peripetilja on 2012-07-11
```
apt-get install brcmwl-kernel-source
```
Gave me this error
```
E: Unable to locate package brcmwl-kernel-source
```

```
modprobe wl
```
Gave me this
```
FATAL:Module wl not found.
```

---

### Post by chili555 on 2012-07-11
"What a drag it is getting old."  --Mick Jagger

Sorry, I meant:```
[COLOR="Red"]bcmwl[/COLOR]-kernel-source
```Please try again.

---

### Post by Peripetilja on 2012-07-11
It is working! \o/

---

