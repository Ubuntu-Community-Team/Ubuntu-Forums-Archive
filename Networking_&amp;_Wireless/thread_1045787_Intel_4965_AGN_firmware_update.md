---
title: "Intel 4965 AGN firmware update"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by EateryOfPiza on 2009-01-20
Hello, using 8.10 intrepid here.

I'm being affected by an issue that was reported against the iwlagn driver on both [kernel.org](http://bugzilla.kernel.org/show_bug.cgi?id=11983) and at the [Intel Linux Wireless site](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1703). Intel has released a microcode update that solves this issue, version 228.57.2.23, and I see it has been merged into the Ubuntu's linux-firmware package [version 1.3](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-firmware/linux-firmware_1.3/changelog).

From what I can tell, v1.3 of linux-firmware will only be released for Jaunty. Am I wrong and will it be released for Intrepid? If it will not, then is there a way to get the updated package on Intrepid?

Thanks

---

### Post by EateryOfPiza on 2009-01-21
Okay, here is what I did to update the Intel firmware. Can somebody tell me if this was the right procedure, or did I hose my system?

1. Download the latest firmware from Intel's site ([http://www.intellinuxwireless.org/?n=downloads&f=ucodes_4965](http://www.intellinuxwireless.org/?n=downloads&f=ucodes_4965)) and extract it somewhere. I wanted version 228.57.2.21.
```
cd ~/Public
wget http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.2.23.tgz
tar xzvf iwlwifi-4965-ucode-228.57.2.23.tgz
```

2. Copy the old firmware someplace safe. I happened to have the iwlwifi-4965-ucode-228.57.2.21 firmware installed.
```
mkdir ~/Public/iwlwifi-4965-ucode-228.57.2.21
cp /lib/firmware/iwlwifi-4965-2.ucode ~/Public/iwlwifi-4965-ucode-228.57.2.21
```

3. Unload the driver.
```
sudo modprobe -v -r iwlagn
```

4. Replace the old firmware with the new firmware
```
sudo cp ~/Public/iwlwifi-4965-ucode-228.57.2.23/iwlwifi-4965-2.ucode /lib/firmware/
```

5. Reload the driver.
```
sudo modprobe -v iwlagn
```

I'll post later and report if it resolves my issues.

---

### Post by chadk on 2009-01-29
It's later... did it resolve your issues?

---

### Post by EateryOfPiza on 2009-01-29
Nope, but seems a new kernel got pushed out yesterday which had a new compat-wireless stack, and I've had no problems since.

---

### Post by jivica on 2009-02-03
ok so is the only solution to get 4965 AGN to get the new kernel and recompile it?

Please if you can elaborate what you did to make it work
Thanks in advance!!

---

### Post by EateryOfPiza on 2009-02-03
The new microcode did help, but the thing that solved it for me was upgrading to 2.6.27-11-generic and also installing linux-backports-modules-intrepid.

---

### Post by jivica on 2009-02-04
Well I did get new updated kernel 2.6.27-11-generic + backports but still no luck on my HP 8710w laptop.. Think that HW RF Kill switch could be the problem...
If you have any idea, please!!!
Ivica


 2.6.27-11-generic #1 SMP Tue Jan 27 23:53:21 UTC 2009 x86_64 GNU/Linux
[  480.733507] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[  480.733511] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[  480.733616] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  480.733638] iwlagn 0000:10:00.0: setting latency timer to 64
[  480.733673] iwlagn 0000:10:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  480.770693] iwlagn 0000:10:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[  480.772678] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  525.398793] firmware: requesting iwlwifi-4965-2.ucode
[  525.402349] iwlagn 0000:10:00.0: loaded firmware version 228.57.2.23
[  525.402469] iwlagn 0000:10:00.0: Radio disabled by HW RF Kill switch
[  525.425234] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by EateryOfPiza on 2009-02-04
For me, that message shows up when I have disabled the wireless using the hardware switch on my T61p. For your HP laptop, there might be a switch or a button you can try to press that will turn on the wireless.

---

### Post by jivica on 2009-02-05
well I do have the button but pressing will only activate or deactivate bluetooth and have nothing to do with wifi...
Wondering if someone have managed to do it at HP 8710w 
thanks anyway
Ivica

---

