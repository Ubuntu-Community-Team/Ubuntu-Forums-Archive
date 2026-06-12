---
title: "wireless not working in ubuntu 10.04  (disconnecting again and again)"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Akash Kumar on 2010-06-01
Hello Everybody,

This is my first post on this forum.

I installed ubuntu 10.04 a few days ago. And I am running into a few problems wherein my wireless network disconnects and prompts me again for password.

Even when I re-enter it (correctly of course) I cannot reconnect and I have to do a system restart. After the restart, the wireless stays connected but disconnects again after a while and I find myself stuck in this loop.

I do not know if the following is any help, but below I am producing the output of lspci command and a few log messages that I think maybe related to this problem

Here is the output of lspci command


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)





And here are some messages that show up quite often in daemon.log

May 31 17:20:31 akash-laptop wpa_supplicant[919]: Trying to associate with SSID 'sainath'
May 31 17:20:31 akash-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 31 17:20:31 akash-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 31 17:20:31 akash-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 31 17:20:31 akash-laptop wpa_supplicant[919]: Association request to the driver failed
May 31 17:20:33 akash-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 39)
May 31 17:20:33 akash-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 39).
May 31 17:20:33 akash-laptop NetworkManager: <WARN>  nm_device_wifi_set_mode(): error setting card wlan0 to mode 2: Device or resource busy


Please let me know if there is any fix you know (or can figure out) for this problem.

Regards
-Akash


PS: I believe (maybe I am incorrect,, I am not sure) that this might be a hardware problem. I got frustrated and tried different versions of ubuntu (9.10 and 9.04) as well but it did not help.

---

### Post by -Shuji- on 2010-06-03
Akash, I'm experiencing that exact same issue but I'm using a different wireless card.

Buffalo WLI-CB-B11
Chipset: RTL8180L

I hope someone can help us fix this problem.

Shuji

---

### Post by greazeball on 2010-06-03
I am also having the same problem on a ThinkPad T60

Apologies because I'm not a very sophisticated user, but I'm copying the same logs as Akash.  If someone thinks they'll be able to help if I give more info, please tell me what to do!

lspci

-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
           +-01.0-[0000:01]----00.0  ATI Technologies Inc M52 [Mobility Radeon X1300]
           +-1b.0  Intel Corporation N10/ICH 7 Family High Definition Audio Controller
           +-1c.0-[0000:02]----00.0  Intel Corporation 82573L Gigabit Ethernet Controller
           +-1c.1-[0000:03]----00.0  Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection
           +-1c.2-[0000:04-0b]--
           +-1c.3-[0000:0c-13]--
           +-1d.0  Intel Corporation N10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation N10/ICH 7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation N10/ICH 7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation N10/ICH 7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
           +-1e.0-[0000:15-18]----00.0  Texas Instruments PCI1510 PC card Cardbus Controller
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller
           \-1f.3  Intel Corporation N10/ICH 7 Family SMBus Controller

daemon.log

Jun  3 21:10:44 lazarus wpa_supplicant[879]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jun  3 21:10:44 lazarus NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jun  3 21:10:44 lazarus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1372
Jun  3 21:11:00 lazarus NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jun  3 21:11:00 lazarus avahi-daemon[746]: Withdrawing address record for 192.168.1.33 on wlan0.
Jun  3 21:11:00 lazarus avahi-daemon[746]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.33.
Jun  3 21:11:00 lazarus avahi-daemon[746]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) starting connection 'Auto ROCK-ON-2'
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 21:11:00 lazarus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto ROCK-ON-2' has security, and secrets exist.  No new secrets needed.
Jun  3 21:11:00 lazarus NetworkManager: <info>  Config: added 'ssid' value 'ROCK-ON-2'
Jun  3 21:11:00 lazarus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun  3 21:11:00 lazarus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 21:11:00 lazarus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun  3 21:11:00 lazarus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 21:11:00 lazarus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 21:11:00 lazarus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 21:11:00 lazarus NetworkManager: <info>  Config: set interface ap_scan to 1
Jun  3 21:11:02 lazarus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 21:11:12 lazarus bluetoothd[848]: HCI dev 0 down
Jun  3 21:11:12 lazarus bluetoothd[848]: Adapter /org/bluez/845/hci0 has been disabled
Jun  3 21:11:12 lazarus bluetoothd[848]: Stopping security manager 0
Jun  3 21:11:12 lazarus bluetoothd[848]: HCI dev 0 unregistered
Jun  3 21:11:12 lazarus bluetoothd[848]: Unregister path: /org/bluez/845/hci0
Jun  3 21:11:13 lazarus avahi-daemon[746]: Withdrawing address record for fe80::213:2ff:fe99:90bc on wlan0.
Jun  3 21:11:13 lazarus NetworkManager: <info>  (wlan0): device state change: 5 -> 2 (reason 0)
Jun  3 21:11:13 lazarus NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jun  3 21:11:15 lazarus NetworkManager: <info>  WiFi now disabled by radio killswitch

The wireless went down and I disabled it.  Sorry I'm not more savvy, but if anyone can help it would be much appreciated!

