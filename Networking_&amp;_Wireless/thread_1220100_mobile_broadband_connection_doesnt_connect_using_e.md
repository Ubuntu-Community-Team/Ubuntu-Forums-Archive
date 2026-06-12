---
title: "mobile broadband connection doesnt connect using edge modem in ubuntu 9.04"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by xihad76 on 2009-07-22
i was using ubuntu 8.04 and my edge modem was working fine there using a gnome ppp dialer. today i have upgraded to 9.04. then my edge modem was automatically detected and i made a connection using network manager. but whenever i try to connect to net using the newly created mobile broad band connection, it shows "gsm connection disconnected" after few moments.then i tried to connect using my nokia phone and that time it was ok. So the problem is somewhere with the usb modem configuration.

here i want to mention one thing. when i installed the same modem in xp i had to change the init string for this modem manually as it was made for another service provider and the init string for that service provider was set by default. 

so,i guess the problem might happen due to the default init string here in ubuntu as well.if it really is then can anyone plz tell me how to change the init string for edge modem in ubuntu 9.04? 

or am i missing something here? plz help.. 

thnx in advance..

---

### Post by xihad76 on 2009-07-22
Guys, please help me. or i have to go back to previous version :-(

---

### Post by dk06 on 2009-07-22
Who is your mobile broadband ISP?

AT&T?
Verizon?
..........?

& What Make/Model Device are you using 

Is it USB connection to a nokia cell phone?

If so what is the model?

---

### Post by xihad76 on 2009-07-22
HI, i m from bangladesh and my ISP is Grameen phone. but ISp config is ok as i m using internet now using the same connection with my nokia phone. but whenever i try to connect using my usb edge modem it doesnt.

---

### Post by dk06 on 2009-07-22
> **xihad76 said:**
> HI, i m from bangladesh and my ISP is Grameen phone. but ISp config is ok as i m using internet now using the same connection with my nokia phone. but whenever i try to connect using my usb edge modem it doesnt.


When I got my USB Modem I needed to use it in Windows FIRST with the software that came with the USB Modem. 
Basically,(in my case) my device needed to authenticate with the ISPs server and associate the USB device with my account. After using it with Windows  it worked fine in several distros of linux including ubuntu.

So...Here is what I would do:
1) Boot Windows & install the USB Device software that came with it.
2) Plug in the device & connect with Windows
3) Surf for a couple minutes & test it
4) Disconnect & unplug it properly
5) Try it out in Linux

Hope This Helps

---

### Post by xihad76 on 2009-07-22
> **dk06 said:**
> When I got my USB Modem I needed to use it in Windows FIRST with the software that came with the USB Modem. 
Basically,(in my case) my device needed to authenticate with the ISPs server and associate the USB device with my account. After using it with Windows  it worked fine in several distros of linux including ubuntu.

So...Here is what I would do:
1) Boot Windows & install the USB Device software that came with it.
2) Plug in the device & connect with Windows
3) Surf for a couple minutes & test it
4) Disconnect & unplug it properly
5) Try it out in Linux

Hope This Helps


just followed your way. but still no luck. anyways.. thnx for the help :-)

---

### Post by xihad76 on 2009-07-23
still no solution :( i have also tried by installing wvdial manually but still no luck. it shows that carrier found and then connection get lost. but the same usb modem is working fine in xp and with other mobile handset in ubuntu 9.04 as well..

---

### Post by shahan on 2009-07-23
[http://www.scribd.com/doc/16099866/Connecting-3110c-on-Ubuntu](http://www.scribd.com/doc/16099866/Connecting-3110c-on-Ubuntu)
&#2447;&#2439; &#2482;&#2495;&#2434;&#2453;&#2463;&#2494; &#2438;&#2474;&#2472;&#2495; &#2463;&#2509;&#2480;&#2494;&#2439; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2503;&#2472;&#2404;

---

### Post by xihad76 on 2009-07-23
> **shahan said:**
> [http://www.scribd.com/doc/16099866/Connecting-3110c-on-Ubuntu](http://www.scribd.com/doc/16099866/Connecting-3110c-on-Ubuntu)
&#2447;&#2439; &#2482;&#2495;&#2434;&#2453;&#2463;&#2494; &#2438;&#2474;&#2472;&#2495; &#2463;&#2509;&#2480;&#2494;&#2439; &#2453;&#2480;&#2468;&#2503; &#2474;&#2494;&#2480;&#2503;&#2472;&#2404;

Shahan vai,

my problem is a bit peculiar. the usb modem i m using is not provided with any mobile handset rather this is a mediatech 2.75G usb edge modem. when i tried to get connected using wvdial the modem is reconized without any problem, also the data carrier; but after few moments connections get lost automatically and it tries to reconnect and nothing happens afterwards. :(:(

---

### Post by shahan on 2009-07-23
you can try making a new user account.

---

### Post by xihad76 on 2009-07-24
this is the output while trying with wvdial: 

--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer gpinternet] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","gpinternet"
AT+CGDCONT=1,"IP","gpinternet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!} } }2}"}&} } } } }#}$@#}'}"}(}"R[04]~
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT*99***1#
--> Waiting for carrier.
~[7f]}#@!}!}!} }2}"}&} } } } }#}$@#}'}"}(}"][14]~~[7f]}#@!}!}"} }2}"}&} } } } }#}$@#}'}"}(}"L$~~[7f]}#@!}!}#} }2}"}&} } } } }#}$@#}'}"}(}"C4~~[7f]}#@!}!}$} }2}"}&} } } } }#}$@#}'}"}(}"nD~~[7f]}#@!}!}%} }2}"}&} } } } }#}$@#}'}"}(}"aT~~[7f]}#@!}!}&} }2}"}&} } } } }#}$@#}'}"}(}"pd~~[7f]}#@!}!}'} }2}"}&} } } } }#}$@#}'}"}(..................... 


