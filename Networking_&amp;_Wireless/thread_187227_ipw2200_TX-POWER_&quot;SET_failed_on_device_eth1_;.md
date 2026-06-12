---
title: "ipw2200 TX-POWER &quot;SET failed on device eth1 ; Input/output error.&quot;"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by uldall_ on 2006-06-02
Hi,

I installed drapper drake yesterday, and the wireless connection worked fine in the beginning.

Then at onetime I restarted the computer and i hanged at the "is now restarting" screen were it suddently started to say that it couldn't switch off my wireless card.

After that insident my wireless connection has been broken.

The wireless indicator on my laptop is not led and the radio is turned off. 

I think it has something to do with the "TX-power", but when I try to turn it to auto I get the following error message:
```

$ sudo iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.

```

My dmesg says the following:
```

[4318516.802000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4318516.802000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4318516.802000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4318516.803000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4318516.938000] ipw2200: Radio Frequency Kill Switch is On:
[4318516.939000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

```

Anyone got a solution?

Christian

---

### Post by MrObvious on 2006-06-02
[4318516.938000] ipw2200: Radio Frequency Kill Switch is On:

Hint?

---

### Post by uldall_ on 2006-06-03
But how do I turn it off?

---

### Post by uldall_ on 2006-06-04
I solved it!

I downloaded the acerhk driver from [http://www2.informatik.hu-berlin.de/~tauber/acerhk/]("http://www2.informatik.hu-berlin.de/~tauber/acerhk/")

unpacked it, made a make, then a make install

then restarted and typed:
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled

then restarted, and the wireless worked again!

---

