---
title: "Connecting to 3G network"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Jesus on 2009-06-29
I've just got an Acer Aspire One and am currently using the bundled distro, Linpus. I tried booting UNR off a flash drive and was very impressed, however there is one barrier before I can install.

I connect to the internet using a 3G modem which connects to an academic network provided by a company called Synetrix. When I plugged it in the first time Linpus brought up a dialog to configure it. All I had to do was type in my APN and I was away (Synetrix doesn't require usernames or passwords or anything else).

When I tried doing the same with UNR it brought up a wizard that gave me a list of ISPs, none of which were the one I wanted. I was able to get past this by choosing one at random, then editing the connection that was created and changing the details. However it insists I provide it with a telephone number to dial. I have no idea what this number would be.

Screenshots of both config tools: [http://omploader.org/vMXdmZA](http://omploader.org/vMXdmZA)

I know basically nothing about 3G so any pointers would be appreciated.

---

### Post by Jesus on 2009-06-30
This may be poor etiquette but I'm gonna have to bump.

---

### Post by Jesus on 2009-07-02
OK after some research I've learned that the *99# number that Ubuntu automatically fills in the field dials the default number stored on the 3G usb stick. I've also learned that *99***1# does the same thing. I've tried both of these and every time I try to connect it just does the little animation that indicates it's trying to connect to a network and then a notification pops up saying "GSM network disconnected - you are now offline."

---

### Post by Hobgoblin on 2009-07-02
> **Jesus said:**
> OK after some research I've learned that the *99# number that Ubuntu automatically fills in the field dials the default number stored on the 3G usb stick. 

It doesn't dial any number, *99# tells it to connect to the default access point (APN).

Check the settings under the IPv4 tab, on mine Method was incorrectly set (after selecting my correct carrier).

---

### Post by Jesus on 2009-07-02
> **Hobgoblin said:**
> It doesn't dial any number, *99# tells it to connect to the default access point (APN).

Check the settings under the IPv4 tab, on mine Method was incorrectly set (after selecting my correct carrier).

Thanks for the response.

I only see two options under Method: Automatic (PPP) and Automatic (PPP) addresses only.

Starting to wonder if maybe it's a driver issue. I'm using an Icon 225 which requires the hso driver. This driver appears to have been integrated into the kernel in 2008. dmesg reports that it's in use in UNR 9.04:

```
[  122.220154] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  122.382271] usb 2-1: configuration #1 chosen from 1 choice
[  122.510331] usb-storage: probe of 2-1:1.0 failed with error -5
[  122.664181] usb 2-1: USB disconnect, address 2
[  124.144141] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  124.307223] usb 2-1: configuration #1 chosen from 1 choice
[  124.320274] usb-storage: probe of 2-1:1.0 failed with error -5
[  124.355860] usb-storage: probe of 2-1:1.1 failed with error -5
[  124.358683] usb-storage: probe of 2-1:1.2 failed with error -5
[  124.408701] hso: /build/buildd/linux-2.6.28/drivers/net/usb/hso.c: 1.2 Option Wireless
[  124.410386] hso0: Disabled Privacy Extensions
[  124.412290] usbcore: registered new interface driver hso
```

---

### Post by Jesus on 2009-07-03
I've finally found the solution, and it's annoyingly simple.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325)

Even if your provider doesn't require a username and password, NetworkManager will fail to authenticate if the fields are empty (this feels like a bug to me).

The solution is to put nonsense values in these fields and the problem goes away. I'm now ready to install UNR on my netbook!

---

