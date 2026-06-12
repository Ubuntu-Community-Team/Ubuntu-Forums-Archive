---
title: "Plz help if not ill loose my job.ipw2200BG problem"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by l3east on 2009-03-14
Well my job laptop that the comapn owns wasmessed up.And i asked permision to fix it.Then i installed ubuntu.t when i installed it te ipw2200Bg wireless card wasent working.It dint even been reconized by iwconfig or iwconfig.And i told the problem about it.And he said if i dont fix it my job is on the line (hes an *** by the way).Can someone plz help me.:(

---

### Post by kestrel1 on 2009-03-14
What is the output from:```
ifconfig
```
and ```
lspci
```

---

### Post by l3east on 2009-03-14
By the way i have a HP Compaq nc6230


ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:14:38:17:2e:07  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:38ff:fe17:2e07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1173603 (1.1 MB)  TX bytes:172959 (172.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

```

 lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
junior@ubuntu:~$ 


```

---

### Post by kestrel1 on 2009-03-14
Can't see that the wireless is installed.
Normally the HP NC & NX series laptops have either an Intel wireless card or a Broadcom. Both of these work, no problem.
Do you know what wireless card you have. There is a cover on the bottom of the laptop that has a single cross head screw. If you remove that you will probably see a memory module or an empty module slot & the wireless card with a black & a white cable attached to it. What does the label on it say?

---

### Post by l3east on 2009-03-14
Um can u show me this part thru a picture or something.Sorry im a noob.kinda lost

---

### Post by kestrel1 on 2009-03-14
Just looked at the service manual for your model & it is different to the NC & NX machines I have repaired & appears you have to take a lot of the machine apart to see the card. I wouldn't suggest you do that.
Having also looked on the HP site this model should have either the Intel PRO Wireless card or the Broadcom card that I mentioned. Are you certain that the wireles card is in the machine, because if so it should be showing up unless the card has gone faulty.
I know some companies remove wireless cards from staff laptops, why I do not know.

---

### Post by l3east on 2009-03-14
I was cheking the site and evrything and it does come with it.thats weird .i think img onna have a look inside.

---

### Post by kestrel1 on 2009-03-14
Get the service manual first then: [http://bizsupport2.austin.hp.com/bc/docs/support/SupportManual/c00622160/c00622160.pdf](http://bizsupport2.austin.hp.com/bc/docs/support/SupportManual/c00622160/c00622160.pdf)

---

### Post by fixitdude on 2009-03-14
I don't know if ubuntu installs all the wireless stuff by default.

Go to System > Synaptic then search for "wireless" and install at least "wireless tools" "wlassistant" "linux-wlan-ng" and a few others you think you may need. Those should install other libraries and modules you may need.

Then power off and boot fresh.

I don't know what your particular card needs but you should search with the card type and "ubuntu" as keywords on google and read up on what it needs. Some cards may need the "ndiswrapper" stuff so you can run the windows drivers for them.

Also, I think you wanted to do a "ifconfig -a" so it shows all interfaces, not just the ones that are up.

And don't just think all that in the "lspci -v" and other listings is just a bunch of confusing junk because all you did was skim over it, read it and you may start to understand what it all means. Mostly the hardware that ubuntu thinks is there, so look for your wireless card.

There's also a hardware listing in "Kinfocenter", look there too if you are using KDE.

Next time, try ubuntu on your own stuff, or old stuff and be better at it before you go offering to fix stuff.

---

### Post by kestrel1 on 2009-03-15
Ubuntu does install wireless bt default if the drivers are available. I have recently re-installed my HP Compaq NX6110 & was up & running in no time. If the card is actually installed in the machine it should work out of the box, as the model of laptop you have takes the same cards as the NX6110 & NC6120.
ndiswrapper is not required for the Intel Pro or the Broadcom cards that come with these machines. The Broadcom is a better card though.

---

### Post by ugm6hr on 2009-03-15
> **l3east said:**
> Well my job laptop that the comapn owns wasmessed up.

How was it messed up?  Was it the wifi?

lspci reports only a LAN card.  ifconfig reports only eth0 (ethernet).

It is likely that this is a hardware issue; either the internal wifi is broken, or the connection has come loose.

---