any idea??

---

### Post by GeorgeVita on 2009-07-24
Hi **xihad76**,
usually the **--> Carrier detected. Waiting for prompt.**
is caused because an extra line is needed into your **/etc/wvdial.conf** file:
**Stupid Mode = 1**

This will skip the 'old' login and go directly to the pppd.

Try it and if disconnects you again, post your /etc/wvdial.conf file to check.

Regards,
George

---

### Post by xihad76 on 2009-07-25
> **GeorgeVita said:**
> Hi **xihad76**,
usually the **--> Carrier detected. Waiting for prompt.**
is caused because an extra line is needed into your **/etc/wvdial.conf** file:
**Stupid Mode = 1**

This will skip the 'old' login and go directly to the pppd.

Try it and if disconnects you again, post your /etc/wvdial.conf file to check.

Regards,
George


Hi there!, 

Thank u very very much!! this is working like a charm.. :-D 
i was actually starting to get frustrated and this time u literally saved my life!!  

So one more question bro if u have time to answer ... if it is possible to configure the network manager mobile broadband connection settings and get connected from there like i m doing now configuring the wvdial.conf?? 

and thanx again for ur help. take care n God bless U. :-)

---

### Post by GeorgeVita on 2009-07-25
Hi **xihad76**, so you have good news! Let's continue with some ideas:

Use your connection to get updates (from Synaptic or Update Manager). Delete any existing Mobile Broadband connection, reboot without the modem, _remove/disconnect/disable_ any ethernet/Wifi/Bluetooth connection, attach the modem and _just wait for 1 minute_ for the wizard to start. If started (I hope so) set up your connection.

If not started, open a terminal window and try:```
dmesg
```Copy and post the last lines (10-20 maximum) regarding system activity about your modem and/or usbserial/option/... driver used.
Try also:```
lsusb
```to see vendorID & productID of your modem (post here the results).
From 9.04 some changes made into the USB peripheral recognition method and I am not sure I can help you but ... we deserve to try it!

Regards,
George

---

### Post by thomaspember on 2009-07-25
im having some problems to

when i type dmesg i get 

```

[  145.896048] usb 2-5: new high speed USB device using ehci_hcd and address 3
[  146.046889] usb 2-5: configuration #1 chosen from 1 choice
[  146.048785] usb-storage: device ignored
```

and with lsusb

```
 Bus 002 Device 003: ID 19d2:2000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0681:0005 Siemens Information and Communication Products ID-Mouse with Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 090c:f371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device

```

can anyone help?

sorry to hijack the thread

---

### Post by GeorgeVita on 2009-07-25
Hi **thomaspember**,
as your modem is **19d2:2000** (a ZTE modem) and your Ubuntu is 9.04 (propably), the most appropriate ideas to try are at another thread:
**[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)**

Try post#1 update solution (udev-extras) and post here or there the results to follow up.

Regards,
George

---

### Post by thomaspember on 2009-07-25
it does not show on the desktop or computer as a ZeroCD device it does nothing and never has shown as any USB device on Desktop or Computer. The green light is on 

im using Ubuntu 9.04 jaunty 

Kernel 2.6.28-13 generic

and gnome 2.26.1

my modem is MF627 (3 Mobile Broudband UK)

