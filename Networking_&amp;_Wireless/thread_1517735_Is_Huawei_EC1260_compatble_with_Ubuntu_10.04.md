---
title: "Is Huawei EC1260 compatble with Ubuntu 10.04?"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by jre6 on 2010-06-25
I currently use Ubuntu 9.04. I have thought of upgrading to 10.04 for a long time, but I am unable to do so as I do not know if my mobile broadband device, Huawei EC1260, works out of the box in 10.04. In the [Ubuntu wiki]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G"), I found that it was not compatible with 9.10 and a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") had been already filed. A line is mentioned in the page, which tells us:

>  Declined  for Lucid  by Jeremy FosheeSo, does this mean that the problem is fixed in 10.04? Or, if it is incompatible, then, how will I configure it so that it can work?

Now, many people may be considering that I might just download the CD image and try it out. Although my company has given me the device with 5 GB of free usage, but I have to show reasons for any file downloaded more than 15 MB, so I am helpless.

Please help. I am desperate searching for an answer, and Google has disappointed me.

---

### Post by pdc on 2010-06-26
what does 

> lsusb


give you for this device?

---

### Post by jre6 on 2010-06-26
As I have not upgraded to Lucid yet, it is very difficult for me to give the output of lsusb. But, according to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146"), the device is detected (in Karmic) and the lsusb output (for Huawei E620, another dongle which didn't work in Karmic) is:

```

Bus 005 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

```

[According to Hardik Dalwadi]("http://hardik.in/2010/03/20/ubuntu-9-10-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-of-the-box/"), this is due to a bug in modem manager.

Could you devise a way to do it without the PPA? The PPA will take help of the Internet connection to download the required packages, and I do not have any other method to connect.

---

### Post by pdc on 2010-06-26
> As I have not upgraded to Lucid yet, *it is very difficult for me to give the output of lsusb*.

My understanding is that lsusb gives the identity of the device, so it should not change whatever version of ubuntu (or fedora) you run ..

so you have a very standard Huawei modem that should run just fine; 

Karmic (9.10) had various mobile broadband problems: **my impressio**n is that 10.04 is working very well with mobile broadband

---

### Post by jre6 on 2010-06-27
Well, this is what appears for lsusb in Jaunty when Huawei EC1260 is connected with the machine :

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by jao_madn on 2010-06-27
Well my huawei E169U works fine in ubuntu 10.04 no PPA required..

---

### Post by jre6 on 2010-07-02
Sorry for my extremely late response, I am presently very very busy.

Is there any way I can make it work in Karmic?

---

### Post by pdc on 2010-07-02
> can I make it work in Karmic?

... can you ? who knows .........

---

### Post by jre6 on 2010-07-03
> **pdc said:**
> ... can you ? who knows .........

No, I can't, and that is why I have posted the question.

The forum isn't the place for misbehaviour :mad:

**I would expect a better response henceforth. **

---

### Post by jre6 on 2010-07-03
Can anyone do [this]("http://hardik.in/2010/03/20/ubuntu-9-10-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-of-the-box/") without the PPA? It reportedly works.

---

### Post by jre6 on 2010-07-05
Well, it works in Karmic without any modification, contrary to what the link posted above says. It should work in the same manner in Lucid. If it doesn't work, see the link.

---

