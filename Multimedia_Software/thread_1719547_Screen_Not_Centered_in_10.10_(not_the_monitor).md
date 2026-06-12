---
title: "Screen Not Centered in 10.10 (not the monitor)"
date: 2011-04-01
forum: Multimedia Software
---

### Post by Emor8t on 2011-04-01
I do love upgrading.

I have a old HP Pavilion a000 - it has onboard video, of what variety I'm not to sure. It worked fine under 10.06 but I had the genius idea to upgrade. Now I have an empty xorg.conf file and the screen isn't centered on the monitor - the monitor hardware buttons don't go far enough to adjust it.

Any ideas?

---

### Post by wolfen69 on 2011-04-01
Post the output of 
```
lspci
```

Yeah, the upgrade process can be iffy sometimes. Better to clean install.

---

### Post by Emor8t on 2011-04-02
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]




I guess I should say I did a clean install.

I should also add that the monitor is 1920.1080 and the max res I ever got out of the onboard video was 1400x1050 - I'm cool with that. I just prefer it to fill the entire monitor.

---

### Post by Emor8t on 2011-04-02
Am I looking at this right - [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

Via doesn't currently support 10.10 and that maybe I should downgrade to 10.04 in order to fix this?

---

### Post by wolfen69 on 2011-04-02
You have a Savage card which I've heard can be problematic. I've never had one, but maybe someone else can help.

---

### Post by gordintoronto on 2011-04-02
What monitor? Some monitors have an "auto" setting in the menus, which usually fixes things right up.

You might find that buying a cheap ATI or Nvidia video card on eBay simplifies your life a great deal. I spent $10 to have a real video card rather than on-board VIA. It still doesn't support compiz, but it works great.

---