---

### Post by Akash Kumar on 2010-06-04
Hello again everybody,

The  above posts make three of us facing the same problem :(

Please help

Regards
-Akash

---

### Post by JimmieC on 2010-06-04
Have you updated your driver through System > Administration > Hardware Drivers? Have you assigned static ip addresses, subnet, gateway, and DNS addresses? 

Jim

---

### Post by Warnfried on 2010-06-04
I've got the exact problem using an "Extensa 5630EZ" notebook.
It occured on 9.10 and continues now on 10.4.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: RaLink RT2860
0d:06.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 01)

---

### Post by Dutch-Man on 2010-06-04
Same problem.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
85:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)

---

### Post by Nezing on 2010-06-04
Tried Ubuntu 10.4 today via my Netgear Router,and wireless is just not recognised.Hate to say this here,but via my msi u130 Netbook,MeeGo works flawlessly,via wifi.I simply installed the OS,and it recognised my wireless connection without any fuss.Please Mr Shuttleworth (Mark),I know I will get flak for this,but come to some arrangement where Ubuntu just works.For the record,I have used Ubuntu on a spare desktop for the last 5 years,but have never managed to get any "buntu" version working via a wireless connection.And no I have not got the time to spend ages "compiling code" or getting "Window" drivers by other means.Are you listening software companies?
Sorry for the rant guys,but I have had a bad morning :(

---

### Post by llawwehttam on 2010-06-04
Try the link in my sig. Works for most. Just replace karmic with lucid in the commands.

---

### Post by Dutch-Man on 2010-06-04
I cant install those things. It says that it could not be found.

---

### Post by Akash Kumar on 2010-06-04
Hello Jim,

Thanks for your reply.
When I tried updating the drivers, the following message showed up 

"No proprietary drivers are in use on this system"

As for the IP address, its not static, we use DHCP.

Does that help you figure out the issue we are facing?

Regards
-Akash

---

### Post by llawwehttam on 2010-06-04
Try the following:

```

linux-backports-modules-`uname -r`-generic
linux-backports-modules-lucid
linux-backports-modules-lucid-generic
linux-backports-modules-wireless-lucid-generic
```

---

### Post by KaYnemO on 2010-06-04
The problem is in conflict of radeon ati and wifi module. If you disable KMS in GRUB, your wifi will remain stable and will not disconnect.

---

### Post by Dutch-Man on 2010-06-04
> **llawwehttam said:**
> Try the following:

```

linux-backports-modules-`uname -r`-generic
linux-backports-modules-lucid
linux-backports-modules-lucid-generic
linux-backports-modules-wireless-lucid-generic
```
this is what i get if i do any of those commands:
linux-backports-modules-2.6.32-22-generic-generic: command not found

---

### Post by llawwehttam on 2010-06-04
> **KaYnemO said:**
> The problem is in conflict of radeon ati and wifi  module. If you disable KMS in GRUB, your wifi will remain stable and  will not disconnect.
  sorry mate but its more bother than its worth.


oh I'm so sorry, I wasn't thinking properly, how stupid of me...


```
sudo apt-get install linux-backports-modules-`uname -r`-generic &&
sudo apt-get install linux-backports-modules-lucid &&
sudo apt-get install linux-backports-modules-lucid-generic &&
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by Akash Kumar on 2010-06-04
Hello llawwehttam,

My kernel version is 2.6.32-22-generic

I also could not find the first 3 packages you listed. The 4 th package you suggested is available on synaptic. 

The first package that you suggested is not available

Dont know what to do now. Please suggest whenever you get time.

Best
-Akash

---

### Post by llawwehttam on 2010-06-04
where I typed `uname -r` the terminal should replace that with your kernel version.

If it doesn't please enter uname -r into a terminal and copy and paste it into the line

ie for me

sudo apt-get install linux-backports-modules-`uname -r`

would become:


sudo apt-get install linux-backports-modules-2.6.31-22-generic


Please don't use synaptic though. Open terminal

Applications> Accessories> Terminal (last time I looked)

and copy and paste the code in.

---

### Post by Dutch-Man on 2010-06-04
> **llawwehttam said:**
> where I typed `uname -r` the terminal should replace that with your kernel version.

If it doesn't please enter uname -r into a terminal and copy and paste it into the line

ie for me

sudo apt-get install linux-backports-modules-`uname -r`

would become:


sudo apt-get install linux-backports-modules-2.6.31-22-generic


Please don't use synaptic though. Open terminal

Applications> Accessories> Terminal (last time I looked)

and copy and paste the code in.
2.6.32-22-generic

---

### Post by llawwehttam on 2010-06-04
so for you it would be:
```

sudo apt-get install linux-backports-modules-2.6.32-22-generic


```

---

### Post by Dutch-Man on 2010-06-04
> **llawwehttam said:**
> so for you it would be:
```

sudo apt-get install linux-backports-modules-2.6.32-22-generic


```
Kon pakket linux-backports-modules-2.6.32-22-generic niet vinden

What means that the package could not be found.

---

### Post by llawwehttam on 2010-06-04
sorry mate, no more ideas. This isn't really my area.

---

### Post by Dutch-Man on 2010-06-04
Is there maybe another version of ubuntu 10.04?

---

### Post by -Shuji- on 2010-06-04
Goodluck to you guys.  I've decided to go back to XP.  I don't have a lot of time to try and fix this problem.  Ubuntu is great but many devices are not yet supported.

---

### Post by Dutch-Man on 2010-06-04
I just installed again a fresh Ubuntu and now i did download every update exept the kernal updates. And guess what? Running for more than 4h without any problems! That means there is a kernal proplem.

---

### Post by drpjkurian on 2010-06-04
Hi
Please install lucid backport modules for wireless
and backport modules generic via synaptic package manager

---

### Post by greazeball on 2010-06-04
I did this

> **llawwehttam said:**
> 
```
sudo apt-get install linux-backports-modules-`uname -r`-generic  &&
sudo apt-get install linux-backports-modules-lucid &&
sudo apt-get install linux-backports-modules-lucid-generic &&
sudo apt-get install  linux-backports-modules-wireless-lucid-generic
```

and this

> **drpjkurian said:**
> Hi
Please install lucid backport modules for wireless
and **backport modules generic via synaptic package manager**

and restarted and things seem to be more stable (so far)


Thanks very much!

---

### Post by JimmieC on 2010-06-04
I could not connect using DHCP, I had to manually configure my wireless adapter. I first had a Linksys pci wireless with a Broadcom driver. It would not connect until I updated the driver through System > Administration > Hardward Drivers and then set a static ip address. After I manually configured the adapter I also had to reboot. I did not have to do this in previous versions.

I then purchased an inexpensive Gigabyte ($15.00) pci wireless adapter and it has been very stable. I had to assign a static ip address and then reboot after the manual configuration. Now it works just fine.

I run a Linksys router with Tomato firmware but for my setup I have to use a manually configured wireless adapter.

Jim

---

### Post by drpjkurian on 2010-06-05
> **greazeball said:**
> I did this



and this



and restarted and things seem to be more stable (so far)


Thanks very much!


Hi
Most welome buddy

---

### Post by Akash Kumar on 2010-06-05
Hello There,

Can you be a little more specific (you already are, I just ask for my convenience) as to what backport modules I should get from synaptic.

I think you mean these

linux-backport-modules-wireless-lucid-generic
linux-backport-modueles-headers-lucid-generic (This is the generic backport module you mention. Right?)

There are a bunch of other wireless backport modules. I should get those as well. Is that correct?

Please let me know

Best Regards
-Akash

---

### Post by Karim_ on 2010-06-05
Happens with windows as well you just don't see it happen, because window automatically reconnects.

---

### Post by Karim_ on 2010-06-05
Happens with windows as well you just don't see it happen, because window automatically reconnects. Ubuntu on the other hand asks for a password or sometimes prompts you to reconnect.

---

### Post by Karim_ on 2010-06-05
Happens with windows as well you just don't see it happen, because window automatically reconnects. Ubuntu on the other hand asks for a password or sometimes prompts you to reconnect.

---

### Post by Karim_ on 2010-06-05
Happens with windows as well you just don't see it happen, because window automatically reconnects. Ubuntu on the other hand asks for a password or sometimes prompts you to reconnect.

---

### Post by Karim_ on 2010-06-05
Happens with windows as well you just don't see it happen, because  window automatically reconnects. Ubuntu on the other hand asks for a  password or sometimes prompts you to reconnect.

---

### Post by drpjkurian on 2010-06-05
Hi Karim

Why do you echo your comments. Repeating the post several times does not attract swift solution....

---

### Post by drpjkurian on 2010-06-05
> **Akash Kumar said:**
> Hello There,

Can you be a little more specific (you already are, I just ask for my convenience) as to what backport modules I should get from synaptic.

I think you mean these

linux-backport-modules-wireless-lucid-generic
linux-backport-modueles-headers-lucid-generic (This is the generic backport module you mention. Right?)

There are a bunch of other wireless backport modules. I should get those as well. Is that correct?

Please let me know

Best Regards
-Akash

Hi Akash
Download the packages which I ve mentioned, ignore the rest

---

### Post by Karim_ on 2010-06-05
> **drpjkurian said:**
> Hi Karim

Why do you echo your comments. Repeating the post several times does not attract swift solution....

It's not my fault. It's an error it happen when I decided to rewrite my post and hit the stop button. If I could I would delete them. Sorry.

---

### Post by carbon512 on 2010-06-05
Hi all -- new to this forum; jumping on this thread because it has been really relevant, and I think my other post for help was maybe not specific enough.

I was having the same problem (except only with one particular WPA network, and when I did connect for 20-30 seconds, my connection would bum everyone else off the network!). In trying to fix it, I have now lost all wireless recognition. I'm running Ubuntu 10.04. In my network icon area, I only see ethernet and vpn (I have no VPN connections).

I just installed the linux-backports-modules-wireless-lucid-generic. No go. Here is what I show as installed doing a "backports" search in synaptic:

 linux-backports-modules-wireless-lucid-generic version 2.6.32.22.23
linux-headers-lbm-2.6.32.22 generic     version 2.6.32-22.13
linux-backports-modules-wireless-2.6.32-22-generic     version 2.6.32-22.13
linux-backports-modules-alsa-2.6.32-22-generic pae     version 2.6.32-22.13

linux-backports-modules-alsa-2.6.32.22-generic  (version version 2.6.32-22.23) shows as installed too but it does not have a ubuntu symbol next to it. From a different repository?

wirless network shows to be unclaimed:
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:9d:f2:4e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.102.55 latency=0 multicast=yes
       resources: irq:27 memory:93500000-9353ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:92500000-92501fff


My attempts to install the windows wireless driver (which I did not seem to need until I started messing with it), using ndisgtk, are detailed over in post [http://ubuntuforums.org/showthread.php?p=9413430](http://ubuntuforums.org/showthread.php?p=9413430)

Is there anything else I am missing? Or something I should unistall? Am I missing something really obvious? The network controller is right there... I just cant seem to use it any more or have it play with Ubuntu any more.

Thanks; this is a great resource!

---

### Post by Akash Kumar on 2010-06-06
Hello Dr Kurian,

Thanks you have been great help.

I hope I am not annoying you, but I wanted to ask that I am unable to find the following 3 packages (neither on synaptic nor via command line)


1) linux-backports-modules-2.6.32-22-generic
2) linux-backport-modules-lucid
3) linux-backport-modules-lucid-generic

In synaptic, I could however see the following related to 2.6.32-22 which contains backport driver headers for generic kernel image

linux-backport-modules-headers-lucid-generic


I am getting a bunch of other wireless and alsa related packages but not the ones you mentioned.
I am not sure why. Any ideas? 

Regards
-Akash

---

### Post by gordon33 on 2010-06-06
Hello JimmieC

I have had the same problem no connection to wireless since i installed updates 2 days ago.

 Jim wrote
Have you updated your driver through System > Administration > Hardware Drivers? Have you assigned static ip addresses, subnet, gateway, and DNS addresses?

Jim

What is, or how do you assigned static ip addresses, subnet, gateway, and DNS addresses?

Thank you

gordon33

---

### Post by drpjkurian on 2010-06-06
> **gordon33 said:**
> Hello JimmieC

I have had the same problem no connection to wireless since i installed updates 2 days ago.

 Jim wrote
Have you updated your driver through System > Administration > Hardware Drivers? Have you assigned static ip addresses, subnet, gateway, and DNS addresses?

Jim

What is, or how do you assigned static ip addresses, subnet, gateway, and DNS addresses?

Thank you

gordon33


Hi
Please note that there has been a kernel upgrade recently. Most probably you might require a recompiling of your drivers.

please consider my thoughts

---

### Post by drpjkurian on 2010-06-06
> **Karim_ said:**
> It's not my fault. It's an error it happen when I decided to rewrite my post and hit the stop button. If I could I would delete them. Sorry.

No probs mate. its ok

---

### Post by drpjkurian on 2010-06-06
> **Akash Kumar said:**
> Hello Dr Kurian,

Thanks you have been great help.

I hope I am not annoying you, but I wanted to ask that I am unable to find the following 3 packages (neither on synaptic nor via command line)


1) linux-backports-modules-2.6.32-22-generic
2) linux-backport-modules-lucid
3) linux-backport-modules-lucid-generic

In synaptic, I could however see the following related to 2.6.32-22 which contains backport driver headers for generic kernel image

linux-backport-modules-headers-lucid-generic


I am getting a bunch of other wireless and alsa related packages but not the ones you mentioned.
I am not sure why. Any ideas? 

Regards
-Akash

Hi Akash

Please see the screenshot

---

### Post by Akash Kumar on 2010-06-06
Thanks a lot Dr Kurian,

I am trying this out just now.

BTW you guys have been doing a great job.

I have to admit Microsft gave us only windows, linux (in a very real sense because of you guys) gives us the whole house.

Have a nice day Doc

-Akash

---

### Post by Smokabowl on 2010-06-10
> **drpjkurian said:**
> Hi
Most welome buddy

For cereals though. That didn't solve my problem. I'm still getting disconnects quite often. I've moved back to the normal wireless kernel drivers. I'm starting to think it's a BIOS issue. I'm running a Thinkpad T60 && this

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by drpjkurian on 2010-06-12
Hi smokabowl
:twisted:

---

### Post by claracc on 2010-06-29
> **Smokabowl said:**
> For cereals though. That didn't solve my problem. I'm still getting disconnects quite often. I've moved back to the normal wireless kernel drivers. I'm starting to think it's a BIOS issue. I'm running a Thinkpad T60 && this

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

What works for me, with the same wireless card is to install wicd instead of gnome network manager.

Gnome network-manager (in karmic and in lucid) connects and disconnects wifi all the time, doing it unusable (i think it is an old problem), wicd fixes the problem, you can install it from synaptic.

Regards

---

### Post by mrufino1 on 2010-07-01
I also have a t60 and have been getting this disconnect, which never happened on previous versions of ubuntu. I was about to install wicd before I read this, so I'm doing that now. Do I need to uninstall the gnome network manager?The disconnect only happens if I am downloading a large file or watching something on hulu (and not always) but it started again big time just now, while trying to download the iso for av linux 4.0. (av uses wicd also, which is how I knew about it, I dual boot ubuntu and av).

---

### Post by claracc on 2010-07-01
> **mrufino1 said:**
> . Do I need to uninstall the gnome network manager?.

when you select in synaptic wicd and apply for installing, it automatically uninstall gnome-network-manager in karmic koala. I think, you have to uninstall it manually (synaptic too) in lucid lynx, after installing wicd.

Regards.

---

### Post by mrufino1 on 2010-07-01
Yes, you do have to uninstall it. I did, and wicd is working well. Let's hope it stays that way! It's been a long time since I had wireless issues with ubuntu (6.04-ish...).

---

### Post by rcktsingh on 2010-07-01
> **drpjkurian said:**
> Hi Akash

Please see the screenshot

Hi, first of all, thanks for the wonderful help you guys are providing. I tried installing the packages in the screenshot, was running fine last night but got disconnected again this morning. ](*,) 

secondly. after reading about gnome nm and wicd, i am planning to try that too. but when i go to synaptic and type wicd in the search tab, i see a couple of packages(screenshot attached). which one do I install ?

Also, what should I do to uninstall gnome network-manager ?

Any kind of help is appreciated.

Thanks

---

### Post by mrufino1 on 2010-07-01
There should be a wicd that is a meta package, meaning it will collect everything you need to install it. It will say that on it. And for network manager, I just typed in network-manager and anything that seemed to fit was uninstalled, a few of them put another package on the list to uninstall (intentionally). I then restarted the computer and wicd was working, so far so good.

---

### Post by rcktsingh on 2010-07-01
Thanks !! done that. lets see how it goes. wireless used to work fine in my system with network manager, until I updated my system with the latest updates when it started disconnecting too much !! restarting the system helped but thats a stupid way.

---

### Post by metalf8801 on 2010-07-01
I've been having the same problem if I'm using a kernel newer then 2.6.32-21 

I don't have this problem with 2.6.32.21 or 2.6.31-11-rt (real time) kernels 

I was hopping with the new 2.6.32-23 which I just got in an update that I wouldn't be having this problem but I still am 

I've tried installing linux-backports-modules-wireless-karmic-generic
which didn't help and then I uninstall it 

then installed wicd which kind of helps but it keep disconnecting and then reconnecting which doesn't happen with the older kernel 

has anyone else tried using an older kernel?

---

### Post by rcktsingh on 2010-07-01
> **metalf8801 said:**
> I've been having the same problem if I'm using a kernel newer then 2.6.32-21 

I don't have this problem with 2.6.32.21 or 2.6.31-11-rt (real time) kernels 

I was hopping with the new 2.6.32-23 which I just got in an update that I wouldn't be having this problem but I still am 

I've tried installing linux-backports-modules-wireless-karmic-generic
which didn't help and then I uninstall it 

?

+1. 
today is my 1st day with wicd. till now going ok, except on one occasion when it got disconnected and i had to restart my system. I hardly remember facing this problem when i used to be on an older kernel.

---

### Post by rcktsingh on 2010-07-02
okay. i am kinda pissed off today. wicd has got disconnected 3 times today in a span of 4 hours. I had to restart my system to get it back. It never used to be like that before some stupid updates few days back. 

I dont understand. wireless problems (have to dig down to find a workaround).. screen flickering problems whenever some heavy application starts on my system. whats the point of using linux if such basic problems keep popping up. 

I use linux because it helps me in my work. But if this kind of stupid problems persist, I seriously got no time fixing them around. I dont care about other flashy things linux has to offer like rhythmbox, compiz and all that crap. All you need to work peacefully is a stable system. It doesn't matter how much you keep shouting about why Linux is better than Windows, for problems like these where you have to spend days finding a stupid workaround, Windows always scores better.

Thanks,
a very frustrated guy struggling with wifi and screen flickering problems after trying out numerous workarounds!!

p.s. I don't mind moving this post to testimonials !!

---

### Post by metalf8801 on 2010-07-02
> **rcktsingh said:**
> okay. i am kinda pissed off today. wicd has got disconnected 3 times today in a span of 4 hours. I had to restart my system to get it back. It never used to be like that before some stupid updates few days back. 

I dont understand. wireless problems (have to dig down to find a workaround).. screen flickering problems whenever some heavy application starts on my system. whats the point of using linux if such basic problems keep popping up. 

I use linux because it helps me in my work. But if this kind of stupid problems persist, I seriously got no time fixing them around. I dont care about other flashy things linux has to offer like rhythmbox, compiz and all that crap. All you need to work peacefully is a stable system. It doesn't matter how much you keep shouting about why Linux is better than Windows, for problems like these where you have to spend days finding a stupid workaround, Windows always scores better.

Thanks,
a very frustrated guy struggling with wifi and screen flickering problems after trying out numerous workarounds!!

p.s. I don't mind moving this post to testimonials !!

do you have "Ubuntu, with Linux 2.6.31.21" as an option in grub? If you do try using that if it works better use SartUp-Manager to make it your default 

If you don't try installing the real time kernel and see if that works better for you 
sudo apt-get install linux-rt linux-headers-rt 

then make sure to select "Ubuntu, with Linux 2.6.31.11-rt" in grub to test it out 

good luck and I'll keep looking for better fixes for this problem hopefully the next Kernel will not have this problem

Also have you looked in Launchpad to see if anyone has reported this as a bug? I really think they have but I don't have a link to the report right now. It important that we report that the bug is also affecting our wireless cards.

---

### Post by andyhelloween on 2010-07-03
> **claracc said:**
> when you select in synaptic wicd and apply for installing, it automatically uninstall gnome-network-manager in karmic koala. I think, you have to uninstall it manually (synaptic too) in lucid lynx, after installing wicd.

Regards.

I've installed wicd and so far, no trouble.
Thanks a lot!

---

### Post by nilcam on 2010-07-08
> **andyhelloween said:**
> I've installed wicd and so far, no trouble.
Thanks a lot!

Is it still running well? I updated my system a few days ago and I've had nothing but wireless problems since. I've dealt with sound issues in the past but wireless has always worked flawlessly on this system.

I'm on a Toshiba Satellite a135-s2276 with an Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) card.

Thanks.

---

### Post by rcktsingh on 2010-07-11
> **metalf8801 said:**
> do you have "Ubuntu, with Linux 2.6.31.21" as an option in grub? If you do try using that if it works better use SartUp-Manager to make it your default 

If you don't try installing the real time kernel and see if that works better for you 
sudo apt-get install linux-rt linux-headers-rt 

then make sure to select "Ubuntu, with Linux 2.6.31.11-rt" in grub to test it out 

good luck and I'll keep looking for better fixes for this problem hopefully the next Kernel will not have this problem

Also have you looked in Launchpad to see if anyone has reported this as a bug? I really think they have but I don't have a link to the report right now. It important that we report that the bug is also affecting our wireless cards.

I uninstalled wicd and re-installed network manager. it seems to be working more or less fine as of now. (I have kinda adjusted to the fact that its almost impossible to get it perfectly working) 

I didn't feel like playing with kernels -- too much of a stress. While wicd was working more or less in a stable manner in my apartment(secured nw), wicd didn't work at all in my school, which uses an unsecured network. I have a feeling wicd doesn't work well with unsecured networks. So I am better off with nw-manager.

Thanks for all those words by the way!! Appreciate that.

---

### Post by mrufino1 on 2010-07-11
I also reinstalled network-manager, wicd has some weird quirks when you are trying to connect to a new network, finally grew tired of it. I'll see what happens with network manager this time.

---

### Post by ov3rcl0ck on 2010-07-11
Are they backport drivers, because they may have been backported because they were unstable/bugged. If they are you may have to use a different drivers. Trying to find an opensource driver for it is probably the best bet, but they may be a bit slower because they have restrictions to some of that "super secret" proprietary mumbo-jumbo.

If theres no other driver, then last resort is always NDIS wrapper.

Also, it maybe a problem with conflicting modules, you have 2 modules(drivers if you will) that don't like eachother...

---

### Post by JackAbear on 2010-07-11
Everyone seems to forget the most important variable...i.e the fluctuating reception and dropouts of wireless Broadband,
If you do get  connected at all, you probably got it right, the problem is if two minutes later you loose the signal, most will go and change something in their setting to get it back...that is often the wrong thing to do and may get you further from you goal....it probably was a cloud or rain or trees swinging in the wind....just saying do not forget that variable.
I kept loosing mine today during the FIFA game,...was the same on my Wind-Hose  installation. It is what it is! expensive and unreliable when there is big demand.
also when doing long downloads, I put a fan right on the Rocket stick, cause it gets very hot when it is working hard and slows down to between 5 kbs&40kbs,....cool it and speed comes back( if the reception is good of course)

It is a bit like witchcraft to get them working right...and you need a network manager like the one used on 9.04 that has broadband wireless as an option...I wish I could help more, but this is new to me also, it took me two weeks to figure it out and get it working, and I tried so many things that I'm not certain which parts of what I did were useless and which ones caused it to work ...YET!?
I want to re-install at this point and try to replicate what I did , and take notes to formulate a working procedure, which I will post in a couple of weeks if I'm successful the second time around. 
until then, good luck all.

---

### Post by KaYnemO on 2010-07-13
As I am reading all your comments and posts, I have to say that the easiest solution was what I have done - disabling KMS - I lost a webcam, but ever since my wifi has been working flawlessly.

---

### Post by atulkakrana on 2010-08-21
DELL STUDIO 14 + Ubuntu 10.04
Broadcom card
5 Years of power Ubuntu usage
TIME TO MOVE ON ======= WINDOWS 7 Here I come....I want to kiss Bill Gates for first time ever...you have made an incredibly stable system....Windows 7....

The Story 
NO MATTER WHAT I DO MY WIFI DISCONNECTS RANDOMLY....ONLY WHILE DOWNLOADING TORRENTS

Install backports....Limit speed...turn off Wifi card power saver...Play Rhythmbox to prevent sleep/whatever....etc etc....nothing works...

I am a proponent of linux...i am using it for last 5 years...and when these problems can violently distract me..what will happen to new users....

Canonical and Ubuntu developers...please stop it...you have done enough....do not develop it any more...stop and concentrate on what you have developed already...

I ASSURE YOU THAT ONLY BECAUSE OF THIS PROBLEM>>>I WILL SHIFT TO WINDOWS 7....I personally believe that its easy to use Windows 7 and it is more stable then Ubuntu these days....

GO AWAY UBUNTU...I spend so much of time trouble shooting your problems...still 'full brightness' 'wifi disconnect' 'ALSA re installation after kernel update'....GOD I will shoot myself...Its a GANG BANG..... by Canonical , Ubuntu and Linus torvalds..

I feel sorry but cant help it

Atul Kakrana

---

### Post by mlzarathustra on 2010-09-09
[SIZE=2][COLOR=Red]**UPDATE**[/COLOR]

I just did:

sudo su 
...
apt-get update 
apt-get upgrade
init 6

and now the wireless seems to now be working fine.  As of today, 2010-09-12.  Hopefully it will stay that way!

:)


original message: -------------

Hi all,

I have an ASUS Eee with an Atheros AR5001, and just installed Ubuntu/Netbook remix, after suffering with the silly OS that ASUS provided for several years.  Aside from the wireless support, it looks really cool.  Wired networking is perfectly OK.[/SIZE] [SIZE=2]

Initially, the wireless card worked, although v-e-r-y s-l-o-w-l-y.  Then Ubuntu insisted on installing a ton of updates, and after that the network card stopped working altogether.  (it still sees networks, but can't log in).[/SIZE] [SIZE=2]

After perusing this thread, I hereby summarize some possible solutions.  Please let me know if you have any take on any of these.  I want to think about this some before trying anything.[/SIZE] [SIZE=2]

Somewhat alarming that, the more recent your kernel, the less likely the wireless is to work.  On the other hand, Video used to be that way and it has gotten much better recently.[/SIZE] [SIZE=2]

Thanks![/SIZE] [SIZE=2]
  -= miles =-
[B]
Possible solutions:[/B][/SIZE] [SIZE=2]

[see "UPDATE" above]

1. Install Madwifi for Atheros in Lucid[/SIZE] [SIZE=2]
[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)[/SIZE] [SIZE=2]

Apprently, madwifi gets blacklisted by default.  Hm....[/SIZE] [SIZE=2]
---------------------------------------------------

2. Install backport modules of :[/SIZE] [SIZE=2]
   wireless
   lucid generic

[http://ubuntuforums.org/showthread.php?p=9452499#post9452499](http://ubuntuforums.org/showthread.php?p=9452499#post9452499)[/SIZE]  [SIZE=2]
 [see post #43 - it shows the relevant modules in synaptic; labeled:]
linux-backports-modules-wireless-lucid-generic
linux-backports-modules-headers-lucid-generic

There are 2 more with the -pae suffix that are unchecked.[/SIZE] [SIZE=2]

post #26 shows how to do it from the command line:[/SIZE] [SIZE=2]
sudo apt-get install linux-backports-modules-`uname -r`-generic  &&
sudo apt-get install linux-backports-modules-lucid &&
sudo apt-get install linux-backports-modules-lucid-generic &&
sudo apt-get install  linux-backports-modules-wireless-lucid-generic



----------------------------------------------------[/SIZE]   [SIZE=2]

3. install wicd (meta package) and uninstall gnome-network-manager[/SIZE] [SIZE=2]

“You might want to try changing the WPA Supplicant on your network manager to wext.  [/SIZE] [SIZE=2]
 On wicd it's the first option when you go into Preferences.”

----------------------------------------------------[/SIZE]  [SIZE=2]
4. uninstall wicd and re-install gnome-network-manager
----------------------------------------------------
5. Try switching to an older kernel (by editing the grub config)
----------------------------------------------------
6. Try using windows driver and ndiswrapper module




**Helpful commands:**[/SIZE]     [SIZE=2]

lshw -C network[/SIZE] [SIZE=2]
*lists hardware - shows info about the device*[/SIZE]    [SIZE=2]


 iwconfig  [/SIZE]   [SIZE=2]
[I]like ifconfig for wireless


[/I]
[/SIZE]      [SIZE=2]
[/SIZE]  [SIZE=2]iw event -t
[I]may require `sudo apt-get install iw` first.  it gives messages which may not be helpful for anyone other than a kernel developer, but it’s marginally better than staring at a blank screen.



[/I][/SIZE]       [SIZE=2][B]References
[/B]Here is the Linux Kernel wireless site for reporting bugs.  It talks about some things to try first, in order to isolate the problem.

[/SIZE][SIZE=1][SIZE=2]http://wireless.kernel.org/en/users/Documentation/Reporting_bugs
[/SIZE] 




[/SIZE]

---

### Post by NotTheMessiah on 2010-09-10
I am having the same problem on my MSI wind netbook. the connection drops and then it's not able to reconnect.
 I didn't have this problem with karmic koala so i am regretting "upgrading" to lucid remix.
 I've installed xp which, obviously, works without a problem. It's so frustrating since lucid is so much slicker and seems faster then KK.

---

### Post by mlzarathustra on 2010-09-12
So it sounds like the problem occurred somewhere between K and L

Are there other Koala users that can verify?  (if so, they're probably not reading this thread, unless they upgraded to Lucid and the wireless stopped working)

Thanks,
  -= miles =-

---

### Post by Praet0rian on 2010-09-22
Hi all, just wanted to be part of this, to report the same problem here on my Toshiba Satellite with Intel Wifi Link 5100.

I also tried all the steps above, not installing wicd, with no solution yet.

Besides that all, I have realized one strange thing. everytime i get kicked from my wlan network and ubuntu trying to reconnect righ after, my router seemed to reboot (other windows nb showed also no connection). This happened in my work too, with different routers. I was crashing wlan networks with my Lucid and this kernel issue, which was pretty uncomfortable for my colleagues. Can anybody confirm this? Looks like an router reboot due to an owerflow, or sth like that.

I will most probably wait for new 10.10, not touching kernels at all ;)

---

### Post by quixote on 2010-10-09
Just to confirm, dropping the wireless didn't happen in Karmic, but does for me in Lucid.  I have a Thinkpad X201s, not sure what the wireless is, just some kind of generic Intel something...?  It's not really random in my case.  It happens after I bring the machine back from suspend.  It'll be okay for a while, and then suddenly the wireless is gone.  Nothing brings it back.  I've tried: --manually giving it the accesspoint again, --disabling and reenabling wireless in network-manager, --restarting networking,  --logging out and logging back in.  The only thing that brings it back is a reboot.

The reason I saw this thread is because I thought I should try to actually fix it.  So far, I've just been rebooting. :?

---

### Post by NotTheMessiah on 2010-10-09
> **quixote said:**
> Just to confirm, dropping the wireless didn't happen in Karmic, but does for me in Lucid.  I have a Thinkpad X201s, not sure what the wireless is, just some kind of generic Intel something...?  It's not really random in my case.  It happens after I bring the machine back from suspend.  It'll be okay for a while, and then suddenly the wireless is gone.  Nothing brings it back.  I've tried: --manually giving it the accesspoint again, --disabling and reenabling wireless in network-manager, --restarting networking,  --logging out and logging back in.  The only thing that brings it back is a reboot.

The reason I saw this thread is because I thought I should try to actually fix it.  So far, I've just been rebooting. :?

welcome to the club(it's growing, unfortunately) I have given up and i am currently looking at other ditros(or i'll install KK again)

---

### Post by ryan a neily on 2011-03-07
This worked: On my netbook I am running Lucid. In Synaptic I found the lucid wireless package 
that if present will ensure during an upgrade the backport modules get upgraded too. 
Synaptic reported that the packages for the kernel could not be found and did I want to continue? 
I said yes and was given the option to upgrade the kernel with the appropriate modules etc. 
I said yes to the new kernel. Once I rebooted with the new kernel, the wireless connection works. 

Thanks for the help.

Ryan A Neily

---

### Post by tlindvall on 2011-03-13
> **ryan a neily said:**
> This worked: On my netbook I am running Lucid. In Synaptic I found the lucid wireless package 
that if present will ensure during an upgrade the backport modules get upgraded too. 
Synaptic reported that the packages for the kernel could not be found and did I want to continue? 
I said yes and was given the option to upgrade the kernel with the appropriate modules etc. 
I said yes to the new kernel. Once I rebooted with the new kernel, the wireless connection works. 

Thanks for the help.

Ryan A Neily

Interesting information. I've also been strugling with ath5k and intermittent connections.  Could you be more specific, please?
- using lucid?
- what wireless chipset you have?
- do you use ath5k driver or madwifi driver (pci_ath)?
- before installing,
--- what kernel you had before installation of that package (stock lucid?)
--- did you have some backports wireless installed?
- what was the exact package name you installed?
- after installation of the package
--- what is your current kernel version?
--- is your connection still stable?

---

### Post by sam.666 on 2011-03-15
this resolved the issue for me:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-25-generic linux-image-2.6.35-25-generic

i found it in the below post, reply #8:

[http://ubuntuforums.org/showthread.php?t=1555385](http://ubuntuforums.org/showthread.php?t=1555385)

since 2.6.35-19 that was listed in the post was not available, i did

sudo apt-cache search linux headers generic 35

and picked the latest version (2.6.35-25 in my case).

for the first time since i upgraded to lucid lynx i was able to watch an entire episode of a bandwidth-heavy program without getting disconnected.  so it appears that so far my issue with disconnecting repeatedly is addressed.

---

### Post by guru_r236 on 2011-03-15
I am also experiencing the same problem. Please advice.

---

