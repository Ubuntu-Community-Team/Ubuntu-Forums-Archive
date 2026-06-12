---
title: "intel 3945 wireless driver is incompatible with 9.10"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by zachzach on 2010-04-10
I installed Ubuntu 9.10 three months ago on my PC after having some bad experiences with Windows viruses.

As of a few days ago (probably right after some update, although I do not pay close attention to my updates) my wireless stopped working for encrypted networks. It connects fine to unsecured networks, and when I reboot in Windows the wireless works perfectly on encrypted networks. So the issue is certainly just my computer in Ubuntu on encrypted networks.

I have searched around and found that many people have faced the same issue with my wireless driver: Intel 3945. This issue has been reported as a bug many times over the years for people with Intel 3945 wireless driver.

I installed wicd and it does not make a difference.

This bug has been reported many times over the years and so I don't think my report will change anything, especially not in the short term.

I have really enjoyed using Linux these past few months but don't see how I can continue doing so without Internet.

Should I reinstall Ubuntu from the original CD I had and just never update? Is it feasible to use Ubuntu long-term without ever updating?

Should I give up trying to use Ubuntu on this laptop with this wireless driver? I would rather put up with Windows and its problems instead of using Ubuntu if Ubuntu can't even get me online. But I like Ubuntu and will stick with it if anyone can point me to a solution.

Thanks.

---

### Post by Thomy23 on 2010-04-10
Where exactly is the bug filed, can you give me some URLs (Launchpad prefered)?

---

### Post by zachzach on 2010-04-11
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434342](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434342)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/559290](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/559290)

I'm not an expert on these things so I cannot tell for sure whether this is the same problem as mine, but it seems like it, and when I type in my wireless driver name it comes up many times as a bug.

Can someone instruct me on how to report this bug properly?

---

### Post by chili555 on 2010-04-11
I don't believe the card is incompatible with 9.10, nor with WPA. I am using it right now perfectly. If you are ready to do some troubleshooting, let's see:```
rfkill list
dmesg | grep iwl
```

---

### Post by zachzach on 2010-04-18
my apologies for the very late reply. i have had little time to take my computer somewhere with an unsecured wireless network.

i entered those commands and here is what it says:

zachary@zachary-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
zachary@zachary-laptop:~$ dmesg | grep iwl
[   19.724442] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.724446] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.724586] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.724602] iwl3945 0000:05:00.0: setting latency timer to 64
[   19.799173] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   19.799179] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.799335] iwl3945 0000:05:00.0: irq 27 for MSI/MSI-X
[   19.811878] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.619663] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   22.714568] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   22.810006] Registered led device: iwl-phy0::radio
[   22.810032] Registered led device: iwl-phy0::assoc
[   22.810092] Registered led device: iwl-phy0::RX
[   22.810113] Registered led device: iwl-phy0::TX
[   53.560220] Registered led device: iwl-phy0::radio
[   53.560299] Registered led device: iwl-phy0::assoc
[   53.560334] Registered led device: iwl-phy0::RX
[   53.560368] Registered led device: iwl-phy0::TX

---

### Post by chili555 on 2010-04-18
You might try:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=0
```Now try an encrypted network. If this works, we can tweak one file and make it permanent.

---

### Post by zachzach on 2010-04-18
I entered the codes..

zachary@zachary-laptop:~$ sudo rmmod -f iwl3945
[sudo] password for zachary: 
zachary@zachary-laptop:~$ sudo modprobe iwl3945 swcrypto=0
zachary@zachary-laptop:~$ 

It didn't display anything to tell me what was going on, but I assume that was expected. I will try an encrypted network when I get home, and will report back, but for now I just want to make sure that the terminal commands and lack of output look like they are supposed to.

---

### Post by chili555 on 2010-04-18
> the terminal commands and lack of output look like they are supposed to.Exactly correct. The lack of response means, roughly, 'command accepted and there are no errors or warnings to report.' Let us know how you connect.

---

### Post by zachzach on 2010-04-20
No luck. I tried both a WPA and a WEP network.

In both cases it tries for a few minutes and eventually reads: "Connection Failed: Unable to Get IP Address". 

By the way, I am connecting through Wicd Network Manager, not the program that came with the system, not that this should matter (I switched to Wicd once this problem had already started).

---

### Post by zachzach on 2010-04-26
If nobody has any additional advice on this, can someone help me to properly report this bug on Launchpad? I am not experienced on linux and have never reported anything, but from my perusing the launchpad site it seems they are always asking for extra particular info and i want to get it right so hopefully this can get fixed.

---

### Post by chili555 on 2010-04-27
Let's try a different driver parameter. These steps are temporary; upon reboot they will be lost. If it works, we can write a conf file to make it permanent. Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```I am not sure there is any best way to report a bug; just tell them the symptoms and what you have tried so far. You just need to register at launchpad and post it.

You may find out that the bug is actually Network Manager.

I am quite mystified; my 3945ABG connects immediately to unencrypted, WEP or WPA networks. It does so with NM, Wicd or manual configuration.

---

### Post by zachzach on 2010-04-30
Still having the problem: unable to get IP address.

I also had no problems with this wireless driver for the first several months running Ubuntu. It stopped working for no apparent reason.

I am now using Wicd, which has failed just the same as Network Manager.

---

