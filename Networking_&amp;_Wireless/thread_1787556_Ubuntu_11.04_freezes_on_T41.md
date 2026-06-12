---
title: "Ubuntu 11.04 freezes on T41"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by shredIt on 2011-06-21
Hi folks,

I upgraded Ubuntu 10.10 to 11.04 on my IBM Thinkpad T41. [http://www.thinkwiki.org/wiki/Category:T41](http://www.thinkwiki.org/wiki/Category:T41)

Since I did this, my gnome desktop freezes constantly after I connected to a wireless lan.
It doesn't freeze immediately but a couple of minutes later.

syslog gave me the hint that it could be a mistake in loading a module for my intel wireless card...

syslog:
```
Jun 21 14:40:16 BlackBox pulseaudio[1508]: module-alsa-card.c: Failed to find a working profile.
Jun 21 14:40:16 BlackBox pulseaudio[1508]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> WiFi now disabled by radio killswitch
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> (eth1): device state change: 3 -> 2 (reason 0)
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> (eth1): deactivating device (reason: 0).
```

Any help or hints are appreciated thx @ lot!!!

---

### Post by chili555 on 2011-06-21
> syslog gave me the hint that it could be a mistake in loading a module for my intel wireless card...```
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> WiFi now disabled by radio killswitch
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> (eth1): device state change: 3 -> 2 (reason 0)
Jun 21 14:40:19 BlackBox NetworkManager[479]: <info> (eth1): deactivating device (reason: 0).
```
In my not so expert opinion, I own a T40 and a T60 and I have owned two T23s, that tells you nothing useful. That simply says that the wireless switch, in your case, Fn+F5, I believe, turned the wireless off and Network Manager deactivated the device.

I'd like to see, after it freezes and you reboot:```
sudo cat /var/log/syslog | grep -e eth1 -e <wireless_driver> -e error
```If the output is sparse, check syslog.1.

Find out your wireless driver with:```
sudo lshw -C network
```Here is mine:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       --- snip ---
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:edf00000-edf00fffTherefor, in my case, I'd substitute iwl3945 above.

Whenever a T40/41/42/43 freezes, I suspect this: [http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T41-hangs-probably-the-graphics-chip-solder-problem/td-p/91563](http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T41-hangs-probably-the-graphics-chip-solder-problem/td-p/91563)

[http://www.thinkwiki.org/wiki/Problem_with_garbled_screen](http://www.thinkwiki.org/wiki/Problem_with_garbled_screen)

---

### Post by shredIt on 2011-06-21
Thank you for your quick response!!


My driver is called Intel ipw2100:

The drivers output:
```
*-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:5f:10:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=&#65533;&#65533;:3:A5A5A5A5 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:11 memory:c0214000-c0214fff
```

The Errors output:

```
Jun 21 14:31:31 BlackBox kernel: [   18.317967] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jun 21 14:31:32 BlackBox NetworkManager[464]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 21 14:31:33 BlackBox kernel: [   20.649529] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Jun 21 14:31:33 BlackBox kernel: [   20.649535] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Jun 21 14:31:34 BlackBox kernel: [   21.132292] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jun 21 14:31:34 BlackBox kernel: [   21.133039] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Jun 21 14:31:34 BlackBox NetworkManager[464]: <error> [1308659494.811027] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jun 21 14:31:34 BlackBox NetworkManager[464]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2100' ifindex: 4)
Jun 21 14:31:44 BlackBox kernel: [   31.140096] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun 21 14:39:39 BlackBox kernel: [   21.183554] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jun 21 14:39:40 BlackBox NetworkManager[479]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 21 14:39:41 BlackBox kernel: [   23.897669] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Jun 21 14:39:41 BlackBox kernel: [   23.897676] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Jun 21 14:39:42 BlackBox kernel: [   24.171530] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jun 21 14:39:42 BlackBox kernel: [   24.172853] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Jun 21 14:39:42 BlackBox NetworkManager[479]: <error> [1308659982.762027] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jun 21 14:39:42 BlackBox NetworkManager[479]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2100' ifindex: 4)
Jun 21 14:39:44 BlackBox kernel: [   26.090853] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun 21 14:39:47 BlackBox kernel: [   29.316407] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jun 21 14:40:27 BlackBox NetworkManager[479]: <warn> bluez error getting default adapter: No such adapter

```

At 14:31 I started my system and connected to a wireless network.
At 14:39 my system froze...
At 14:40 I logged into my system after a reset...

This messages tell me that there is some problem with the kernel and there are problems in getting the physical MAC-address of my wireless card.
But... I didn't change it...

Thanks for the links I'm gonna look for a solution for it, but if you or somebody other finds a solution I would be very glad if it would get postet here.

Thank you very much!!

---

### Post by chili555 on 2011-06-21
> (eth1): unable to read permanent MAC address (error 0)I doubt that's a real issue. I have seen this a few times before, last week, in fact. However, your wireless card proceeds normally and connects. The system sees and can read what I assume is a proper MAC address:> *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: [COLOR="Red"]00:0c:f1:5f:10:75[/COLOR]
       width: 32 bitsJust out of curiosity, you might check for the sticker on the bottom of your T41 and see if the MAC address is still shown and correct.

I assume DISABLED is because Fn+F5 has it turned off. The wireless radio consumes a fair amount of power and emits heat, so I wouldn't rule out heat as an issue. Let's see:```
sudo cat /var/log/syslog | grep -i error
sudo cat /var/log/syslog | grep -i acpi
sudo cat /var/log/syslog | grep -i <your_video_driver>
```Find your video driver in:```
sudo lshw -C display
```

---

### Post by superduperlinuxperson on 2011-06-21
sorry to interrupt, but i can see that it says network Disabled, which can only mean two things: 1, that you have it disabled by a hardware and/or key combination, or 2, that it is disabled from the menu (the icon on the top).
thanks

---

### Post by tgalati4 on 2011-06-21
Probably a bad motherboard.  Flexing, age, and bad soldering.  Try using a network cable.

---

### Post by shredIt on 2011-06-22
I disabled the wireless card and connected to the internet by an umts memory stick, because otherwise my system freezes after a few minutes.

If I connect via 802.3 (cable) the system is running fine...

The mac address shown in the logs is correct and it doesn't seem that heat is the problem...

This system workes without problems the last three years and it has got this errors just after upgrading to Ubuntu 11.04.

By the way I haven't found a solution until now... :-(

---

### Post by wildmanne39 on 2011-06-22
> **shredIt said:**
> I disabled the wireless card and connected to the internet by an umts memory stick, because otherwise my system freezes after a few minutes.

If I connect via 802.3 (cable) the system is running fine...

The mac address shown in the logs is correct and it doesn't seem that heat is the problem...

This system workes without problems the last three years and it has got this errors just after upgrading to Ubuntu 11.04.

By the way I haven't found a solution until now... :-(
Hi, here is a link on freezing issues, I hope it helps.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by shredIt on 2011-06-22
Thanks for the link, I'm gonna try an earlier kernerl version in about half an hour.
I'm also gonna paste the results in here.

I recognized in the meanwhile that the firmware for ipw2100 isn't any more in the standard repositories of Ubuntu. In 10.10 there was a package called something like firmware-ipw2100 and this doesn't exist in the repositories of 11.04 any more.

Maybe the support for this chipset is outdated?!?

---

### Post by wildmanne39 on 2011-06-22
> **shredIt said:**
> Thanks for the link, I'm gonna try an earlier kernerl version in about half an hour.
I'm also gonna paste the results in here.

I recognized in the meanwhile that the firmware for ipw2100 isn't any more in the standard repositories of Ubuntu. In 10.10 there was a package called something like firmware-ipw2100 and this doesn't exist in the repositories of 11.04 any more.

Maybe the support for this chipset is outdated?!?
Hi, most problems with freezing in natty can be fixed on the link I gave you, but however you do it I hope it helps.

---

### Post by chili555 on 2011-06-22
> **shredIt said:**
> Thanks for the link, I'm gonna try an earlier kernerl version in about half an hour.
I'm also gonna paste the results in here.

I recognized in the meanwhile that the firmware for ipw2100 isn't any more in the standard repositories of Ubuntu. In 10.10 there was a package called something like firmware-ipw2100 and this doesn't exist in the repositories of 11.04 any more.

Maybe the support for this chipset is outdated?!?The firmware is now contained in a package called linux-firmware. I strongly suspect that if your card is working, the linux-firmware package is installed. You could try to reinstall it:```
sudo apt-get install --reinstall linux-firmware
```You could also try the compat-wireless package:  [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

If you'd like to try, it is a bit more involved than simply apt-get install; I'd be happy to guide you through the process.

Generally when support dies for a driver, it is removed entirely. I am surprised at all this. I have a perfectly operating ipw2200 right here!

---

