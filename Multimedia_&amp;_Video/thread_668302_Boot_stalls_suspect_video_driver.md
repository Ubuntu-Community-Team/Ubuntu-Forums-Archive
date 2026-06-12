---
title: "Boot stalls: suspect video driver"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by trappleye on 2008-01-15
I've been running Ubuntu 7.10 for the last 4 months or so on my HP DV9000 with no big issues till I installed the recommended updates (I don't remember what they were). After the requested system reboot it shutdown properly but got stuck on the reboot. I wasn't sure what was going on, the orange status bar just stopped. Alt+F1 didn't do anything so I did a Hard reboot and this time entered recovery mode. Again, the system stalled at the "Loading Hardware Drivers" prompt. I tried Ctrl+c to get past it but it didn't have any effect. After rebooting 4 times trying different things it just came up good. Then on the next reboot it got hung up again in the same place!! So I ran a few tests. On 25 reboots to recovery mode it came up 5 times without stalling, and got hung up 20 times. And on 25 reboots to X (normal boots) it only came up 3 times, and hung up 22 times. I didn't change anything between attempts. And when I say hung up it NEVER comes up. I even let it sit overnight. It boots to Windows every time without problem. What is wrong??? I suspect the video driver isn't getting initialized. I am running envy because I have an envidia video card. the next time I can successfully boot I would like to look at some kind of log, but don't know where to look. ANY help is greatly appreciated. 

I have a HP DV9205us:

- 1.6 GHz AMD Turion 64 X2 TL-50 dual-core processor
- 120 GB hard drive,
- 2 GB installed RAM (I upgraded from the 1GB stock.
- multi-format/dual-layer LightScribe DVD drive
- 54g Wi-Fi LAN (802.11b/g), 10/100 Ethernet
- Nvidia GeForce Go 6150 video card with up to 288 MB shared memory
- Pre-installed with Windows Vista Home Premium (with Media Center capabilities)

---

### Post by Waappu on 2008-01-15
> **trappleye said:**
> I've been running Ubuntu 7.10 for the last 4 months or so on my HP DV9000 with no big issues till I installed the recommended updates (I don't remember what they were). After the requested system reboot it shutdown properly but got stuck on the reboot. I wasn't sure what was going on, the orange status bar just stopped. Alt+F1 didn't do anything so I did a Hard reboot and this time entered recovery mode. Again, the system stalled at the "Loading Hardware Drivers" prompt. I tried Ctrl+c to get past it but it didn't have any effect. After rebooting 4 times trying different things it just came up good. Then on the next reboot it got hung up again in the same place!! So I ran a few tests. On 25 reboots to recovery mode it came up 5 times without stalling, and got hung up 20 times. And on 25 reboots to X (normal boots) it only came up 3 times, and hung up 22 times. I didn't change anything between attempts. And when I say hung up it NEVER comes up. I even let it sit overnight. It boots to Windows every time without problem. What is wrong??? I suspect the video driver isn't getting initialized. I am running envy because I have an envidia video card. the next time I can successfully boot I would like to look at some kind of log, but don't know where to look. ANY help is greatly appreciated. 

I have a HP DV9205us:

- 1.6 GHz AMD Turion 64 X2 TL-50 dual-core processor
- 120 GB hard drive,
- 2 GB installed RAM (I upgraded from the 1GB stock.
- multi-format/dual-layer LightScribe DVD drive
- 54g Wi-Fi LAN (802.11b/g), 10/100 Ethernet
- Nvidia GeForce Go 6150 video card with up to 288 MB shared memory
- Pre-installed with Windows Vista Home Premium (with Media Center capabilities)

Hi

This is know "issue". If you manage boot, see if this helps

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

