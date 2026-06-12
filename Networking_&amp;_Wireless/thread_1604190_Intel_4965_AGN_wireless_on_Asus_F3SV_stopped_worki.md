---
title: "Intel 4965 AGN wireless on Asus F3SV stopped working (Ubuntu 10.4)"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by benmann on 2010-10-23
Description:
My wireless worked out of the box for the past few months.  When I was running low on battery recently, I put the laptop to sleep.  When I woke it up, there was a black screen with a flashing underscore.  I pressed a bunch of buttons but nothing happened.  Then suddenly it said something about a wireless hardware error and I did a hard reset by holding down the power button.  When I turned the computer back on, wireless was greyed out.  There's no hardware switch to enable and disable wireless and the software switch had no effect.  I tried echoing into the 'state' of the adapter but it didn't let me.  When I tried sudo ifconfig wlan0 up it gave me the following error:
```
 
SIOCSIFFLAGS: Unknown error 132

```

lspci: 
```

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61) 
```

iwconfig wlan0:
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

ifconfig -a:
```

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:70:47:df  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lsmod | grep iw:
```

iwlagn                122996  0 
iwlcore               125179  1 iwlagn
mac80211              238896  2 iwlagn,iwlcore
led_class               3764  3 iwlcore,sdhci,asus_laptop
cfg80211              148725  3 iwlagn,iwlcore,mac80211

```


dmesg | grep iw:
```

[   11.352049] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.352051] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.352137] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.352149] iwlagn 0000:03:00.0: setting latency timer to 64
[   11.352196] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.400841] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.400975] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   13.626852] phy0: Selected rate control algorithm 'iwl-agn-rs'

```

iwlist scan | grep wlan0:
wlan0     Failed to read scan data : Network is down

lsb_release -d
Description:	Ubuntu 10.04.1 LTS

uname -mr
2.6.32-25-generic x86_64

sudo /etc/init.d/networking restart
```

[sudo] password for ben: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

---

### Post by Jerazol on 2011-01-11
Don't know if you've figured out this problem yet, but at least for others finding this thread. Suspending the machine and waking up again seems to sort it out. Probably some sort of bug with the suspend/resume routines, when the machine is suspended, but not resumed as expected.

---

### Post by neontiger2011 on 2011-05-17
> **Jerazol said:**
> Don't know if you've figured out this problem yet, but at least for others finding this thread. Suspending the machine and waking up again seems to sort it out. Probably some sort of bug with the suspend/resume routines, when the machine is suspended, but not resumed as expected.

I should raise a tribute to you, man.
I f*cking tried everything at my reach to make it work, then when I've read what you said I remembered that my wireless stopped to work in the very moment I had to hard-reboot my PC after a failed wakeup.

Then I tried everything, removing and reinstalling modules, filtering through all the boottime information, active modules, tried to switch USB ports, tried to boot other kernel versions.... whatever I could think of...

Then, as you suggested, I suspended to RAM then woke it up, and then suddendly my wireless started working again as If I gave it a b*tchslap...

Man, it may sound ridiculous but, you saved me. Hahaha.



Thank you very much for your help,
and sorry for my bad English.


Regards from Argentina,
Leo.

---

