---
title: "Bluetooth ubuntu X windows XP"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Michalxo on 2009-12-20
Hello all,
 I am experiencing a very interesting "bug?" in ubuntu and XP systems via dualboot. Sometimes I was able to use my BT in ubuntu, probably depended on some luck factor whether it brought up or no. Most times, like now, I was unable to see my BT adapter. 
 
 Today I wanted to use BT (mobile, but my applet responded with "no adapter present" text. After trying different kernels (31-14,31-16, liveCDs Karmic and Lucid Alpha 1), none of them managed to bring up my BT. Finally I decided to try fiddle a bit with BT in my windows XP. I've installed BT driver, paired the phone and restarted back to ubuntu. BT was active. 

 I have to say, that I was able to use BT yesterday via karmic\lucid(?) liveCD without any problems before installing BT drivers in XP. So, can anyone explain to me why does "my" BT acts like the most ridiculous piece of hardware ever?
I've noticed following "dmesg |grep Bluetooth" change:

before installing drivers (not working BT):
```
$ dmesg |grep lueto
[    0.272011] Bluetooth: Core ver 2.15
[    0.272027] Bluetooth: HCI device and connection manager initialized
[    0.272027] Bluetooth: HCI socket layer initialized
[    1.460628] Bluetooth: L2CAP ver 2.13
[    1.460630] Bluetooth: L2CAP socket layer initialized
[    1.460633] Bluetooth: SCO (Voice Link) ver 0.6
[    1.460635] Bluetooth: SCO socket layer initialized
[    1.460678] Bluetooth: RFCOMM TTY layer initialized
[    1.460682] Bluetooth: RFCOMM socket layer initialized
[    1.460692] Bluetooth: RFCOMM ver 1.11

```
and after successful BT bringing up:
```
~$ dmesg |grep lueto
[    0.272011] Bluetooth: Core ver 2.15
[    0.272027] Bluetooth: HCI device and connection manager initialized
[    0.272027] Bluetooth: HCI socket layer initialized
[    1.460628] Bluetooth: L2CAP ver 2.13
[    1.460630] Bluetooth: L2CAP socket layer initialized
[    1.460633] Bluetooth: SCO (Voice Link) ver 0.6
[    1.460635] Bluetooth: SCO socket layer initialized
[    1.460678] Bluetooth: RFCOMM TTY layer initialized
[    1.460682] Bluetooth: RFCOMM socket layer initialized
[    1.460692] Bluetooth: RFCOMM ver 1.11
[   17.388051] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   18.888253] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.888257] Bluetooth: BNEP filters: protocol multicast

```
rfkill list shows both now:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

(I have laptop Toshiba A200)
```
Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
```

So, can you help me guys with this? Will I ever be able to set up my BT without using XP or no? 
Sorry for such a long post, but I am really interested in solving this "bug" 
Thanks in advance

---

### Post by GeorgeVita on 2009-12-20
Hi **Michalxo**,
I did some tests on my EeePC 1000H, integrated BT, Ubuntu 10.04 a1 and bluetooth package 4.51-0ubuntu2 (default)

Parameters that change BT (& wlan) behaviour:
- BIOS enable/disable on board peripherals
- s/w kill switch (**Fn+F2**) which acts differently on xp
- s/w enable/disable BT or wlan via application (click selection from icon)

I reproduced your problem when used BIOS to disable BT peripheral but worked fine after clicking BT icon and then 'turn on bluetooth'. As I remember this package came out 'working' last days before release of Ubuntu 9.10 so it is possible to have some 'bugs' on different h/w.

For your case, try to 'enable' every peripheral from BIOS, do NOT use Fn+F2 (or any other soft kill switch) and do not bother about signing Leds. Use only enable/disable selections from application software (on both O.S.) till you find a steady working state. Then 'debug' the non working condition and help developers by filling a bug report to launchpad.

Regards,
George

P.S.: testing above I found that Fn+F2 or 'turn on bluetooth' enables the onboard camera also (bug).

---

### Post by Michalxo on 2009-12-26
Ok, I think I know what is going on with my machine.
 I clicked on bluetooth icon on panel and software-turned off my adapter. Now I can't see my bluetooth-applet, even though it runs. So, how can I bring it up again? Does anyone know how to turn it on via command line?
Thanks


edit: Booting to XP machine and back, brings up the BT...

---

