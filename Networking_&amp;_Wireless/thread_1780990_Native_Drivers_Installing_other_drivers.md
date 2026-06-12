---
title: "Native Drivers? Installing other drivers?"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by smcrossman on 2011-06-12
I'm having issues with one of my 3 computers hooking into and staying connected to the wireless network.  This has been happening longer than I've had Ubuntu installed....initially I figured it was drops in the service from my ISP. LOng story...but that had been happening from way back when I moved in here.  So I recently switched back to DSL. Speed is better and connection as well, except my monster machine.  

Before I start the hunt for USB adapters I want to make sure I am using the best driver(s) and that the newer equipment will be worth it. This gateway is dual boot Natty and Win 7 HP both 64 bit.  The primary adapter is a netopia that was provided to me by AT&T.  It comes up in the system as a RT73 and it has a native driver installed.  I finally with a lot of babying got it to connect with the 2WiIRE modem/gateway. (meaning I put in MAC addresses for both machines, switched types of protection AND attached an ethernet cable to the ethernet port that ISP swore wouldn't work.  It just constantly flickers in & out, well it goes in spells...but

The second adapter is an old legacy 2WIRE. It works great in the back room on the older computer. Up here the 2 lights were on all morning but there was never any acknowledgement of any kind of wireless anything on the pc.  This pc identifies it as a ZyDas ZD1211B.  I found a lot of wikis on this one...the most recent I believe said the correct driver was a zd1211rw or zyd maybe....IF that is the correct match for this adaptor. 

then there is the router/gateway (I haven't even researched it yet). Its a 2WIRE 3800hgv. I do have the current windows drivers for it (Win7) from the website.

Problem is I'm tired and scared to do this copy/compile/install thing.  Seems pretty complicated. Of course I saw a few enteries on special drivers and how to's as well as the one with missing documentation links for the RT37. So I also don't know what is proper for 11.07 AND for 64bit.

Can anyone simplify the process?  I spent all day yesterday with no recognition of anything wireless, so at least it is working somewhat now. Also I'm hoping to put an external hard drive on this monster as a Samba share srv location so I need to be able to set it up for that role as well, which means the networking part really needs to be up to specs.

I hope I got most of what you need to know in here. I've run some of those diagnostics so many times that they are gibberish in my dreams!

---

### Post by chili555 on 2011-06-12
Our most eminent physician, Dr. Driver, has been given your case. Which of your two patients would you like me to see first? I hope it's that cute little Zydas there. Let's be sure what we are working with. Please open a terminal and run and post:```
lsusb
```Feel free to strip away all the lines that are not the Zydas wireless device.

After we get it running, we'll move on to the rt73usb.

Compiling from a tar.gz is really no big task and can be fun. Sadly, for Dr. Driver, we see no reason, so far, to do so.

---

### Post by smcrossman on 2011-06-13
Okay here goes.... just as an FYI both adapters are plugged in.  I know! But the 2WIRE didn't even make wireless show as possible so I plugged in the netopia on the USB extender hub. I figured it would be much easier to post if I had access on this machine!

root@gateway-suzanna:/home/gateway_u1_suzanna# lsusb
[COLOR=Magenta]Bus 002 Device 055: ID 0ace:1215 ZyDAS ZD1211B 802.11g[/COLOR]
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Purple]Bus 001 Device 012: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter[/COLOR]
Bus 001 Device 011: ID 0a5c:2154 Broadcom Corp. 
Bus 001 Device 010: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 009: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 007: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 001 Device 002: ID 050d:0016 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@gateway-suzanna:/home/gateway_u1_suzanna# 

The wired connection eth0 is not connected to the network. It is manually controlled at the moment.

---

### Post by smcrossman on 2011-06-13
Well, I did manage to get the little 2Wre to hook up.  had to unplug it and massage it's antenna a bit...LOL

So here is the lsusb without both hooked up AND with wireless connected (not that that seems to matter on this report)

root@gateway-suzanna:/home/gateway_u1_suzanna# lsusb
[COLOR=Magenta]Bus 002 Device 064: ID 0ace:1215 ZyDAS ZD1211B 802.11g[/COLOR]
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0a5c:2154 Broadcom Corp. 
Bus 001 Device 010: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 009: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 007: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 0a48:5014 I/O Interconnect Mass Storage Device
Bus 001 Device 002: ID 050d:0016 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@gateway-suzanna:/home/gateway_u1_suzanna# 

Oh but the connection died before I could hit submit post...so back to the eth0!

---

### Post by chili555 on 2011-06-13
> ID 0ace:1215 ZyDAS ZD1211B 802.11gYou are quite correct; the module *zd1211rw* is correct for your device. It has been built in to the kernel for the last several Ubuntu versions. > So here is the lsusb without both hooked up AND with wireless connected...
...Oh but the connection died before I could hit submit post...Let's try to find out why the connection is not stable. Please open a terminal and run and post:```
sudo modprobe zd1211rw
iwconfig
dmesg | grep -e wlan -e zd12
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by smcrossman on 2011-06-13
Hmmm...well I might have fixed it....but the check will be good regardless.  It wasn't being read so I picked it up and checked the connections...it popped in, connected and popped out. Duh! the cord?  So after a couple of switch outs I found one htat powered it and seems to  be working consistently.

The first command gave me nothing...a short delay then a new line prompt.

iwconfig:

gateway_u1_suzanna@gateway-suzanna:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Zan"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 98:2C:BE:6D:01:21   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/100  Signal level=48/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:92   Missed beacon:0

gateway_u1_suzanna@gateway-suzanna:~$ 

the last one gave me more than the memory on my terminal will display. I'm going to try a diff terminal. to see if I can adjust the settings a little better and then I'll post what I get or can post in the next post.

---

### Post by smcrossman on 2011-06-13
Okay...just needed to adjust the scrollback ability.  Here it is:

gateway_u1_suzanna@gateway-suzanna:~$ dmesg | grep -e wlan -e zd12
[ 3969.430518] usbcore: registered new interface driver zd1211rw
[ 4031.046260] zd1211rw 2-5:1.0: phy0
[ 4031.091232] <30>udev[2784]: renamed network interface wlan0 to wlan1
[ 4031.357710] zd1211rw 2-5:1.0: firmware version 4725
[ 4031.417709] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4031.499102] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4031.603749] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4031.640141] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4031.640161] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4031.710100] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4032.902398] zd1211rw 2-5:1.0: phy1
[ 4032.951107] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4033.169712] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4034.362572] zd1211rw 2-5:1.0: phy2
[ 4034.420995] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4034.643714] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4035.832378] zd1211rw 2-5:1.0: phy3
[ 4035.880999] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4036.098720] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4037.332376] zd1211rw 2-5:1.0: phy4
[ 4037.380990] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4037.604706] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4038.792396] zd1211rw 2-5:1.0: phy5
[ 4038.840977] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4039.063715] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4040.212731] zd1211rw 2-5:1.0: phy6
[ 4040.261001] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4040.479714] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4041.592388] zd1211rw 2-5:1.0: phy7
[ 4041.661028] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4041.881716] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4043.052977] zd1211rw 2-5:1.0: phy8
[ 4043.140988] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4043.365713] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4044.502680] zd1211rw 2-5:1.0: phy9
[ 4044.551250] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4044.777723] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4045.992388] zd1211rw 2-5:1.0: phy10
[ 4046.031003] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4046.252717] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4047.412705] zd1211rw 2-5:1.0: phy11
[ 4047.460982] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4047.685712] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4048.823671] zd1211rw 2-5:1.0: phy12
[ 4048.870995] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4049.091722] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.242674] zd1211rw 2-5:1.0: phy13
[ 4050.300984] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4050.549758] zd1211rw 2-5:1.0: firmware version 4725
[ 4050.609712] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4050.690869] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4050.910066] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910078] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910084] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910089] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910094] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910098] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910103] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910108] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910112] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910117] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910121] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910140] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.910161] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4050.990082] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4052.162935] zd1211rw 2-5:1.0: phy14
[ 4052.211134] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4052.464710] zd1211rw 2-5:1.0: firmware version 4725
[ 4052.524741] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4052.603818] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4054.810173] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.810182] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.810188] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.810193] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.810210] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.810230] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4054.910187] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4056.072910] zd1211rw 2-5:1.0: phy15
[ 4056.121057] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4056.350736] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4057.522884] zd1211rw 2-5:1.0: phy16
[ 4057.581031] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4057.832721] zd1211rw 2-5:1.0: firmware version 4725
[ 4057.892713] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4057.910725] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -62
[ 4059.082417] zd1211rw 2-5:1.0: phy17
[ 4059.131069] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4059.358747] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4060.522379] zd1211rw 2-5:1.0: phy18
[ 4060.581029] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4060.803708] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4062.062928] zd1211rw 2-5:1.0: phy19
[ 4062.121018] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4062.373710] zd1211rw 2-5:1.0: firmware version 4725
[ 4063.553670] zd1211rw 2-5:1.0: phy20
[ 4063.601272] <30>udev[4543]: renamed network interface wlan0 to wlan1
[ 4063.854710] zd1211rw 2-5:1.0: firmware version 4725
[ 4063.914711] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4063.995808] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4066.620716] wlan1: authenticate with 98:2c:be:6d:01:21 (try 1)
[ 4066.623780] wlan1: authenticated
[ 4066.702730] wlan1: associate with 98:2c:be:6d:01:21 (try 1)
[ 4066.707728] wlan1: RX AssocResp from 98:2c:be:6d:01:21 (capab=0x431 status=0 aid=2)
[ 4066.707737] wlan1: associated
[ 4066.709389] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 4070.043782] wlan1: deauthenticating from 98:2c:be:6d:01:21 by local choice (reason=3)
[ 4070.250204] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4070.340083] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4071.782415] zd1211rw 2-5:1.0: phy21
[ 4071.851007] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4072.084714] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4073.242924] zd1211rw 2-5:1.0: phy22
[ 4073.281000] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4073.533714] zd1211rw 2-5:1.0: firmware version 4725
[ 4073.593713] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4073.672820] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4073.810126] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4075.012905] zd1211rw 2-5:1.0: phy23
[ 4075.101010] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4075.321717] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4076.472687] zd1211rw 2-5:1.0: phy24
[ 4076.511022] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4076.733735] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4077.873110] zd1211rw 2-5:1.0: phy25
[ 4077.920996] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4078.141057] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4079.302280] zd1211rw 2-5:1.0: phy26
[ 4079.351101] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4079.575757] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4080.762383] zd1211rw 2-5:1.0: phy27
[ 4080.811000] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4081.031488] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4082.251701] zd1211rw 2-5:1.0: phy28
[ 4082.301055] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4082.524258] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4083.693835] zd1211rw 2-5:1.0: phy29
[ 4083.741022] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4083.990964] zd1211rw 2-5:1.0: firmware version 4725
[ 4084.050990] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4084.121035] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4084.122176] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4084.220099] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4085.313549] zd1211rw 2-5:1.0: phy30
[ 4085.360974] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4085.612773] zd1211rw 2-5:1.0: firmware version 4725
[ 4085.672801] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4085.751972] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4086.053892] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4086.053912] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4086.070102] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4087.152526] zd1211rw 2-5:1.0: phy31
[ 4087.191011] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4087.442683] zd1211rw 2-5:1.0: firmware version 4725
[ 4087.502715] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4087.583849] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4087.890095] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4087.890116] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4087.890217] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4089.042433] zd1211rw 2-5:1.0: phy32
[ 4089.120979] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4089.372650] zd1211rw 2-5:1.0: firmware version 4725
[ 4089.432681] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4089.511813] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4090.541709] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4090.541731] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4090.560108] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4091.702814] zd1211rw 2-5:1.0: phy33
[ 4091.751067] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4092.003964] zd1211rw 2-5:1.0: firmware version 4725
[ 4092.063992] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4092.143129] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4092.534434] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4092.534455] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4092.540278] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4093.632776] zd1211rw 2-5:1.0: phy34
[ 4093.680995] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4093.931928] zd1211rw 2-5:1.0: firmware version 4725
[ 4093.991961] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4094.073087] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4094.370113] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4094.370135] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4094.390103] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4095.492694] zd1211rw 2-5:1.0: phy35
[ 4095.551009] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4095.802862] zd1211rw 2-5:1.0: firmware version 4725
[ 4095.862894] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4095.944025] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4096.221721] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4096.221743] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4096.240103] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4097.322608] zd1211rw 2-5:1.0: phy36
[ 4097.380997] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4097.633781] zd1211rw 2-5:1.0: firmware version 4725
[ 4097.693811] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4097.772930] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4098.177716] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4098.177735] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4098.190091] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4099.322622] zd1211rw 2-5:1.0: phy37
[ 4099.370984] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4099.623774] zd1211rw 2-5:1.0: firmware version 4725
[ 4099.683804] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4099.764931] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4100.080102] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4100.080124] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4100.100095] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4101.202542] zd1211rw 2-5:1.0: phy38
[ 4101.271005] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4101.524722] zd1211rw 2-5:1.0: firmware version 4725
[ 4101.584754] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4101.665891] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4102.090100] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4102.090121] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4102.110098] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4103.212550] zd1211rw 2-5:1.0: phy39
[ 4103.260985] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4103.512716] zd1211rw 2-5:1.0: firmware version 4725
[ 4103.572748] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4103.651907] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4104.052340] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4104.052361] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4104.070106] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4105.142540] zd1211rw 2-5:1.0: phy40
[ 4105.191010] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4105.439679] zd1211rw 2-5:1.0: firmware version 4725
[ 4105.499714] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4105.580920] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4105.863986] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4105.864008] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4105.880097] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4106.982126] zd1211rw 2-5:1.0: phy41
[ 4107.040992] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4107.292606] zd1211rw 2-5:1.0: firmware version 4725
[ 4107.352636] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4107.431849] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4107.650081] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650093] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650099] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650104] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650109] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650114] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650118] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650123] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650127] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650131] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650136] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650154] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.650175] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4107.689255] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4108.833345] zd1211rw 2-5:1.0: phy42
[ 4108.870975] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4109.119518] zd1211rw 2-5:1.0: firmware version 4725
[ 4109.179559] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4109.260745] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4109.471715] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -62
[ 4109.471731] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471737] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471742] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471747] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471751] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471756] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471760] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471764] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471769] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471773] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471790] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.471818] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4109.550088] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4110.691972] zd1211rw 2-5:1.0: phy43
[ 4110.760998] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4111.012468] zd1211rw 2-5:1.0: firmware version 4725
[ 4111.072494] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4111.153630] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4111.450197] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4111.450216] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4111.453652] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4112.542212] zd1211rw 2-5:1.0: phy44
[ 4112.581003] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4112.837374] zd1211rw 2-5:1.0: firmware version 4725
[ 4112.897406] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4112.976540] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4113.399523] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4113.399545] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4113.410091] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4114.512207] zd1211rw 2-5:1.0: phy45
[ 4114.560967] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4114.813364] zd1211rw 2-5:1.0: firmware version 4725
[ 4114.873395] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4114.954519] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4115.262711] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4115.262732] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4115.270465] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4116.402135] zd1211rw 2-5:1.0: phy46
[ 4116.450992] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4116.704308] zd1211rw 2-5:1.0: firmware version 4725
[ 4116.764338] zd1211rw 2-5:1.0: zd1211b chip 0ace:1215 v4810 full 00-24-7e AL2230S_RF pa0 g--N-
[ 4116.845475] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4117.250199] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4117.250219] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4117.250325] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -19
[ 4118.372124] zd1211rw 2-5:1.0: phy47
[ 4118.420993] <30>udev[4824]: renamed network interface wlan0 to wlan1
[ 4118.522215] zd1211rw 2-5:1.0: error ioread32(CR_REG1): -62
[ 4118.539314] zd1211rw 2-5:1.0: couldn't load firmware. Error number -62
[ 4197.753772] zd1211rw 1-5:1.0: phy48
[ 4197.820960] <30>udev[7446]: renamed network interface wlan0 to wlan1
[ 4197.882283] zd1211rw 1-5:1.0: firmware version 4725
[ 4197.922301] zd1211rw 1-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-24-7e AL2230S_RF pa0 g--N-
[ 4197.942842] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4199.956709] wlan1: authenticate with 98:2c:be:6d:01:21 (try 1)
[ 4199.958067] wlan1: authenticated
[ 4199.958113] wlan1: associate with 98:2c:be:6d:01:21 (try 1)
[ 4199.960325] wlan1: RX AssocResp from 98:2c:be:6d:01:21 (capab=0x431 status=0 aid=2)
[ 4199.960331] wlan1: associated
[ 4199.961867] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 4210.620024] wlan1: no IPv6 routers present
gateway_u1_suzanna@gateway-suzanna:~$ 


