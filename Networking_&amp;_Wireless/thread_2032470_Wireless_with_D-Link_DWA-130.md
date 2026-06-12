---
title: "Wireless with D-Link DWA-130"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by TimmyK. on 2012-07-23
It's on the [list of USB wireless cards with Linux compatibility]("http://linuxwireless.org/en/users/Devices/USB"), but I'm not exactly sure how to go about installing the drivers. Help? Thanks.

---

### Post by chili555 on 2012-07-24
The link you gave s refers to DWA-130 [COLOR="Red"]rev B[/COLOR]. Is that what you have? Please open a terminal, insert the device and run and post:```
lsusb
```How to install the driver will depend on your Ubuntu version:```
lsb_release -d
```In future posts, more information is better than less, please.

---

### Post by TimmyK. on 2012-07-24
lsusb =

```
Bus 002 Device 003: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
```

The release is Ubuntu Studio 12.04 LTS.

---

### Post by chili555 on 2012-07-24
> ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]In 12.04, this works with the module r8712u. Let's load it and see what the message logs have to tell us:```
sudo modprobe r8712u
dmesg | grep 8712
iwconfig
```Thanks.

---

### Post by TimmyK. on 2012-08-02
I typed that in and it doesn't seem to do anything. One other update, I don't know if this is important or not, but it actually worked for a few days, then just decided to die for some reason.

---

### Post by praseodym on 2012-08-03
Can you please try an earlier kernel?

---

### Post by chili555 on 2012-08-03
> **TimmyK. said:**
> I typed that in and it doesn't seem to do anything. One other update, I don't know if this is important or not, but it actually worked for a few days, then just decided to die for some reason.Let's dig a bit deeper:```
sudo modprobe r8712u
dmesg | grep -i rtl
```Thanks.

---

### Post by TimmyK. on 2012-08-11
First one just made me enter a password, second one said:

```

[   1.767844] 8139too 0000:00:12.0: eth0: RealTek [COLOR="Red"]RTL[/COLOR]8139 at 0xa000, 00:e0:18:8
6:05:64, IRQ 17
[   26.548710] r8712u: register [COLOR="Red"]rtl[/COLOR]8712_netdev_ops to netdev_ops
[   35.951178] r8712u: Loading firmware from "[COLOR="Red"]rtl[/COLOR]wifi/[COLOR="red"]rtl[/COLOR]8712u.bin"

```

---

### Post by chili555 on 2012-08-14
Please try:```
sudo su
echo r8712u >> /etc/modules
exit
```Reboot with the D-Link inserted and let's take a look at your message log:```
dmesg > timmy.txt
zip timmy.zip timmy.txt
```Look in your user directory for the file timmy.zip and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by TimmyK. on 2012-08-14
None of them work, except for the last one. It reads:
```
  adding: annette.txt (deflated 72%)
```(This isn't my computer, it's my mum's, so the username is different).

One other thing, it works for a few minutes after every reboot.

Thanks for the help.

---

### Post by chili555 on 2012-08-15
They all worked. When you issue a command in Linux and nothing is returned, it generally means, roughly, 'command executed and there are no errors or warnings to report.' That's exactly what you want and, I gather, exactly what you got.

I asked that the file be named *timmy* so that I could related it to your specific case in my *Forum* folder on my desktop currently containing about 3 Gb of items. 

So where is the zip file I asked you to attach?

---

### Post by TimmyK. on 2012-08-20
Oh, I see, they're commands. I thought they were to get information. Anyway, here's the zip.

---

### Post by chili555 on 2012-08-20
> [   33.234288] Registered led device: rt2500pci-phy0::radio
[   33.234390] Registered led device: [COLOR="Red"]rt2500pci[/COLOR]-phy0::quality
[   33.251628] [COLOR="Red"]r8712u[/COLOR]: DriverVersion: v7_0.20100831
[   33.251687] r8712u: register rtl8712_netdev_ops to netdev_ops
[   33.251694] r8712u: USB_SPEED_LOW with 4 endpoints
[   33.264153] r8712u: Boot from EFUSE: Autoload OKDo you have two wireless devices fighting for control and undoubtedly conflicting? Why?

---

### Post by TimmyK. on 2012-08-22
OK, that would be the source of our problems! I forgot I still had a PC-i wifi card. It seems to be working now, but it's worked for a while and quit before, so I'm not sure if it's fixed yet. Thanks for the help!

---

### Post by chili555 on 2012-08-22
> **TimmyK. said:**
> OK, that would be the source of our problems! I forgot I still had a PC-i wifi card. It seems to be working now, but it's worked for a while and quit before, so I'm not sure if it's fixed yet. Thanks for the help!We can always blacklist its driver and, once the conflict is out of the way, your USB will probably work fine. Post back if you need more help.

---

### Post by praseodym on 2012-08-22
Check this udev rule:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace "b43" twice with "rt2500pci" in that script

---