---

### Post by sonu 1807 on 2009-07-25
Hi, I am from India and also use a ZTE modem for internet. I right clicked network mangager and then in edit connections I went to Mobile Broadband. Then in Auto Mobile Broadband CDMA I simply clicked edit and punched in my username and password while selcting Available to all users. Now when i have to connect I simply click the network manager icon and choose Auto Mobile Broadband CDMA connection and it works

---

### Post by GeorgeVita on 2009-07-25
Hi **sonu 1807**, your modem is a different type (ZTE also) which is recognised by the system. The other one is not recognised at all as a modem. At **lsusb** command is shown as **19d2:2000** which this is a "virtual" CD with Win drivers (usually).

Hi **thomaspember**, the idea from the link in my previous post is that system will use **udev-extras** to force the modem to real 'modem state' 19d2:00xx and then try network-manager.

You need Internet connection on this PC to do the above. If you have no other connection you could try a 'trick' using a windows PC. This is described on my post: [http://ubuntuforums.org/showpost.php?p=6894586&postcount=8](http://ubuntuforums.org/showpost.php?p=6894586&postcount=8)
> **GeorgeVita said:**
> ...
2. The modem responds **19d2:2000** (as the internal CD drive or USB hub) but we need the actual modem (**19d2:0031**). You may use a special program called **usb_modeswitch** (see [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)) but I preferred to send the AT command **AT+ZCDRUN=8** from a Windows PC to the modem (use hyperterminal or add it as an extra init command through control panel).
This command turns off the AUTO RUN function of the internal CD, if you want to return to default you have to send **AT+ZCDRUN=9** (info taken from [www.matt-barrett.com](www.matt-barrett.com)).

Test again the terminal command **lsusb** to be sure you have **19d2:0031**

The idea is to gain the 'real modem mode'.

G

---

### Post by thomaspember on 2009-07-25
thanks GeorgeVita i got it working in the end i forgot to save a config (silly me) and now it all working good with speeds around 7mps :)

---

### Post by GeorgeVita on 2009-07-25
Well Done!
Did you managed it with the **udev-extras** ?

You can **edit** your "I made it" posts and be _more informative_ (technically) for other future readers!

Regards,
George

---

### Post by xihad76 on 2009-07-25
Hi GeorgeVita,

according to ur dictation firstly i have installed all the recommended updates via update manager.then removed the present mobile broad band connection settings. then disconnected my ethernet cable and edge modem from my pc. after that i restarted my pc and connected my edge modem again. after waiting for sometime the mobile broadband connection wizard appeared automatically and i made a new connection following proper settings. Then i tried to connect via network manager and after trying for a few moments it says that- **GSM network disconnected - you are now offline..** 

here are the last few lines generated with **dmesg** : 

```
[   19.278552] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.278562] Bluetooth: BNEP filters: protocol multicast
[   19.335577] Bridge firewalling registered
[   21.966823] [drm] Initialized drm 1.1.0 20060810
[   21.996389] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.996613] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   22.136695] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   22.137440] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   24.294511] eth0: link down
[   24.294798] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.298033] mtrr: no MTRR for e0000000,2000000 found
[   74.300557] mtrr: no MTRR for e2000000,5000000 found
[   76.704189] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   76.705005] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   76.705698] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[  132.608019] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  132.841964] usb 2-1: configuration #1 chosen from 1 choice
[  132.894990] cdc_acm 2-1:1.1: ttyACM0: USB ACM device
[  132.898285] usbcore: registered new interface driver cdc_acm
[  132.898296] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```

and these are the output of **lsusb** command :