If you aren't seeing any issues I'll just assume it was an old power cord issue.  Its a basic USB to the mini USB which is so popular. I just need to be sure its a good quality one when I buy it. 

Oh and is this a legacy or is it capable of MasterMode? Just out of curiousity. If it is I probalby should use it on whichever pc I'm going to use as my local server host I'm thinking.

---

### Post by chili555 on 2011-06-13
You have a wireless interface and it's connected, albeit to a weak signal:> Link Quality=[COLOR="Red"]48/100[/COLOR] Signal level=48/100 Does it drop the connection? Is there an option to increase the power level in the modem/router?> the last one gave me more than the memory on my terminal will display. I'm going to try a diff terminal. to see if I can adjust the settings a little better and then I'll post what I get or can post in the next post. You can transfer it to a text file and post it from there:```
dmesg | grep -e wlan -e zd12 > dmesg.txt
```The text file will be found in your user directory and you can open it with Text Editor, also known as gedit.

---

### Post by chili555 on 2011-06-13
Issues? You have almost nothing *BUT* issues! I suspect this is the root of it all:> zd1211rw 2-5:1.0: couldn't load firmware. Error number -62According to modinfo, there are several firmware files associated with zd1211rw:> $ modinfo zd1211rw
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
firmware:       zd1211/zd1211_uphr
firmware:       zd1211/zd1211b_uphr
firmware:       zd1211/zd1211_ub
firmware:       zd1211/zd1211b_ub
firmware:       zd1211/zd1211_ur
firmware:       zd1211/zd1211b_ur
version:        1.0
I'm not sure, but I think a different firmware blob is loaded depending on the specific device that's plugged in. Let's shortcut the process and reinstall the firmware:```
sudo apt-get install --reinstall linux-firmware
```Reboot and rerun:```
dmesg | grep -e wlan -e zd12
```Is it a lot cleaner now?

---

### Post by smcrossman on 2011-06-13
Oh , much prettier!  LOL  Here it is:

gateway_u1_suzanna@gateway-suzanna:~$ dmesg | grep -e wlan -e zd12
[   17.400846] zd1211rw 1-5:1.0: phy0
[   17.401614] usbcore: registered new interface driver zd1211rw
[   17.440590] <30>udev[470]: renamed network interface wlan0 to wlan1
[   17.524260] zd1211rw 1-5:1.0: firmware version 4725
[   17.564264] zd1211rw 1-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-24-7e AL2230S_RF pa0 g--N-
[   17.581558] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.821520] wlan1: authenticate with 98:2c:be:6d:01:21 (try 1)
[   19.823258] wlan1: authenticated
[   19.823277] wlan1: associate with 98:2c:be:6d:01:21 (try 1)
[   19.827256] wlan1: RX AssocResp from 98:2c:be:6d:01:21 (capab=0x431 status=0 aid=1)
[   19.827259] wlan1: associated
[   19.828155] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   29.850016] wlan1: no IPv6 routers present
gateway_u1_suzanna@gateway-suzanna:~$ 


And just for good measure on reboot it quietly did exactly what it should...powered up and connected with the gateway.  Of course the wired Ethernet created a new auto connection which I had to turn off.... but once I'm certain of the wireless then the cord will be going away.

---

### Post by chili555 on 2011-06-13
It looks perfectly lovely! I suggest you use it for a few days and if it's all good, come back and mark this thread Solved. If not, post back and tell us what your symptoms are.

---

### Post by smcrossman on 2011-06-13
Great! I can easily do that.  Of course there is the other adapter still.  That one I just tried in the back and it isn't wanting to connect. I don't know if I should do the diagnostics up here or if they need to be done back there. That computer is really old with only a 10GB HD (8 of which is currently used). But in order for it to network with my other 2 it does need to have a USB adaptor so it is capable of networking.

Regardless Thank you so much. It's going to be such an improvement to have consistent internet  on this monster (especially now that I have the new glasses and can actually READ what is on the monitor!)

---

### Post by chili555 on 2011-06-13
I'm ready (after supper) to start the other one. Please post:```
lsusb
lsmod | grep rt73
```Thanks.

---

### Post by smcrossman on 2011-06-13
Okay, here you go....

gateway_u1_suzanna@gateway-suzanna:~$ lsusb
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0a5c:2154 Broadcom Corp. 
Bus 001 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 008: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface SBus 001 Device 003: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapterubclass)
Bus 001 Device 007: ID 03f0:5b11 Hewlett-Packard OfficeJet J2100 series
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 0a48:5014 I/O Interconnect Mass Storage DeviceBus 001 Device 003: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter
[COLOR=Magenta]Bus 001 Device 003: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter[/COLOR]
Bus 001 Device 002: ID 050d:0016 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gateway_u1_suzanna@gateway-suzanna:~$ lsmod |grep rt73
rt73usb                27406  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20330  1 rt73usb
rt2x00lib              49235  2 rt73usb,rt2x00usb
gateway_u1_suzanna@gateway-suzanna:~$ 

Since I rebooted with this one plugged in it has loaded & connected slowly. Dropped out before I could connect to internet. Then dropped out before the page could reload for me to type the reply.. It's back up & on now, but I activated the eth0 so I could get this posted.

---

### Post by smcrossman on 2011-06-14
Another question before I forget....

As far as increasing power to the router/gateway....  How is that done. Is that something I can tweak in the online setup?  (Like a channel or something?)  I had a sales person tell me that this router wouldn't support more than 2 maybe 3 machines max.  Well I've got the 3 PCs and then my iPhone is usually on that as well.  I usually don't have more than 2 pcs running at a time, but ...  I know I've been considering looking for a better option where I could hook an external HD to it for network back up and filekeeping, but they are pricey and not an immediate thing.

Believe it or not this IS a better/faster connection that I had with Uverse the last 2 years or so.  

Oh and if this adaptor is being properly identified there is a new driver out from the manuf. it's binary, but I don't know how to go about installing it.

---

### Post by chili555 on 2011-06-14
Let's start at the end and work our way to the beginning!```
As far as increasing power to the router/gateway.... How is that done. Is that something I can tweak in the online setup? (Like a channel or something?) 
```Exactly. You log on to the setup pages of the modem/router device and look under wireless settings. You might or might not see an option to change the transmit power in the router. Attached is a sample from my router. If you have such a setting, make sure it's at maximum.

rt73usb is correct for your device and there are no driver conflicts that I can see. There is a driver parameter we might try:```
sudo gedit /etc/modprobe.d/rt73usb.conf
```Add a single line:```
options rt73usb nohwcrypt=1
```Proofread carefully, save and close gedit. After a reboot, is the performance better or worse? If it's worse, delete the file with:```
sudo rm /etc/modprobe.d/rt73usb.conf
```> I had a sales person tell me that this router wouldn't support more than 2 maybe 3 machines max.Frankly, that sounds like a failed attempt at upsell to me. I suppose there are low powered cheap routers out there, but I haven't seen many. What brand and model is it?> there is a new driver out from the manuf. it's binary, but I don't know how to go about installing it.What is the name of the file and, especially, the file extension?

---

### Post by smcrossman on 2011-06-14
Okay, I'm waiting on a couple of downloads so I can reboot.  That was a new file I created for the options right?

My power was set to 4.  I moved it up to 10 we'll see how that affects things!

The driver I downloaded was named  2011_0210_RT73_Linux_STA_Drv1.1.0.5.bz2

I'm not really sure but the update or release date was this year Feb or April? Of course if I don't need it that's fine too.  Although at some point I bet I will have to figure out how to put in a non-repository driver, but all in good time.

---

### Post by chili555 on 2011-06-14
> That was a new file I created for the options right?That's correct.> My power was set to 4. I moved it up to 10 we'll see how that affects things!I strongly suspect that's going to make all the difference in the world.

We can build the newer driver pretty easily and we'll both learn from the experience.> the update or release date was this year Feb or April?February, 2011; that's pretty recent. If the power increase doesn't solve it, I will be interested to read the release notes to see if anything changes that helps you.

EDIT: I searched a bit and found the file on Ralink's site. Here is a quote from the release notes:> [V 1.1.0.2]

1.) [I][B]Modify for kernel 2.6.27. 
[/B][/I]
*******************************************************************



[V 1.1.0.1]

1.) Modify for kernel 2.6.24 and up. 

*******************************************************************



[V1.1.0.0]

1.) Use USB single write and new firmware to support USB single write.

2.) Support USB 1.1 and improve its throughput.

3.) Fix the bug: reboot AP,sta unload then load«á, excuting supplicant would

     crash.

4.) Fix the AdHoc problem with Connexant STA at A band.

5.) Fix the problem: can't link to Broadcom AP,when AP set auth:wpa2 cipher:aes

6.) Ap set 802.1x & Fragmentation set 256,station can't connect AP

7.) There are hidden AP in enviroment,sta connect to AP hardly.

 

[V1.0.5.0]

1.) Fix the bug about deciding which BSSID is higher in IBSS mode.



[V1.0.4.1]

1.) Support configuration by NetworkManager

2.) Support linux kernel version 2.6.21I have highlighted the latest entry. Note that the last change was to modify it for kernel version 2.6.27. Ubuntu 11.04 runs 2.6.38! I suspect that Ralink isn't developing the driver for download any longer, instead developing within the mainline kernel. By the way, the version of rt73usb that I have is:> $ modinfo rt73usb 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
[COLOR="Red"]version:        2.3.0[/COLOR]
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     3EA0AD47E08DA7DB71F48C7
--- snip ---It seems that the version you have is a regression, not an improvement.

---

### Post by smcrossman on 2011-06-14
Interesting how things turn out isn't it?  I thought it was kind of strange that they had such a new update since the netopia I'm using is at least 2 years old.  But some areas technology doesn't jump up as quickly as others I guess.  I think it was also being touted as a STABLE version.  So they've probably been going back and addressing some of those older issues that have carried problems through to more current kernels.  It's odd how the whole industry works when it comes to bugs and such.  Thing is a lot of those bugs have had community & linux distributed workarounds for so long that they aren't such issues anymore.

The downloads I'm doing are going to take quite a while so I guess I'm going to take a little vacation and water my dying plants. I plugged the ethernet back up since it is twice as fast at downloading at the moment. Somehow that just seems wrong to me, but that may just be because they advertise wireless is so much faster.

I certainly appreciate all your time and help!  So many folks have wireless networking issues starting out, but there are just so many variables to figure out.  I'll be glad to have this part of the process behind me...It's been a long week!

---

### Post by smcrossman on 2011-06-15
Well, the connection really seemed to be more consistent.  The wireless speeds are just dragging, especially tonight. I'll have to research a little mroe and see whether an equipment upgrade would help that.  Its been a long time since I really looked at all the accessories available an dinvolved in wireless networking.

I've switched the netopia back to the back computer.  I'll have to see if I can get the network connection going there. If not I can run cable back there for whenever I have that one turned on.

Thanks for all the help!

---

