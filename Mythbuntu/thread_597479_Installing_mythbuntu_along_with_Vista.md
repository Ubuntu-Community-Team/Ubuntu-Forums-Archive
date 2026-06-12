---
title: "Installing mythbuntu along with Vista"
date: 2007-10-30
forum: Mythbuntu
---

### Post by cooldudeny on 2007-10-30
I want to try out mythbuntu for live tv purposes coz mce is crap and i heard good things about mythbuntu 

i want to know if i can install it on a machine running windows vista and if my tv tuner card will work 

tv tuner: pinnacle pctv HD card 

please advice

---

### Post by Lem on 2007-10-30
Mythtv will only run on linux. However, Mythbuntu is available as an ISO with the relevant Ubuntu bits built in - you could dual boot Mythbuntu/Vista.

---

### Post by cooldudeny on 2007-10-30
> **Lem said:**
> Mythtv will only run on linux. However, Mythbuntu is available as an ISO with the relevant Ubuntu bits built in - you could dual boot Mythbuntu/Vista.

Do you know if my pinnacle tv tuner will work with it when i do that

---

### Post by Lem on 2007-10-31
Is it the USB stick? Don't know much about these cards as I'm in the UK where the service is different.

I know the Homerun HD is very popular in the US for mythtv.

---

### Post by cooldudeny on 2007-11-09
> **Lem said:**
> Is it the USB stick? Don't know much about these cards as I'm in the UK where the service is different.

I know the Homerun HD is very popular in the US for mythtv.

No it is PCI card

---

### Post by superm1 on 2007-11-10
Boot up the live disk and see what the device identifies as.  Nothing will be done to your computer until you install, so booting the livedisk is perfectly safe.

It can be hit and miss depending upon the model number and some more.

If you are new to linux, you will unfortunately have to type a command in the terminal to get this information. (Most of the other stuff in mythbuntu is GUI based though)

When you boot up the live disk, click the Applications menu and find the Terminal item in it.

In the terminal type```
lspci
```

Highlight all the output from lspci, copy it to the clipboard and open up firefox from the livedisk and paste it here.  We can see if we can help figure out if that tuner is supposed to be working.

---

### Post by cooldudeny on 2007-11-10
> **superm1 said:**
> Boot up the live disk and see what the device identifies as.  Nothing will be done to your computer until you install, so booting the livedisk is perfectly safe.

It can be hit and miss depending upon the model number and some more.

If you are new to linux, you will unfortunately have to type a command in the terminal to get this information. (Most of the other stuff in mythbuntu is GUI based though)

When you boot up the live disk, click the Applications menu and find the Terminal item in it.

In the terminal type```
lspci
```

Highlight all the output from lspci, copy it to the clipboard and open up firefox from the livedisk and paste it here.  We can see if we can help figure out if that tuner is supposed to be working.

sure i am downloading the mythbuntu and will update you on the results because i heard people are really happy with it and i will like to use it since the bundled in application for windows on my tv tuner card is no use it is waste of time

---

### Post by cooldudeny on 2007-11-11
> **superm1 said:**
> Boot up the live disk and see what the device identifies as.  Nothing will be done to your computer until you install, so booting the livedisk is perfectly safe.

It can be hit and miss depending upon the model number and some more.

If you are new to linux, you will unfortunately have to type a command in the terminal to get this information. (Most of the other stuff in mythbuntu is GUI based though)

When you boot up the live disk, click the Applications menu and find the Terminal item in it.

In the terminal type```
lspci
```

Highlight all the output from lspci, copy it to the clipboard and open up firefox from the livedisk and paste it here.  We can see if we can help figure out if that tuner is supposed to be working.

Hi i did as you said and this is the terminal screen i am pasting here 

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:02.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:02.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:02.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
ubuntu@ubuntu:~$

---