```
xihad@xihad:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e8d:0003 MediaTek Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

hope these will help.. take care..

---

### Post by GeorgeVita on 2009-07-25
Hi **xihad76**, just an idea ...
as you are connecting via **wvdial** we assume that parameters are correct. Edit the 'mobile broadband' connection for 'Grameen Phone', place the same user/password and Phone *99***1# **as in /etc/wvdial.conf** and retry.
Finally, if not suceeded, try changing some parameters like 'ppp settings' in authentication leave only PAP and CHAP etc. and check DNS settings at IPV4 tag.

Good Luck,
George

---

### Post by xihad76 on 2009-07-25
Hi GeorgeVita, Thnx for the reply..

Instead of using my edge modem i have tried to connect using nokia handset via network manager and it gets connected with same mobile broadband connection settings without any problem.. so just wondering what could be wrong with my edge modem.. 

i have also tried by changing the parameters.. but haven't been fruitful either.. 

thnx for everything bro.. u have been real helpful.. God bless U..

---

### Post by pantera10 on 2009-07-29
ok so i was bout to open a new topic but then i came across this one..and seems like everybody is pretty happy tht their internet is working fine...

so a shout out to george for some HELP...
im a big noob of ubuntu...first some info

Usb modem = Global Tone , HSDPA USB STICK..
Location = Malaysia

ok so i plugged in the usb stick and it gave me a blue light which means its working fine...so i went to network manager..created a connection "Celcom" and rebooted the pc..then i left clicked on network connections and there was no connection there :S...it works fine on windows..i can even access the setup it has inside the usb stick...but on ubuntu its just giving me tht blue light..thts it :(

did i miss something out...cause i followed the directions given in Help & Support to perfection

---

### Post by GeorgeVita on 2009-07-29
Hi **pantera10**,
please do some basic tests and/or give some technical info:

Boot without the modem, wait for system to load, attach the modem, open a terminal window, when led is blue (modem initialised, found 3G network) try:
```
dmesg
```look at the last 10-15 lines regarding modem driver (option? usbserial?) and a possible ttyU*. Copy here those lines.
From terminal try also:```
lsusb
``````
ls /dev/ttyU* /dev/ttyH* /dev/ttyA*
```to see vendorID : productID of the modem and any port created.

Post to follow up.

Regards,
George

---

### Post by pantera10 on 2009-07-29
heres the result of     "dmesg"   , last few lines.
 

 

 

 [   23.046945] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 

 [   80.500021] Clocksource tsc unstable (delta = -373060737 ns)
 

 [   84.520094] usb 2-1: new high speed USB device using ehci_hcd and address 3
 

 [   84.665546] usb 2-1: configuration #1 chosen from 1 choice
 

 [   85.000760] Initializing USB Mass Storage driver...
 

 [   85.000942] usb-storage: device ignored
 

 [   85.000995] usbcore: registered new interface driver usb-storage
 

 [   85.001006] USB Mass Storage support registered.
 

 [  335.011767] usb 2-1: USB disconnect, address 3
 

 [  344.520184] usb 2-1: new high speed USB device using ehci_hcd and address 4
 

 [  344.665694] usb 2-1: configuration #1 chosen from 1 choice
 

 [  344.669608] usb-storage: device ignored
 

 

 

 

 

 after doing the dmesg the usb stick light turned to green and would only return to blue if i would disconnect it and connect it again..ok so after waiting for like 10 mins the light turned blue..i did the same dmesg command , results did not change
 

 

 

 heres the lsusb result
 

 

 

 lsusb
 

 Bus 002 Device 004: ID 19d2:2000   
 

 Bus 002 Device 002: ID 0408:030c Quanta Computer, Inc.  
 

 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 

 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 

 Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
 

 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 

 

 i tried the /dev commands aswell and it says "no such file or directory"
 

 

 pls tell me there is still hope for me !

---

### Post by GeorgeVita on 2009-07-29
> **pantera10 said:**
> Bus 002 Device 004: ID **19d2:2000**

It seems to be a ZTE modem (19d2:2000). From [http://ubuntuforums.org/showpost.php?p=6894586&postcount=8](http://ubuntuforums.org/showpost.php?p=6894586&postcount=8) point 2 we are going to switch to modem state:

The modem in original state responds **19d2:2000** to **lsusb** (terminal command) but we need the actual modem (**19d2:0031**). Using windows we have to send the AT command **AT+ZCDRUN=8** from PC to modem.

If your PC has hyperterminal, use it to send this command to the modem. The modem port can be found from Device Manager or Control Panel (properties of modem).

If you have no hyperterminal you can add it as an 'extra init command' through control panel, modem, properties, advanced settings (I cannot remember actually) or possibly within settings of the provider's s/w (test or log session). After this TRY TO CONNECT ONCE. Then REMOVE this command to be able to connect via windows.

This command turns off the AUTO RUN function of the internal CD, if you want to return to default you have to send **AT+ZCDRUN=9**

Finally boot Ubuntu without modem, wait for the system to load, open a terminal window, attach the modem, try again **lsusb** to see the expected **19d2:0031**

Post here any result/question to follow up.

Regards,
George

---

### Post by pantera10 on 2009-07-30
ok so i dont know why im posting this but i might aswell...i got this guy to setup the modem for me...did it in like 2 mins..haha...anyway...i have no idea how he did it..i dint even ask him...though he did say most of the settings and commands had already been done..anyway...so i can post my lsusb results here if tht'll help...


P.S = mobile broadband is DAMN slow

---

