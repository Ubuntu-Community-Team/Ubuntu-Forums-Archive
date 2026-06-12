---
title: "netgear adapter install"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by DaMcNugGet on 2013-06-05
Hello, 
I am a new ubuntu and linux user. Right now im on a wired ethernet connection but want to go to wireless. I am on a lenovo desktop. (ubutnu version is 12.04) I have a netgear 3100 netgear wireless adapter. How can i use the adapter? Thanks for all your answers.

---

### Post by varunendra on 2013-06-05
Welcome to the forums DaMcNugGet ! :)

Is it a usb adapter? If yes, please open a terminal (ctrl+alt+T), enter the following command and post back its output here:
```
lsusb
```

If it is an internal adapter, then output of -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, click on # button above the edit box to auto-generate 'Code' tags, then copy-paste the output in-between the tags to preserve its formatting. Thanks.

---

### Post by DaMcNugGet on 2013-06-05
okay give me a few minutes im on a different computer might be a while, also dosent seem its recognizing my adapter is plugged in. its a WNA 3100 netgear usb adapter.

---

### Post by DaMcNugGet on 2013-06-05
okay this is what came out

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 17ef:602d Lenovo 
Bus 002 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 004: ID 05e3:0722 Genesys Logic, Inc.
 
```

---

### Post by varunendra on 2013-06-05
> **DaMcNugGet said:**
> ```

Bus 002 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom **[COLOR="#FF0000"]BCM43231[/COLOR]**]
 
```

Hmm.. unfortunately, this device does not have a linux driver yet. Using the windows driver over ndiswrapper seems to be the only way to make it work. Please see this thread to see how to install ndiswrapper and windows driver : [http://ubuntuforums.org/showthread.php?t=1695036&page=17](http://ubuntuforums.org/showthread.php?t=1695036&page=17)

---

### Post by DaMcNugGet on 2013-06-06
okay thanks for the link. Do you know any drivers that are supported right now that would be an easy install? Thanks for being helpful by the way.

---

### Post by varunendra on 2013-06-06
Like I mentioned, the ndiswrapper thing seems to be the only way to make it work on Linux. If you face any difficulty in following the method given in the linked thread, you can post there or here with details of what you tried and the problem you got. We'd be happy to help accordingly.

---

